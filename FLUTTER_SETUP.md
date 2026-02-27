# Flutter 安装和APK构建指南

## 一、安装 Flutter SDK

### Windows 系统安装步骤：

1. **下载 Flutter SDK**
   - 访问：https://flutter.dev/docs/get-started/install/windows
   - 或直接下载：https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.x.x-stable.zip

2. **解压到目录**
   ```
   建议路径：C:\src\flutter
   ```

3. **添加到环境变量**
   - 右键"此电脑" → 属性 → 高级系统设置 → 环境变量
   - 在"用户变量"中找到 Path，点击编辑
   - 添加：`C:\src\flutter\bin`
   - 点击确定保存

4. **验证安装**
   打开新的命令提示符窗口：
   ```bash
   flutter --version
   flutter doctor
   ```

5. **安装 Android 工具链**
   ```bash
   flutter doctor --android-licenses
   ```
   按 `y` 接受所有许可协议

## 二、构建 APK

安装完成后，在项目目录执行：

```bash
cd C:\Users\jiang\Desktop\insect_egg_counter
flutter pub get
flutter build apk --release
```

构建成功后，APK位置：
```
insect_egg_counter\build\app\outputs\flutter-apk\app-release.apk
```

## 三、安装到手机

### 方法1：直接传输（最简单）
1. 将 `app-release.apk` 复制到手机
2. 在手机上点击安装
3. 允许"安装未知来源应用"

### 方法2：使用 ADB
```bash
adb install build\app\outputs\flutter-apk\app-release.apk
```

## 快速命令参考

```bash
# 检查环境
flutter doctor

# 获取依赖
flutter pub get

# 构建APK
flutter build apk --release

# 直接安装到连接的手机
flutter install

# 运行应用（开发模式）
flutter run
```

## 如果不想安装 Flutter

你也可以：
1. 使用在线构建服务（如 Codemagic、GitHub Actions）
2. 请有 Flutter 环境的朋友帮忙构建
3. 使用 Docker 容器构建

## 最小系统要求

- Windows 10 或更高版本
- 磁盘空间：2.5 GB
- Git for Windows
- Android Studio（可选，但推荐）
