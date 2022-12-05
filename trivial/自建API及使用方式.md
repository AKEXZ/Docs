## 一言API

https://api.ak0.cn/yiyan/

### 请求示例 GET

https://api.ak0.cn/yiyan/?format=js

### 返回数据

``javascript
document.write('桑丘，让他们管我叫疯子吧，我还疯得不够，所以得不到他们的赞许。');
``

### 调用效果

桑丘，让他们管我叫疯子吧，我还疯得不够，所以得不到他们的赞许。

### 引用代码

`<script src="https://api.ak0.cn/yiyan/?format=js"></script>`

### 效果

<script src="https://api.ak0.cn/yiyan/?format=js"></script>

### 自定义参数

| 参数名 | 参数值 | 可选/必填 | 描述 |
| :------------: | :------------: | :------------: | :------------: |
| format | text | 默认 | 返回文本格式 |
| format | js | 可选 | 返回document.write格式 |
| format | json | 可选 | 返回json格式  |

------------

## QQ在线状态

https://api.ak0.cn/qqzx/

### 请求示例 GET

https://api.ak0.cn/qqzx/?qq=2637033514

### 返回数据

`{"code":"20","msg":"电脑离线"};`

### 自定义参数

| 参数名 | 参数值 | 可选/必填 | 描述 |
| :------------: | :------------: | :------------: | :------------: |
| qq | QQ号码 | 必填 | 返回文本格式 |

------------

## QQ头像获取API

https://api.ak0.cn/qqimg/

### 请求示例 GET

https://api.ak0.cn/qqimg/?qq=2637033514

### 返回数据

`{"code":"20","msg":"电脑离线"};`

### 自定义参数

| 参数名 | 参数值 | 可选/必填 | 描述 |
| :------------: | :------------: | :------------: | :------------: |
| qq | QQ号码 | 必填 | 返回文本格式 |

------------

## 随机图片API

https://api.ak0.cn/images/

### 请求实例

`https://api.ak0.cn/images/?Category=anime`

### 调用效果

https://api.ak0.cn/images/?Category=anime

### 自定义参数

| 参数名 | 参数值 | 可选/必填 | 描述 |
| :------------: | :------------: | :------------: | :------------: |
| id   | number | 可选 | 如ID对应图片不存在则随机返回一张图片 |
| Category | data | 默认 | 所有类别 |
| Category | anime | 可选 | 动漫图 |
| Category | nature | 可选 | 风景图 |
| type | json | 可选 | 以json返回 |
| type | quantity | 可选 | 返回图片总数 |
| type | string | 可选 | 返回主图 |

