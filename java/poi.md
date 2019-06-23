
### POI加密解密

> 场景一：创建Workbook，加密后以流的方式返回给前段

```java
@RequestMapping("/download")
public void download(HttpServletResponse response) throws Exception {
    Workbook workbook = WorkbookFactory.create(this.getClass().getClassLoader().getResourceAsStream('filename.xslx'));

    // 模式需要是EncryptionMode.standard，不然打开时会提示文件损坏或被篡改
    EncryptionInfo info = new EncryptionInfo(EncryptionMode.standard);
    Encryptor enc = info.getEncryptor();
    enc.confirmPassword("123456");

    POIFSFileSystem fs = new POIFSFileSystem();

    OutputStream os = enc.getDataStream(fs);
    workbook.write(os);
    workbook.close();

    OutputStream outputStream = response.getOutputStream();
    fs.writeFilesystem(outputStream);
}
```

<!-- more -->

> 场景二：加密文件

```java
EncryptionInfo info = new EncryptionInfo(EncryptionMode.standard);
Encryptor enc = info.getEncryptor();
enc.confirmPassword("123456");

POIFSFileSystem fs = new POIFSFileSystem();

OPCPackage opc = OPCPackage.open(new File("/Users/root/Desktop/test.xlsx"), PackageAccess.READ_WRITE);
OutputStream os = enc.getDataStream(fs);
opc.save(os);
opc.close();

FileOutputStream fos = new FileOutputStream("/Users/root/Desktop/test1.xlsx");
fs.writeFilesystem(fos);
fos.close();
```
