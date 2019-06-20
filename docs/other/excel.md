---
description: Excel工具类
---

```java
package com.murphyl.utils.excel;

import lombok.Getter;
import lombok.Setter;
import lombok.experimental.Accessors;
import org.apache.commons.collections.CollectionUtils;
import org.apache.commons.collections.MapUtils;
import org.apache.commons.lang3.ArrayUtils;
import org.apache.poi.xssf.usermodel.XSSFCell;
import org.apache.poi.xssf.usermodel.XSSFRow;
import org.apache.poi.xssf.usermodel.XSSFSheet;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;
import org.springframework.util.Assert;

import java.lang.reflect.Field;
import java.util.Collection;
import java.util.Map;
import java.util.TreeMap;

/**
 * Excel - 渲染工具类
 *
 * @author MurphyL
 * @date 2019/6/20 12:25
 */
@Accessors(chain = true)
public abstract class ExcelRender<A> {

    /**
     * 当前处理的Excel文件，为空则创建
     */
    @Setter
    private XSSFWorkbook template;
    /**
     * 当前处理的Sheet索引
     */
    @Setter
    private Integer sheetIndex;
    /**
     * 从第几行开始填充数据
     */
    @Setter
    private int firstRowIndex = 0;
    /**
     * 从第几列开始填充数据
     */
    @Setter
    @Getter
    private int firstCellIndex = 0;
    /**
     * 展示标题行
     */
    @Setter
    private boolean showTitleRow = true;
    /**
     * 表头索引关系
     */
    private Map<Integer, Field> cellMapping;

    /**
     * 根据指定枚举描述生成Excel
     *
     * @param annotationClass - 描述注解类
     * @param tClass          - 目标对象类型
     * @param items           - 数据集
     * @return
     */
    protected final <T> XSSFWorkbook render(Class annotationClass, Class<T> tClass, String sheetName, Collection<T> items) {
        Assert.notNull(annotationClass, "Excel - 渲染工具类 - 描述注解类型（annotationClass）不能为空！");
        Assert.notNull(tClass, "Excel - 渲染工具类 - 目标对象类型（tClass）不能为空！");
        Assert.isTrue(CollectionUtils.isNotEmpty(items), "Excel - 渲染工具类 - 数据集（items）不能为空！");
        // 工作簿
        XSSFWorkbook workbook = getWorkbook();
        // 工作表
        XSSFSheet sheet = getSheet(workbook, sheetName);
        // 字段映射关系，表头
        Field[] fields = tClass.getDeclaredFields();
        cellMapping = new TreeMap<>();
        if (ArrayUtils.isNotEmpty(fields)) {
            XSSFRow row = null;
            // 创建标题行
            if (showTitleRow) {
                row = sheet.createRow(firstRowIndex);
            }
            int cellIndex;
            A annotation;
            XSSFCell cell;
            for (Field field : fields) {
                // 跳过非标字段
                if (!field.isAnnotationPresent(annotationClass)) {
                    continue;
                }
                // 设置字段访问权限
                field.setAccessible(true);
                // 元数据
                annotation = (A) field.getAnnotation(annotationClass);
                cellIndex = fixCellOffset(getCellIndex(annotation));
                // 映射关系
                cellMapping.put(cellIndex, field);
                // 填充标题行
                if (showTitleRow) {
                    cell = row.createCell(cellIndex);
                    cell.setCellValue(getCellName(annotation));
                }
            }
        }
        if (MapUtils.isEmpty(cellMapping)) {
            return workbook;
        }
        fillSheet(items, sheet);
        return adaptCellWidth(workbook);
    }

    /**
     * 根据起始列索引修正列偏移量
     *
     * @param cellIndex - 列索引
     * @return
     */
    public int fixCellOffset(int cellIndex) {
        return firstCellIndex + cellIndex;
    }


    /**
     * 渲染 Excel
     *
     * @param tClass
     * @param sheetName
     * @param items
     * @param <T>
     * @return
     */
    public abstract <T> XSSFWorkbook render(Class<T> tClass, String sheetName, Collection<T> items);

    /**
     * 根据注解获取列明
     *
     * @param annotation
     * @return
     */
    public abstract String getCellName(A annotation);

    /**
     * 根据注解获取相对列索引
     *
     * @param annotation
     * @return
     */
    public abstract int getCellIndex(A annotation);

    /**
     * 列宽自适应
     *
     * @param workbook
     * @return
     */
    private XSSFWorkbook adaptCellWidth(XSSFWorkbook workbook) {
        workbook.forEach(sheet -> {
            sheet.getRow(sheet.getLastRowNum()).forEach((cell) -> {
                cell.getSheet().autoSizeColumn(cell.getColumnIndex());
            });
        });
        return workbook;
    }

    /**
     * 生成工作簿
     *
     * @return
     */
    private XSSFWorkbook getWorkbook() {
        return null == template ? new XSSFWorkbook() : template;
    }

    /**
     * 生成工作表
     *
     * @return
     */
    private XSSFSheet getSheet(XSSFWorkbook workbook, String name) {
        if (null == sheetIndex) {
            return workbook.createSheet(name);
        } else {
            XSSFSheet sheet = workbook.getSheetAt(sheetIndex);
            workbook.setSheetName(sheetIndex, name);
            return sheet;
        }
    }

    /**
     * 填充数据
     *
     * @param items
     * @param sheet
     * @param <T>
     */
    private <T> void fillSheet(Collection<T> items, XSSFSheet sheet) {
        XSSFRow row;
        XSSFCell cell;
        Object cellVal;
        for (T item : items) {
            row = sheet.createRow(sheet.getLastRowNum() + 1);
            for (Map.Entry<Integer, Field> entry : cellMapping.entrySet()) {
                cell = row.createCell(entry.getKey());
                try {
                    cellVal = entry.getValue().get(item);
                } catch (IllegalAccessException e) {
                    cellVal = "字段导出错误！！！";
                }
                if (null != cellVal) {
                    cell.setCellValue(cellVal.toString());
                }
            }
        }
    }

}
```