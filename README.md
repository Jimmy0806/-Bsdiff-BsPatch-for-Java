# Bsdiff-BsPatch-for-Java
适用于Java调用的 Bsdiff/BsPatch差分包开源库

Java创建JNI对应类BsDiff
```Java
package com.sswl;

public class BsDiff {
    static {
        //这个bz2.dll是bspatch.dll所依赖到的，必须要写上来，而且必须在load bspatch.dll之前，否则会报错：
       //Exception in thread "main" java.lang.UnsatisfiedLinkError: ..\bspatch.dll: Can't find dependent libraries
        System.load("E:\\AS-workspace\\bspatch\\x64\\Release\\bz2.dll");
        System.load("E:\\AS-workspace\\bspatch\\x64\\Release\\bspatch.dll");
    }

    public static native boolean make(String oldFilePath, String newFilePath, String patchPath);

    public static native boolean diff(String oldFilePath, String newFilePath, String patchPath);
}
```
调用类Main

```Java
/**
 * @Description: 打差分包
 * @Author: jimmyliang
 * @CreateDate: 2020/9/4
 */
public class Main {

    public static void main(String[] args) {
//        BsDiff.diff("C:\\Users\\Administrator\\Desktop\\old.apk",
//                "C:\\Users\\Administrator\\Desktop\\new.apk",
//                "C:\\Users\\Administrator\\Desktop\\patch.apk");

        BsDiff.make("C:\\Users\\Administrator\\Desktop\\old.apk",
                "C:\\Users\\Administrator\\Desktop\\new12.apk",
                "C:\\Users\\Administrator\\Desktop\\patch.apk");
    }
}
```
