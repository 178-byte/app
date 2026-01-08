# 图书管理系统 - Android Studio导入与使用指南

## 一、开发环境要求

| 环境 | 版本要求 |
|------|----------|
| Android Studio | Arctic Fox (2020.3.1) 或更高版本 |
| Android Gradle Plugin | 8.2.0 |
| Kotlin | 1.9.22 |
| SDK Platform | Android 14 (API 34) |
| Min SDK Version | Android 8.0 (API 26) |
| Build Tools Version | 34.0.0 |

## 二、项目目录结构

```
BookManagementSystem/
├── app/
│   ├── build.gradle                    # Module级Gradle配置
│   ├── proguard-rules.pro              # ProGuard混淆规则
│   └── src/
│       └── main/
│           ├── AndroidManifest.xml     # 应用清单文件
│           ├── java/
│           │   └── com/
│           │       └── example/
│           │           └── bookmanagement/
│           │               ├── MainActivity.kt          # 主界面（图书列表）
│           │               ├── AddBookActivity.kt       # 添加图书
│           │               ├── EditBookActivity.kt      # 编辑图书
│           │               ├── BorrowActivity.kt        # 借阅操作
│           │               ├── ReturnActivity.kt        # 归还操作
│           │               ├── RecordActivity.kt        # 借阅记录
│           │               ├── StatisticsActivity.kt    # 统计信息
│           │               ├── database/
│           │               │   └── DatabaseHelper.kt    # SQLite数据库帮助类
│           │               └── model/
│           │                   ├── Book.kt              # 图书实体类
│           │                   ├── BorrowRecord.kt      # 借阅记录实体类
│           │                   └── Reader.kt            # 读者实体类
│           └── res/
│               ├── drawable/            # 图片资源
│               ├── layout/              # 布局文件
│               │   ├── activity_main.xml             # 主界面布局
│               │   ├── activity_add_book.xml         # 添加图书布局
│               │   ├── activity_edit_book.xml        # 编辑图书布局
│               │   ├── activity_borrow.xml           # 借阅操作布局
│               │   ├── activity_return.xml           # 归还操作布局
│               │   ├── activity_record.xml           # 借阅记录布局
│               │   ├── activity_statistics.xml       # 统计信息布局
│               │   └── book_item.xml                 # 图书列表项布局
│               ├── mipmap-*/             # 不同密度的图标
│               └── values/              # 资源值
│                   ├── colors.xml
│                   ├── strings.xml
│                   ├── styles.xml
│                   └── themes.xml
├── build.gradle                        # Project级Gradle配置
├── gradle/
│   └── wrapper/
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── gradle.properties                   # Gradle属性配置
└── settings.gradle                     # 项目设置
```

## 三、Android Studio导入项目步骤

### 1. 打开Android Studio

- 启动Android Studio应用程序
- 如果你已经打开了一个项目，点击菜单栏的 `File` → `Close Project` 关闭当前项目

### 2. 导入项目

- 在Android Studio欢迎界面，选择 `Open an existing project`
- 在文件浏览器中，导航到 `BookManagementSystem` 项目的根目录
- 选中 `BookManagementSystem` 文件夹，然后点击 `OK`

### 3. 等待项目同步

- Android Studio会自动开始同步项目，下载所需的依赖项
- 同步过程可能需要几分钟时间，取决于你的网络速度
- 确保同步完成后没有错误信息

### 4. 配置SDK和NDK路径（如果需要）

- 如果Android Studio提示SDK或NDK路径错误，点击 `File` → `Project Structure`
- 在 `SDK Location` 标签页中，确保SDK和NDK路径正确
- 点击 `OK` 保存设置

### 5. 运行项目

- 连接Android设备或启动模拟器
- 点击工具栏上的 `Run` 按钮（绿色三角形），或者使用快捷键 `Shift + F10`
- 在弹出的 `Select Deployment Target` 对话框中，选择你的设备或模拟器
- 点击 `OK`，等待应用安装并运行

## 四、配置签名文件、生成APK/ABB包

### 1. 生成签名密钥

#### 步骤1：打开签名密钥生成向导
- 点击菜单栏的 `Build` → `Generate Signed Bundle / APK...`
- 在弹出的对话框中，选择 `APK` 或 `Android App Bundle（ABB）`，然后点击 `Next`

#### 步骤2：创建新的密钥库
- 点击 `Create new...` 按钮（如果你还没有签名密钥）

#### 步骤3：填写密钥库信息
- **Key store path**：点击 `...` 选择密钥库文件保存位置，例如 `C:\Users\YourName\keystore.jks`
- **Password**：输入密钥库密码（至少6个字符）
- **Confirm**：再次输入相同的密码
- **Alias**：输入密钥别名，例如 `bookapp`
- **Password**：输入密钥密码（可以与密钥库密码相同）
- **Confirm**：再次输入密钥密码
- **Validity (years)**：设置密钥有效期，建议设置为25年或更长
- **Certificate**：填写证书信息（姓名、组织、城市、州、国家代码）
- 点击 `OK` 保存密钥库

### 2. 签署APK/ABB包

#### 步骤1：选择密钥库和密钥
- 在 `Generate Signed Bundle / APK` 对话框中，选择刚刚创建的密钥库文件
- 输入密钥库密码和密钥密码
- 点击 `Next`

#### 步骤2：配置构建类型和目标
- **Build variant**：选择 `release`（发布版本）
- **Destination folder**：选择APK/ABB包的保存位置
- 对于APK，选择 `V1 (Jar Signature)` 和 `V2 (Full APK Signature)`
- 对于ABB，选择 `V1 (Jar Signature)` 和 `V2 (Full APK Signature)`
- 点击 `Finish` 开始构建

