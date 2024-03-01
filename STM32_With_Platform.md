# 如何使用Platform編寫STM32

#### Platform創建專案


![Platform創建專案](https://github.com/hamster-allen/STM32_With_Platform/blob/master/STM32_With_Platform_picture/Platform%E5%89%B5%E5%BB%BA%E5%B0%88%E6%A1%88.png)


#### STM32CubeMX-選擇晶片


![MX_創建1](https://github.com/hamster-allen/STM32_With_Platform/blob/master/STM32_With_Platform_picture/MX_%E5%89%B5%E5%BB%BA1.png)


#### STM32CubeMX-創建路徑與IDE設定
* 創建路徑與Platform專案相同
* IDE設置為**Makefile**


![MX_創建2](https://github.com/hamster-allen/STM32_With_Platform/blob/master/STM32_With_Platform_picture/MX_%E5%89%B5%E5%BB%BA2.png)


#### STM32CubeMX-程式生成設定


![MX_創建3](https://github.com/hamster-allen/STM32_With_Platform/blob/master/STM32_With_Platform_picture/MX_%E5%89%B5%E5%BB%BA3.png)


#### Platform-創建成功
* lib -> 自訂函數庫資料夾
* extra_script.py -> 將輸出的.bin檔轉換成.hex檔
* platformio.ini -> 更改編譯配置


![MX_創建4](https://github.com/hamster-allen/STM32_With_Platform/blob/master/STM32_With_Platform_picture/MX_%E5%89%B5%E5%BB%BA4.png)


#### Platform-自訂函數庫資料夾格式

* lib
  * LED
    * LED.h
    * LED.c
  * 其他函數資料夾
    * 頭文件
    * C文件
   

#### Platform-將輸出的.bin檔轉換成.hex檔

```
Import("env")

env.AddPostAction(
    "$BUILD_DIR/${PROGNAME}.elf",
    env.VerboseAction(" ".join([
        "$OBJCOPY", "-O", "ihex", "-R", ".eeprom",
        "$BUILD_DIR/${PROGNAME}.elf", "$BUILD_DIR/${PROGNAME}.hex"
      ]), "Building $BUILD_DIR/${PROGNAME}.hex")
)
```

#### Platform-更改編譯配置

1. 設置主程式路徑
2. 要編譯的函數庫路徑
3. 編譯後，將輸出的.bin檔轉換成.hex檔

![MX_創建5](https://github.com/hamster-allen/STM32_With_Platform/blob/master/STM32_With_Platform_picture/MX_%E5%89%B5%E5%BB%BA5.png)






















