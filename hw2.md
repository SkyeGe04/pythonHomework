葛天恺_23电信2班_202313410007
### 2.1 数据编号

str.zfil(x)用于补0到指定的长度，如：
```
print('7'.zfill(2))     # 输出 07
print('85'.zfill(5))    # 输出 00085
print('001'.zfill(5))   # 输出 00001
```


```python
datasort = []
i = 0
data = '莱科宁 236,汉密尔顿 358,维泰尔 294,维斯塔潘 216,博塔斯 227'  # 字符串数据
newlist = data.split(',')  # 将字符串数据分割为列表

# 将车手与积分数据添加到新的列表中
for item in newlist:
    opendata = item.split(' ')
    datasort.append([opendata[1], opendata[0]])  # 把积分放前面，方便排序

datasort.sort(reverse=True)  # 数据降序排列（按积分）

print("\033[1;34m" + "*" * 35)
print("输出F1大奖赛车手积分".center(25))
print("*" * 35 + "\033[0m")
print("排名\t车手\t\t积分")

# 循环打印每个赛车手与对应积分
for item in datasort:
    i = i + 1
    print(str(i).zfill(2), '\t' + item[1] + '\t\t' + item[0])

```

    [1;34m***********************************
           输出F1大奖赛车手积分       
    ***********************************[0m
    排名	车手		积分
    01 	汉密尔顿		358
    02 	维泰尔		294
    03 	莱科宁		236
    04 	博塔斯		227
    05 	维斯塔潘		216
    

### 2.2 数据编号2

```python
"{:0<2}".format('8.1')
```
意思是：把字符串 `'8.1'` 填充到长度为 2 的格式中，左对齐（`<`），用 `0` 来填充右边的空位。

---

📌 格式说明：

| 部分        | 含义                     |
|-------------|--------------------------|
| `:`         | 表示要格式化开始         |
| `0`         | 用字符 `'0'` 来填补空位 |
| `<`         | 左对齐                   |
| `2`         | 总宽度为 2               |

---

- 字符串 `'8.1'` 本身长度已经是 3，比宽度 2 要大，所以 **不会被填充**，直接原样输出。
- 所以输出是：

```python
8.1
```


```python
teams = ['猛龙', '勇士', '雄鹿', '开拓者', '掘金', '76人']

for i in range(len(teams)):
    print("{:0>2} {}".format(i + 1, teams[i]))

```

    01 猛龙
    02 勇士
    03 雄鹿
    04 开拓者
    05 掘金
    06 76人
    

```python
print("{:0>2} {}".format(i + 1, teams[i]))
```

- 第一个 `{}` → 放的是“编号”，并格式化成两位（比如 01、02）
- 第二个 `{}` → 放的是“球队名称”，比如 勇士、猛龙

它们的位置 **一一对应 format() 里面的变量**：

### 2.3 验证用户输入的数据


```python
def inputbox(showstr, showorder, length):
    instr = input(showstr)

    if len(instr) != 0:  # 如果输入内容的长度不为0时

        # 模式1：检测输入的字符串是否为数字，并检测是否为0
        if showorder == 1:
            if instr.isdigit():  # 检测是否全为数字
                if instr == "0":  # 如果输入是0
                    print("\033[1;31;40m 输入为零，请重新输入！！\033[0m")
                    return "0"
                else:
                    return instr
            else:
                print("\033[1;31;40m输入非法，请重新输入！！\033[0m")
                return "0"

        # 模式2：检测输入的字符是否为字母，并检测字母是否是3个
        elif showorder == 2:
            if instr.isalpha():  # 检测是否全为字母
                if len(instr) != 3:  # 如果输入的不是3个字母
                    print("\033[1;31;40m必须输入三个字母，请重新输入！！\033[0m")
                    return "0"
                else:
                    return instr
            else:
                print("\033[1;31;40m输入非法，请重新输入！！\033[0m")
                return "0"

        # 模式3：检测输入是否为数字，并且长度等于目标数字
        elif showorder == 3:
            if instr.isdigit():  # 是否全为数字
                if len(instr) != length:  # 输入数字长度与目标不符
                    print("\033[1;31;40m必须输入" + str(length) + "个数字，请重新输入！！\033[0m")
                    return "0"
                else:
                    return instr
            else:
                print("\033[1;31;40m输入非法，请重新输入！！\033[0m")
                return "0"

    else:
        print("\033[1;31;40m输入为空，请重新输入！！\033[0m")
        return "0"

```


```python
inputbox('请输入姓名',2,3)
```

    请输入姓名 gtk
    




    'gtk'



### 2.4 随机姓名生成


```python
import random

# 姓氏库
surname = '赵,钱,孙,李,周,吴,郑,王,冯,陈,褚,卫,蒋,沈,韩,杨,朱,秦,尤,许'

# 第二位名字库
second = '中,万,斯,近,元,伟,丽,国,士,文,连,百,宏,可,立,成,海,友,南,广,云,基'

# 第三位名字库
third = '山,隆,智,瀚,顺,乐,天,杰,大,煜,兵,思,霖,瑶,棋,英,望,炫,翔,维,瑞,瑾,嘉,林,琪,勋,栋,源,路,焱,霖,彩,明,邦,闻,朔,皓,棠,寒,奕,寒,艺'

# 将名字库拆分为列表
surname_new = surname.split(',')
second_new = second.split(',')
third_new = third.split(',')

namelist = []  # 存放生成的名字

many = input('请输入需要生成姓名的数量：\n')

for i in range(int(many)):
    data = [2, 3]
    n = random.choice(data)  # 随机选择2或3字名
    if n == 2:
        name = random.choice(surname_new) + random.choice(second_new)
    else:
        name = random.choice(surname_new) + random.choice(second_new) + random.choice(third_new)
    namelist.append(name)

print('生成的虚拟姓名列表为：\n' + '\n'.join(namelist))
```

    请输入需要生成姓名的数量：
     5
    

    生成的虚拟姓名列表为：
    陈宏
    冯南山
    李宏源
    赵基煜
    许伟
    

### 2.5 加密


```python
import hashlib
import hmac
import random
import string

# 普通哈希加密函数（MD5 / SHA1 / SHA256）
def hash_encrypt(text):
    md5_result = hashlib.md5(text.encode()).hexdigest()
    sha1_result = hashlib.sha1(text.encode()).hexdigest()
    sha256_result = hashlib.sha256(text.encode()).hexdigest()

    print("✅ 原文:", text)
    print("MD5加密结果：", md5_result)
    print("SHA1加密结果：", sha1_result)
    print("SHA256加密结果：", sha256_result)

# 更安全的哈希加密函数（HMAC + 随机 key）
def hmac_md5_encrypt(text):
    # 随机生成一个8位 key（字母+数字）
    key = ''.join(random.choices(string.ascii_letters + string.digits, k=8)).encode()
    message = text.encode()
    
    hmac_result = hmac.new(key, message, digestmod='md5').hexdigest()

    print("🔐 使用的随机key为：", key.decode())
    print("更安全的HMAC-MD5加密结果：", hmac_result)

if __name__ == "__main__":
    text = input("请输入一段要加密的字符串：\n")

    print("\n===== 普通加密（hashlib） =====")
    hash_encrypt(text)

    print("\n===== 更安全的加密（HMAC + key） =====")
    hmac_md5_encrypt(text)

```

    请输入一段要加密的字符串：
     Nuist No.1
    

    
    ===== 普通加密（hashlib） =====
    ✅ 原文: Nuist No.1
    MD5加密结果： 808dc3f4d61ade292832bbb9da25acb9
    SHA1加密结果： eda32cff63c4fb2e3f40c503995b48d96522a50a
    SHA256加密结果： 4439430e5fa406ac172db9b60bb82531c9a6d21871d6c51b739330fb845919ce
    
    ===== 更安全的加密（HMAC + key） =====
    🔐 使用的随机key为： 6Ibpkm0j
    更安全的HMAC-MD5加密结果： bce8a08f5c75fc1f1863f4e1490138eb
    

| 部分代码                           | 含义 |
|------------------------------------|------|
| `text.encode()`                    | 把字符串变成字节格式（加密函数要求是字节，不是普通字符串） |
| `hashlib.md5(...)`                 | 创建一个 MD5 加密对象，用来处理字节数据 |
| `.hexdigest()`                     | 把加密后的结果转换成**可读的十六进制字符串** |
| `md5_result = ...`                 | 最后把结果存进变量 `md5_result` |


### 2.6 append is all you need!


```python
import datetime

# 方法一：+ 拼接
st1 = datetime.datetime.now()
s = ''
for i in range(0, 10000):
    s += str(i)
et1 = datetime.datetime.now()

# 方法二：append + join
st2 = datetime.datetime.now()
lst = []
for i in range(0, 10000):
    lst.append(str(i))
s = ''.join(lst)
et2 = datetime.datetime.now()

print("方法一（+ 拼接）耗时：", et1 - st1)
print("方法二（append + join 拼接）耗时：", et2 - st2)

```

    方法一（+ 拼接）耗时： 0:00:00.008281
    方法二（append + join 拼接）耗时： 0:00:00.002001
    

### 3.1 批量创建文本


```python
import os
import time
import random

# 获取用户输入的路径和要创建的数量
path = input("请输入文件保存地址（如 D:\\Test）：\n")
count = int(input("请输入要创建文件的数量：\n"))

# 判断路径是否存在，不存在则自动创建
if not os.path.exists(path):
    os.makedirs(path)

# 获取当前日期，如 20240324
today = time.strftime('%Y%m%d')

# 批量创建文件
for i in range(count):
    # 随机生成一个编号（100000~999999）
    number = random.randint(100000, 999999)
    
    # 构造完整文件名和路径
    filename = f"{today}_{number}.txt"
    full_path = os.path.join(path, filename)
    
    # 创建文件并写入一行内容
    with open(full_path, 'w') as f:
        f.write(f"这是第 {i+1} 个文件，创建于：{time.strftime('%Y-%m-%d %H:%M:%S')}")

print("创建成功！共生成", count, "个文件！")

```

    请输入文件保存地址（如 D:\Test）：
     D:\Cache
    请输入要创建文件的数量：
     1205
    

    创建成功！共生成 1205 个文件！
    

![image.png](43098fff-4f1b-4607-a0a3-38ec81b44993.png)

### 3.2 根据txt创建文件夹


```python
import os

# 步骤1：指定文本文件路径
file_path = "D://name.txt"

# 步骤2：读取文件内容，每一行就是一个文件夹名
with open(file_path, 'r', encoding='utf-8') as f:
    lines = f.readlines()

# 步骤3：为每一行创建对应的文件夹
for line in lines:
    folder_name = line.strip()  # 去掉换行符和多余空格
    if folder_name:  # 如果不为空
        try:
            os.mkdir(folder_name)
            print(f"✅ 成功创建文件夹：{folder_name}")
        except FileExistsError:
            print(f"⚠️ 文件夹已存在：{folder_name}")
        except Exception as e:
            print(f"❌ 创建失败：{folder_name}，原因：{e}")

```

    ✅ 成功创建文件夹：华为P30 Pro
    ✅ 成功创建文件夹：华为P30
    ✅ 成功创建文件夹：荣耀V20
    ✅ 成功创建文件夹：VIVO X27
    ✅ 成功创建文件夹：OPPO R17
    ✅ 成功创建文件夹：荣耀20
    ✅ 成功创建文件夹：小米9
    

![image.png](9ce15a16-4072-4183-bff7-e906c6b6fcb8.png)

### 3.3 读取txt文档并分词输出


```python
import jieba

# 用户输入文件路径
file_path = input("请输入要读取的文件路径（如 D:\\Test.txt）：\n")

# 打开文件并读取内容
try:
    with open(file_path, 'r', encoding='utf-8') as f:
        content = f.read()

    # 使用 jieba 分词
    word_list = list(jieba.cut(content))

    # 输出分词结果
    print("分词结果如下：")
    print(word_list)

except FileNotFoundError:
    print("文件未找到，请检查路径是否正确！")
except Exception as e:
    print("出现错误：", e)
```

### 3.4 文件名拓展名分离


```python
import os

# 输入文件路径
file_path = input("请输入要判断的文件名：\n")

# 拆分出扩展名
_, ext = os.path.splitext(file_path)

# 判断扩展名是否合法
if ext.lower() in ['.xls', '.xlsx', '.csv']:
    print("您选择的文件符合数据分析的文件格式…")
else:
    print("选择的文件不属于数据表格格式！")

```

### 3.5 分类整理文件夹


```python
import os
import shutil

# 获取用户输入的文件所在路径
src_dir = input("请输入要整理的文件所在目录路径：\n")

# 获取目录下所有文件名（不包括子目录）
files = os.listdir(src_dir)

for file in files:
    # 拼接完整路径
    full_path = os.path.join(src_dir, file)
    
    # 只处理文件（排除子目录）
    if os.path.isfile(full_path):
        # 提取分类名（如“日销量”、“月销量”、“年销量”）
        category = file.split('_')[0]
        
        # 构建目标分类目录路径
        target_dir = os.path.join(src_dir, category)
        
        # 如果不存在该分类目录，就创建
        if not os.path.exists(target_dir):
            os.makedirs(target_dir)
        
        # 构建目标路径（分类目录 + 文件名）
        target_path = os.path.join(target_dir, file)
        
        # 移动文件
        shutil.move(full_path, target_path)
        print(f"✅ 已移动文件 {file} 到 {category}/")
        
print("分类整理完成！")

```
