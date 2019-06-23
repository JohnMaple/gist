
### 加密解密

> 需要注意的是Java中的DESKeySpec类，其规定了秘钥的长度只能是8个字节，大于8字节则只取前8个字节。而且Java里DES加密采用的是默认模式：ECB模式，采用PKCS5Padding填充模式。故没有初始化向量（如果是其他模式，需要加上初始化向量）

Java DES加密解密，加密后再使用base64格式存储
```java
public static String encrypt(String str) {
    String KEY = "12345678";
    SecureRandom random = new SecureRandom();
    DESKeySpec keySpec = new DESKeySpec(KEY.getBytes());
    SecretKeyFactory keyFactory = SecretKeyFactory.getInstance(DES);
    SecretKey secretKey = keyFactory.generateSecret(keySpec);

    Cipher cipher = Cipher.getInstance(DES);
    cipher.init(Cipher.ENCRYPT_MODE, secretKey, random);
    byte[] cipherData = cipher.doFinal(str.getBytes());

    return new BASE64Encoder().encode(cipherData);
}

public static String decrypt(String str) {
    String KEY = "12345678";
    SecureRandom random = new SecureRandom();
    DESKeySpec keySpec = new DESKeySpec(KEY.getBytes());
    SecretKeyFactory keyFactory = SecretKeyFactory.getInstance(DES);
    SecretKey secretKey = keyFactory.generateSecret(keySpec);

    Cipher cipher = Cipher.getInstance(DES);
    cipher.init(Cipher.DECRYPT_MODE, secretKey, random);
    byte[] plainData = cipher.doFinal(new BASE64Decoder().decodeBuffer(str));

    return new String(plainData);
}
```

<!-- more -->

Python DES 加密解密，加密模式和Java保持一致，ECB模式，填充模式为PAD_PKCS5
```python
# -*- coding:UTF-8 -*-
import base64
import sys
from pyDes import des, PAD_PKCS5, ECB

reload(sys)
sys.setdefaultencoding('utf8')

secret_key = '12345678'

def des_encrypt(s):
    k = des(secret_key, ECB, secret_key, pad=None, padmode=PAD_PKCS5)
    en = k.encrypt(s, padmode=PAD_PKCS5)
    return base64.encodestring(en)


def des_decrypt(s):
    k = des(secret_key, ECB, secret_key, pad=None, padmode=PAD_PKCS5)
    de = k.decrypt(data=base64.decodestring(s), padmode=PAD_PKCS5)
    return de


if __name__ == '__main__':
    str_en = des_encrypt('xx')
    print(str_en)
    str_de = des_decrypt(str_en)
    print(str_de)
```
