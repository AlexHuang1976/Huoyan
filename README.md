上海链井科技有限公司<<火眼金睛>>区块链项目开发手记
--Alex 2017-06-28
一．	开发环境：android studio 2.3.3(自带SDK)
1.	Android Studio千万不要安装在programe files下，以后编译会报SDK Location错误（路径不能有空格），通常在D：盘新建一个AndroidStudio文件夹；
2.	为更新NDK，Gradle,需要翻墙，设置http proxy:  sdk.gdgshanghai.com 端口号：8000
二．引用opencv
1．	从官网下载opencv-3.2.0-android-sdk文件,解压后放在AndroidStudio与SDK平级的目录下；
2．	新建项目后，在FILE->NEW->IMPORT MODULE，选择opencv文件夹\SDK\JAVA,完成导入
3．	在项目中，FILE->Project Structure中，选中左边“APP”，在Dependecies中选择“+”号，选择“Module Dependency”,选取刚才导入的openCVLibrary320
4．	在“android视图”下，调整 openCVLibrary320的build.gradle文件，将compileSdkVersion(26)，minSdkVersion(15),targetSdkVersion(26)成与app的build.gradle文件一致。

三．	调用opencv示例程序（免opencv manager）
1.	记下项目的包名，我的是“qqcoin.com.huoyan”
2.	将解压的opencv文件夹\sdk\native下的libs文件夹，复制到项目的app\src\main文件夹下，重命名为jniLibs
3.	将opencv示例程序的AndoidManifest.xml覆盖 项目app\src\main的AndoidManifest.xml,更改为项目当前包名；
4.	将示例程序res文件夹下的layout、values、drawable等覆盖到app\src\main\res下相同文件。
5.	将示例程序src\包路径\下的java文件复制到项目app\src\main\java\包路径下面，将java文件的包号更新为项目包名；
6.	在MainActivity类增加一条代码：
Static{System.loadlibrary(“opencv_java3”);}

其他坑：360手机助手会占用ADT虚拟设备的端口，导到RUN时虚拟设备闪退；————调用摄像头必须用真机调试。
