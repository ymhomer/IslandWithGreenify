# Oasisfeng - Island & Greenify

# Island 炼妖壶

本人使用Island的目的是利用Island的上帝模式来解决绿色守护权限的问题。

三星用户请注意下面2.2红色的说明。

## 1. 安装

### 1.1 事前准备

- 确保已安装ADB。如果没有可以在[这里](https://developer.android.com/studio/releases/platform-tools)下载ADB驱动和它的部件。
    - 如果不能访问可以试试[这里](https://blog.csdn.net/weixin_43927138/article/details/90477966)。
- 手机要启动开发者模式（Developer Options）

    ![../main/Image/Untitled.png](../main/Image/Untitled.png)

    一般手机启动的方式是设置 > 关于手机 > 内部编号（或者是基代版本）点击7下左右。

    ![../main/Image/Untitled%201.png](../main/Image/Untitled%201.png)

- 启动了开发者模式请打开USB调试（USB Debugging）

    ![../main/Image/Untitled%202.png](../main/Image/Untitled%202.png)

## 2. 安装Island app (炼妖壶)

![../main/Image/Untitled%203.png](../main/Image/Untitled%203.png)

### 2.1 下载及安装

- 下载Island炼妖壶
    - [酷安](https://www.coolapk.com/apk/com.oasisfeng.island)网址
- 安装Island并按照里面步骤创造工作环境（Work profile）

    ![../main/Image/Untitled%204.png](../main/Image/Untitled%204.png)

- 安装Island过后最好直接启动上帝模式（操作方法在下面），因为如果工作环境加入了用户账号很有可能上帝模式会启动失败

    如果有用户账号请进入设置 > 用户账号， 把所有工作环境的用户账号清除干净

### 2.2 启动Island的上帝模式（God Mode）

以下三个模式选一个来操作（CMD指令），不知道怎么选就选上帝模式就好

> 部分三星手机启动上帝模式可能会造成开机失败，所以不建议三星手机启动上帝模式

- 上帝模式

    ```powershell
    adb -d shell dpm set-device-owner com.oasisfeng.island/.IslandDeviceAdminReceiver
    ```

- 半上帝模式

    ```powershell
    adb -d shell dpm set-profile-owner --user 0 --name Mainland com.oasisfeng.island/.IslandDeviceAdminReceiver
    ```

- Android5.X

    ```powershell
    adb -d shell dpm set-profile-owner com.oasisfeng.island/.IslandDeviceAdminReceiver 0
    ```

- ##如果上帝模式启动失败请输入以下指令
    - adb -d shell settings put global device_provisioned 0
    - 重新输入上帝模式的指令（如 adb -d shell dpm set-device-owner com.oasisfeng.island/.IslandDeviceAdminReceiver）
    - adb -d shell settings put global device_provisioned 1 （最后这一步很重要，必须输入，否则接受不到信息通知）

### 如果要卸载Island（请关闭上帝模式才卸载）

- 卸载方法

    Island, Settings（设定） - Scoped Settings - Mainland（主要岛屿）, 选择 “Deactivate”（关闭）

    （我自己翻译的，大致上是这个意思）

    注意, 如果你还要重新启动上帝模式，请先清理所有的Island空间。

    如果是半上帝模式可以不损失任何Island的空间。

# Greenify - 绿色守护

- 下载Greenify绿色守护

    [谷歌](https://play.google.com/store/apps/details?id=com.oasisfeng.greenify)网址

    [酷安](https://www.coolapk.com/apk/com.oasisfeng.greenify)网址

- Greenify绿色守护（CMD指令）

    ```powershell
    adb -d shell am force-stop com.oasisfeng.greenify
    adb -d shell pm grant com.oasisfeng.greenify android.permission.GET_APP_OPS_STATS
    adb -d shell pm grant com.oasisfeng.greenify android.permission.READ_LOGS
    adb -d shell pm grant com.oasisfeng.greenify android.permission.WRITE_SECURE_SETTINGS
    adb -d shell pm grant com.oasisfeng.greenify android.permission.DUMP
    adb -d shell am force-stop com.oasisfeng.greenify
    ```
