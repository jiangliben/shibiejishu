# 不安装 Flutter SDK 构建 APK 的方法

## 方法1：GitHub Actions（最简单）✨

我已经创建了配置文件 [`.github/workflows/build-apk.yml`](.github/workflows/build-apk.yml:1)

### 使用步骤：
1. 在 GitHub 创建新仓库
2. 上传项目代码
3. 代码推送后自动构建
4. 在 Actions 页面下载 APK

```bash
cd insect_egg_counter
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/你的用户名/仓库名.git
git push -u origin main
```

构建完成后访问：`https://github.com/你的用户名/仓库名/actions` 下载 APK

---

## 方法2：Codemagic

1. 访问 https://codemagic.io
2. 用 GitHub 账号登录
3. 连接仓库并选择 Flutter 项目
4. 点击 "Start new build"
5. 下载生成的 APK

---

## 方法3：Docker（如果已安装）

```bash
docker pull cirrusci/flutter:stable
docker run --rm -v "%cd%\insect_egg_counter:/app" -w /app cirrusci/flutter:stable sh -c "flutter pub get && flutter build apk --release"
```

APK 位置：`build\app\outputs\flutter-apk\app-release.apk`

---

## 推荐：GitHub Actions

**优点**：
- 完全免费
- 自动化构建
- 无需本地环境
- 每次代码更新自动生成新 APK
