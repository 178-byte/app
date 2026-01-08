# 图书管理系统 - 项目目录结构

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
│               ├── mipmap-hdpi/         # 不同密度的图标
│               ├── mipmap-mdpi/
│               ├── mipmap-xhdpi/
│               ├── mipmap-xxhdpi/
│               ├── mipmap-xxxhdpi/
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