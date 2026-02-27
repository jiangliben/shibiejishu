# 昆虫卵粒自动识别计数应用

## 功能特点

- 📱 支持手机摄像头实时拍摄
- 🔍 自动识别椭圆形绿色/浅绿色卵粒
- 🎯 基于图像处理算法进行计数
- 📊 实时显示检测结果

## 技术方案

- **框架**: Flutter (跨平台支持 Android/iOS)
- **图像处理**: Dart image 库
- **检测算法**: 
  - HSV 色彩空间绿色检测
  - 形态学处理
  - 椭圆形状识别
  - 连通域分析

## 安装步骤

1. 安装 Flutter SDK: https://flutter.dev/docs/get-started/install

2. 进入项目目录:
```bash
cd insect_egg_counter
```

3. 获取依赖:
```bash
flutter pub get
```

4. 运行应用:
```bash
# Android
flutter run

# iOS (需要 Mac)
flutter run
```

## 使用说明

1. 启动应用后会自动打开相机
2. 将相机对准昆虫卵粒
3. 点击"拍照计数"按钮
4. 应用会自动识别并显示卵粒数量
5. 检测到的卵粒会用红色框标记

## 优化建议

- 保持良好的光照条件
- 使用白色或对比度高的背景
- 相机距离保持在 5-15cm
- 避免阴影和反光

## 调整参数

如需调整检测精度，可修改 `lib/egg_detector.dart` 中的参数:

- 绿色阈值: `g > r + 20 && g > b + 20 && g > 80`
- 椭圆长宽比: `ratio < 1.2 || ratio > 2.5`
- 最小/最大面积: `blob.length < 10 || blob.length > 5000`
- 填充率: `fillRatio > 0.6`
