---
description: Spring Boot/MVC导出文件的单元测试
---

```java
package com.murphyl.web.controller;

import com.murphyl.web.controller.BaseSpringTest;
import org.junit.Test;
import org.mockito.Mockito;
import org.springframework.mock.web.MockHttpServletResponse;

import javax.annotation.Resource;
import javax.servlet.ServletOutputStream;
import javax.servlet.WriteListener;
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.OutputStream;

/**
 * -
 *
 * @author luohao
 * @date 2019/6/20 13:42
 */
public class ExcelExportControllerTest extends BaseSpringTest {

    @Resource
    private ExcelExportController excelController;

    @Test
    public void exportExcelFile() throws IOException {
        excelController.exportExcelFile(mockExport(1));
    }

    private MockHttpServletResponse mockExport(int i) throws IOException {
        MockHttpServletResponse response = Mockito.mock(MockHttpServletResponse.class);

        ServletOutputStream outputStream = new ServletOutputStream() {

            FileOutputStream fileOutputStream = new FileOutputStream(new File("d:\\" + i + ".xlsx"));

            @Override
            public boolean isReady() {
                return true;
            }

            @Override
            public void setWriteListener(WriteListener writeListener) {
            }

            @Override
            public void write(int b) throws IOException {
                fileOutputStream.write(b);
            }
        };

        Mockito.when(response.getOutputStream()).thenReturn(outputStream);
        return response;
    }
}
```