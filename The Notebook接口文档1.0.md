# The Notebook项目API接口文档
## 1.1 API 接口说明
- 接口基准地址：`http://localhost:xxxx`
- 数据返回格式统一使用 JSON ( 如有其他格式将在接口文档声明 )

### 1.1.1 支持的请求方法
- POST
- GET

### 1.1.2 通用返回状态说明

| 状态码 | 含义                  | 说明                                                                |
| ------ | --------------------- | ------------------------------------------------------------------- |
| 200    | OK                    | 请求成功                                                            |
| 404    | NOT FOUND             | 请求的资源不存在                                                    |
| 500    | INTERNAL SERVER ERROR | 内部服务端错误<br />(如:传入的参数或者文件格式错误<br />其他错误等) |
| 403    | FORBIDDEN             | 被禁止访问                                                          |
| 401    | UNAUTHORIZED          | 未授权<br />(登录状态过期或未登录时返回)                            |

## 1.2. 数据库 设计

>数据库名 : xxx
>
>数据库账号 : root
>
>数据库密码 : root
>
>数据库 :utf8  排序规则 :utf8_unicode_ci
### 1.2.1.用户表


| 字段名           | 含义             | 数据类型   | 说明               |
| ---------------- | ---------------- | ---------- | ------------------ |
| id               | 用户id           | int        | 必填               |
| <u>*token*</u>   | 加密后的数据     | varchar    | (可不使用)         |
| username         | 用户             | varchar    | 必填               |
| password         | 密码             | varchar    | 必填               |
| *<u>head</u>*    | 头像缩略图       | mediumtext | (可不使用)         |
| *<u>mailbox</u>* | 邮箱             | varchar    | (可不使用)         |
| address          | 地址籍贯         | varchar    | 可不填             |
| sex              | 性别             | varchar    | 必填               |
| createtime       | 用户创建时间     | datetime   | CURRENT_TIMESTAMP  |
| modifytime       | 最近一次修改时间 | datetime   | CURRENT_TIMESTAMP  |
| companionId      | 伴侣id           | int        | 可不填(屏蔽纪念日) |
| message          | 情侣消息         | mediumtext | 可不填             |

### 1.2.2 记事表

| 字段名     | 含义             | 数据类型   | 说明              |
| ---------- | ---------------- | ---------- | ----------------- |
| n_id       | 记事本id         | int        | 必填              |
| u_id       | 用户id           | int        | 必填              |
| title      | 标题             | mediumtext | 必填              |
| content    | 记事内容         | mediumtext | 必填              |
| createtime | 记事本创建时间   | datetime   | CURRENT_TIMESTAMP |
| modifytime | 最近一次修改时间 | datetime   | CURRENT_TIMESTAMP |

### 1.2.2 记账关系表

| 字段名 | 含义   | 数据类型 | 说明 |
| ------ | ------ | -------- | ---- |
| p_id   | 记账id | int      | 必填 |
| u_id   | 用户id | int      | 必填 |

### 1.2.2 记账表

| 字段名                | 含义     | 数据类型 | 说明 |
| --------------------- | -------- | -------- | ---- |
| p_id                  | 记账id   | int      | 必填 |
| expenditureStatistics | 支出统计 | int      | 必填 |
| incomeStatistics      | 收入统计 | int      | 必填 |

### 1.2.2 详细收支情况表

| 字段名     | 含义     | 数据类型          | 说明 |
| ---------- | -------- | ----------------- | ---- |
| p_id       | 记账id   | int               | 必填 |
| income     | 收入信息 | mediumtext        | 选填 |
| expend     | 支出信息 | mediumtext        | 选填 |
| remarks    | 备注信息 | mediumtext        | 必填 |
| createtime | 创建时间 | CURRENT_TIMESTAMP | 必填 |

### 1.2.2 伴侣关系表

| 字段名 | 含义   | 数据类型 | 说明 |
| ------ | ------ | -------- | ---- |
| p_id   | 伴侣id | int      | 必填 |
| m_id   | 男生id | int      | 必填 |
| f_id   | 女生id | int      | 必填 |

### 1.2.2 纪念日表

| 字段名     | 含义             | 数据类型   | 说明              |
| ---------- | ---------------- | ---------- | ----------------- |
| h_id       | 纪念日id         | int        | 必填              |
| p_id       | 伴侣id           | int        | 必填              |
| happy_day  | 纪念日           | datetime   | 必填              |
| remark     | 备注信息         | mediumtext | 必填              |
| goTop      | 是否置顶         | int        | 必填              |
| modifytime | 最近一次修改时间 | datetime   | CURRENT_TIMESTAMP |