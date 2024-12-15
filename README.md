# DdddocrForJava

Java版ddddocr验证码识别

## 导入pom文件

```xml
<dependency>
      <groupId>space.shenmuyan.org</groupId>
      <artifactId>ddddocr</artifactId>
      <version>1.0.0</version>
</dependency>
```

## 简单用法

```java
/**
 * 获取识别的验证码
 *
 * @param base64 验证码base64字符串
 * @return
 */
public static String getCode(String base64) {
    byte[] bytes = Base64.getDecoder().decode(base64);
    ByteArrayInputStream bis = new ByteArrayInputStream(bytes);
    try {
        BufferedImage bufferedImage = ImageIO.read(bis);
        return ocrEngine.recognize(bufferedImage);
    } catch (Exception e) {
        e.printStackTrace();
        return null;
    }
}

/**
 * 获取识别的验证码
 *
 * @param inputStream 验证码图片输入流
 * @return
 */
public static String getCode(InputStream inputStream) {
    try {
        BufferedImage bufferedImage = ImageIO.read(inputStream);
        return ocrEngine.recognize(bufferedImage);
    } catch (IOException e) {
        e.printStackTrace();
        return null;
    }
}
```

