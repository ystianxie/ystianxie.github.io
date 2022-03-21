# Adb常用命令

## 1. 获取手机状态

- 获取锁屏状态

  ```shell
  adb shell dumpsys window policy
  ```

  1. 关闭状态： 
     - dreaming=true 
     - screenState=SCREEN_STATE_OFF 
     -  interactiveState=INTERACTIVE_STATE_SLEEP
  2. 锁屏状态： 
     - dreaming=false
     - screenState=SCREEN_STATE_ON
     - interactiveState=INTERACTIVE_STATE_AWAKE
  3. 解锁状态：
     - showing=false
     - mIsShowing=false
     - mInputRestricted=false
     - dreaming=false
     - screenState=SCREEN_STATE_ON
     - interactiveState=INTERACTIVE_STATE_AWAKE



##2. 有用的命令

   - input

     ```shell
     adb shell input keyevent 26
     adb shell input keyevent 82
     ```

     *1. keyevent: 26 代表电源键 power*
     *2. keyevent: 82 代表尝试解锁*

   - 发送广播关闭USB

     ```shell
     adb shell am broadcast -a android.hardware.usb.action.USB_STATE --ez connected "false"
     ```

   - 关闭gyroscope(陀螺仪)

     ```shell
     adb shell echo 0 > /sys/class/sensors/bmg160/enable
     ```

     *硬件相关，可能有变动*

   - 查看Notification：“找出状态栏广告的主人”

     ```shell
     adb shell dumpsys statusbar
     ```

   - 模拟启动activity

     ```shell
     adb shell am start  <INTENT> : start an Activity
     ```

   - 开关WiFi

     ```shell
     svc wifi [enable|disable]
     ```

   - 开关移动网络

     ```shell
     svc data [enable|disable]
     ```

   - 手机重启

     ```shell
     svc power reboot [reason]
     //Perform a runtime shutdown and reboot device with specified reason.
     ```

   - 手机关机

     ```shell
     svc power shutdown
     ```

   - 查看apk安装列表

     ```shell
     adb shell pm list packages [-s][-3]
     ```

     *-s : 系统应用 -3 ：第三方应用*
     
   - dump input
   
     ```shell
     adb shell dumpsys input
     ```
   
   - 查看activity详细信息，如显示大小，布局等等
   
     ```shell
     adb shell dumpsys activity a
     ```
   
     

		
