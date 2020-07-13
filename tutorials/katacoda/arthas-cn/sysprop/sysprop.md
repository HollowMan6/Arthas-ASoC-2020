
`sysprop`{{execute T2}} 命令可以查看当前JVM的系统属性(`System Property`)

## 使用参考

`sysprop -h`{{execute T2}} 

```
USAGE:
   sysprop [-h] [property-name] [property-value]

 SUMMARY:
   Display, and change all the system properties.

 EXAMPLES:
 sysprop
 sysprop file.encoding
 sysprop production.mode true

 WIKI:
   https://alibaba.github.io/arthas/sysprop

 OPTIONS:
 -h, --help                                  this help
 <property-name>                             property name
 <property-value>                            property value
```

## 查看所有属性

`sysprop`{{execute T2}} 

```bash
$ sysprop
 KEY                                                  VALUE
-------------------------------------------------------------------------------------------------------------------------------------
 java.runtime.name                                    Java(TM) SE Runtime Environment
 sun.boot.library.path                                /Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/Home/jre/lib
 java.vm.version                                      25.51-b03
 user.country.format                                  CN
 gopherProxySet                                       false
 java.vm.vendor                                       Oracle Corporation
 java.vendor.url                                      http://java.oracle.com/
 path.separator                                       :
 java.vm.name                                         Java HotSpot(TM) 64-Bit Server VM
 file.encoding.pkg                                    sun.io
 user.country                                         US
 sun.java.launcher                                    SUN_STANDARD
 sun.os.patch.level                                   unknown
 java.vm.specification.name                           Java Virtual Machine Specification
 user.dir                                             /private/var/tmp
 java.runtime.version                                 1.8.0_51-b16
 java.awt.graphicsenv                                 sun.awt.CGraphicsEnvironment
 java.endorsed.dirs                                   /Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/Home/jre/lib/endors
                                                      ed
 os.arch                                              x86_64
 java.io.tmpdir                                       /var/folders/2c/tbxwzs4s4sbcvh7frbcc7n000000gn/T/
 line.separator

 java.vm.specification.vendor                         Oracle Corporation
 os.name                                              Mac OS X
 sun.jnu.encoding                                     UTF-8
 java.library.path                                    /Users/wangtao/Library/Java/Extensions:/Library/Java/Extensions:/Network/Libra
                                                      ry/Java/Extensions:/System/Library/Java/Extensions:/usr/lib/java:.
 sun.nio.ch.bugLevel
 java.specification.name                              Java Platform API Specification
 java.class.version                                   52.0
 sun.management.compiler                              HotSpot 64-Bit Tiered Compilers
 os.version                                           10.12.6
 user.home                                            /Users/wangtao
 user.timezone                                        Asia/Shanghai
 java.awt.printerjob                                  sun.lwawt.macosx.CPrinterJob
 file.encoding                                        UTF-8
 java.specification.version                           1.8
 user.name                                            wangtao
 java.class.path                                      .
 java.vm.specification.version                        1.8
 sun.arch.data.model                                  64
 java.home                                            /Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/Home/jre
 sun.java.command                                     Test
 java.specification.vendor                            Oracle Corporation
 user.language                                        en
 awt.toolkit                                          sun.lwawt.macosx.LWCToolkit
 java.vm.info                                         mixed mode
 java.version                                         1.8.0_51
 java.ext.dirs                                        /Users/wangtao/Library/Java/Extensions:/Library/Java/JavaVirtualMachines/jdk1.
                                                      8.0_51.jdk/Contents/Home/jre/lib/ext:/Library/Java/Extensions:/Network/Library
                                                      /Java/Extensions:/System/Library/Java/Extensions:/usr/lib/java
 sun.boot.class.path                                  /Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/Home/jre/lib/resour
                                                      ces.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/Home/jre/li
                                                      b/rt.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/Home/jre/l
                                                      ib/sunrsasign.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/H
                                                      ome/jre/lib/jsse.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Content
                                                      s/Home/jre/lib/jce.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Conte
                                                      nts/Home/jre/lib/charsets.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_51.jd
                                                      k/Contents/Home/jre/lib/jfr.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_51.
                                                      jdk/Contents/Home/jre/classes
 java.vendor                                          Oracle Corporation
 file.separator                                       /
 java.vendor.url.bug                                  http://bugreport.sun.com/bugreport/
 sun.cpu.endian                                       little
 sun.io.unicode.encoding                              UnicodeBig
 sun.cpu.isalist
```

## 查看单个属性

`sysprop java.version`{{execute T2}} 

```bash
$ sysprop java.version
java.version=1.8.0_51
```

## 通过`grep`来过滤

`sysprop | grep user`{{execute T2}} 

## 修改单个属性

`sysprop user.country`{{execute T2}} 

`sysprop user.country CN`{{execute T2}} 

```bash
$ sysprop user.country
user.country=US
$ sysprop user.country CN
Successfully changed the system property.
user.country=CN
```

### 自动补全

Arthas支持丰富的自动补全功能，在使用有疑惑时，可以输入`Tab`来获取更多信息。

比如输入 `sysprop java.` 之后，再输入`Tab`，会补全出对应的key：

```
$ sysprop java.
java.runtime.name             java.protocol.handler.pkgs    java.vm.version
java.vm.vendor                java.vendor.url               java.vm.name
...
```

### 历史命令的补全

支持通过`TAB`键自动补全

如果想再执行之前的命令，可以在输入一半时，按`Up/↑` 或者 `Ddown/↓`，来匹配到之前的命令。

比如之前执行过`sysprop java.version`，那么在输入`sysprop ja`之后，可以输入`Up/↑`，就会自动补全为`sysprop java.version`。

如果想查看所有的历史命令，也可以通过 `history`{{execute T2}} 命令查看到。


### pipeline

Arthas支持在pipeline之后，执行一些简单的命令，比如：

`sysprop | grep java`{{execute T2}} 

`sysprop | wc -l`{{execute T2}} 
