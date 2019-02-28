# JCE记录

- **byte[]生产对称密钥**

  ```java
  SecretKey deskey = new SecretKeySpec(keybyte, Algorithm);
  ```

- **大文件加密**

  ```java
  InputStream inputStream = new FileInputStream(readPath);
  OutputStream outputStream = new FileOutputStream(writePath);
  
  byte[] key = Hex.decode("1e00bc3bb92d10f6672a1911839f4c0b");
  SecretKey secretKey = new SecretKeySpec(key, "AES");
  
  /*JCE4.2.12 软硬加密控制*/
  SwxaProvider.setsymmDevice("Cipher", "AES", "");
  Cipher cipher = Cipher.getInstance("AES/ECB/Pkcs5Padding", "SwxaJCE");
  cipher.init(Cipher.ENCRYPT_MODE, secretKey);
  
  CipherInputStream cipherInputStream = new CipherInputStream(inputStream, cipher);
  
  byte[] buffer = new byte[1024 * 1024];
  int len = 0;
  while ((len = cipherInputStream.read(buffer)) != -1) {
      outputStream.write(buffer, 0, len);
  }
  
  outputStream.close();
  inputStream.close();
  ```

  使用软加密实现，CBC模式时，无法通过硬加密获取到IV。

- **获取支持的算法**

  ```
  Provider p = new SwxaProvider();
  for (Provider.Service s : p.getServices()) {
  	if (s.getType().equalsIgnoreCase(enginName)) {
  		String algType = s.getAlgorithm();
  	}
  }  
  ```


- 待续