### 3. 查看生成的包

- 构建完成后，Android Studio会显示 `Build APK(s) completed successfully` 或 `Build Bundle(s) completed successfully`
- 点击 `Locate` 按钮查看生成的APK/ABB文件
- APK文件位于 `app\release\app-release.apk`
- ABB文件位于 `app\release\app-release.aab`

## 五、核心功能说明

### 1. 图书管理
- **添加图书**：点击主界面的"添加图书"按钮，填写图书信息（书名、作者、ISBN、分类、库存）
- **编辑图书**：点击图书列表项，进入编辑界面修改图书信息
- **删除图书**：长按图书列表项，选择"删除图书"选项
- **查询图书**：在搜索栏输入关键词（书名或作者）进行搜索

### 2. 借阅管理
- **借阅图书**：长按图书列表项，选择"借阅图书"选项，填写读者信息（姓名、学号）
- **归还图书**：进入"借阅记录"界面，点击"归还图书"按钮，选择要归还的图书
- **查看借阅记录**：点击主界面的"借阅记录"按钮，查看所有借阅记录

### 3. 基础统计
- 点击主界面的"统计信息"按钮，查看：
  - 图书总数
  - 可借阅图书数量
  - 已借阅图书数量
  - 未归还图书数量

## 六、代码中关键逻辑说明

### 1. 数据库操作（DatabaseHelper.kt）

- **数据库初始化**：在 `onCreate` 方法中创建 `books`、`readers` 和 `borrow_records` 三个表
- **事务处理**：借阅和归还操作使用事务确保数据一致性
- **增删改查**：提供了完整的图书、读者和借阅记录的CRUD方法

### 2. 页面跳转逻辑

- **主界面到添加图书**：`MainActivity` → `AddBookActivity`
- **主界面到编辑图书**：点击图书列表项 → `EditBookActivity`
- **主界面到借阅操作**：长按图书列表项选择"借阅图书" → `BorrowActivity`
- **主界面到借阅记录**：点击"借阅记录"按钮 → `RecordActivity`
- **主界面到统计信息**：点击"统计信息"按钮 → `StatisticsActivity`
- **借阅记录到归还操作**：点击"归还图书"按钮 → `ReturnActivity`

### 3. 数据流转

- 图书数据：`MainActivity` ←→ `DatabaseHelper` ←→ SQLite数据库
- 借阅记录：`RecordActivity`/`ReturnActivity` ←→ `DatabaseHelper` ←→ SQLite数据库
- 统计数据：`StatisticsActivity` ←→ `DatabaseHelper` ←→ SQLite数据库

## 七、常见问题及解决方案

### 1. 同步项目时出现依赖错误
- 确保Android Studio已连接到互联网
- 点击 `File` → `Sync Project with Gradle Files` 重新同步
- 检查 `build.gradle` 文件中的依赖版本是否正确

### 2. 运行项目时出现编译错误
- 检查代码中是否有语法错误
- 确保所有导入的类都已正确引用
- 清理项目：点击 `Build` → `Clean Project`

### 3. 安装应用时出现签名错误
- 确保使用了正确的签名密钥
- 检查 `build.gradle` 文件中的签名配置是否正确
- 卸载设备上已安装的同名应用后重新安装

### 4. 应用崩溃或无响应
- 查看Logcat中的错误信息
- 检查数据库操作是否正确关闭了Cursor
- 确保所有异步操作都在正确的线程中执行

## 八、生成签名APK/ABB的截图说明

### 1. 生成签名APK步骤

1. **打开生成向导**：
   - 菜单：`Build` → `Generate Signed Bundle / APK...`

2. **选择APK选项**：
   - 选择 `APK` → `Next`

3. **配置签名信息**：
   - 选择或创建密钥库
   - 输入密钥库和密钥密码
   - 点击 `Next`

4. **选择构建类型**：
   - 选择 `release` 构建类型
   - 勾选签名版本 `V1` 和 `V2`
   - 点击 `Finish`

5. **查看生成结果**：
   - 构建完成后，点击 `Locate` 查看APK文件

### 2. 生成Android App Bundle（ABB）步骤

1. **打开生成向导**：
   - 菜单：`Build` → `Generate Signed Bundle / APK...`

2. **选择Bundle选项**：
   - 选择 `Android App Bundle` → `Next`

3. **配置签名信息**：
   - 选择或创建密钥库
   - 输入密钥库和密钥密码
   - 点击 `Next`

4. **选择构建类型**：
   - 选择 `release` 构建类型
   - 点击 `Finish`

5. **查看生成结果**：
   - 构建完成后，点击 `Locate` 查看ABB文件

## 九、注意事项

1. **数据库备份**：
   - 应用使用SQLite本地数据库，数据存储在设备内部存储中
   - 建议定期备份数据库文件，避免数据丢失

2. **权限说明**：
   - 应用不需要特殊权限，只使用了本地存储权限（自动授予）

3. **版本升级**：
   - 升级应用时，确保使用相同的签名密钥
   - 数据库升级逻辑已在 `DatabaseHelper.onUpgrade` 方法中实现

4. **性能优化**：
   - 大量数据时，建议优化数据库查询语句
   - 考虑使用分页加载大型列表

5. **安全性**：
   - 发布版本建议启用ProGuard混淆
   - 数据库操作已使用事务确保数据一致性

---

通过以上步骤，你可以成功导入、编译和运行图书管理系统App，并生成签名的APK或ABB包。如果在使用过程中遇到任何问题，请参考常见问题及解决方案，或查阅Android Studio官方文档。