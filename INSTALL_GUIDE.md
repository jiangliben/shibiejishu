# 安卓应用安装指南

## 方法一：构建并安装APK（推荐）

### 1. 构建APK
在项目根目录执行：
```bash
cd insect_egg_counter
flutter build apk --release
```

构建完成后，APK文件位置：
```
insect_egg_counter/build/app/outputs/flutter-apk/app-release.apk
```

### 2. 安装到手机

#### 方式A：通过USB数据线安装
1. 手机开启开发者选项和USB调试
   - 设置 → 关于手机 → 连续点击"版本号"7次
   - 设置 → 开发者选项 → 开启"USB调试"
2. 用数据线连接手机和电脑
3. 执行安装命令：
```bash
cd insect_egg_counter
flutter install
```
或使用adb：
```bash
adb install build/app/outputs/flutter-apk/app-release.apk
```

#### 方式B：直接传输APK文件
1. 将 `app-release.apk` 文件传输到手机（通过微信、QQ、数据线等）
2. 在手机上找到APK文件
3. 点击安装（需要允许"安装未知来源应用"权限）

#### 方式C：通过ADB无线安装
1. 确保手机和电脑在同一WiFi网络
2. 手机开启USB调试和无线调试
3. 执行：
```bash
adb connect 手机IP:端口
adb install build/app/outputs/flutter-apk/app-release.apk
```

## 方法二：直接运行到手机（开发模式）

### 通过USB连接
1. 手机开启USB调试
2. 连接数据线
3. 执行：
```bash
cd insect_egg_counter
flutter run --release
```

### 通过WiFi无线运行
1. 首先通过USB连接手机
2. 执行：
```bash
adb tcpip 5555
adb connect 手机IP:5555
```
3. 拔掉数据线，执行：
```bash
cd insect_egg_counter
flutter run --release
```

## 注意事项

1. **首次安装**需要在手机设置中允许"安装未知来源应用"
2. **相机权限**：首次运行时需要授予相机权限
3. **最小系统要求**：Android 5.0 (API 21) 及以上
4. **APK大小**：约20-30MB（包含Flutter引擎）

## 常见问题

### Q: 提示"未安装应用"
A: 可能是签名问题或系统版本过低，尝试重新构建或检查手机系统版本

### Q: 无法打开相机
A: 检查应用权限设置，确保已授予相机权限

### Q: adb命令不可用
A: 需要安装Android SDK Platform Tools，或使用Android Studio自带的adb

## 快速开始

最简单的方式：
```bash
cd insect_egg_counter
flutter build apk --release
```
然后将生成的APK文件传到手机安装即可。
