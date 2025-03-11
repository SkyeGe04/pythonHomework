### question 1 使用列表推导式输出特殊字符


```python
list = [chr(i) for i in 
        [0x25B3, 0x25BD, 0x20AC, 0xFFE0, 0xFFE1, 0x00A4, 0xFFE1, 0x25A0]]
print(list)
```

    ['△', '▽', '€', '￠', '￡', '¤', '￡', '■']
    

### question 2 电信营业厅周业务分析


```python
import math

days = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
guest = [1821, 752, 951, 1521, 2562, 3522, 4317]

print ('电信营业厅周业务分析\n（客流量每个箭头表示500人，每千人安排一个员工)\n')

print("电信业务一周高峰客流提示牌")
for i in range(len(days)):
    upArrowGuest = math.ceil(guest[i]/500)
    print(f"{days[i]}: " + chr(8593) * upArrowGuest)

print("\n电信业务一周工作人员提示牌")
for i in range(len(days)):
    upArrowStaff = math.ceil(guest[i]/1000)
    print(f"{days[i]}: " + chr(8593) * upArrowStaff)
```

### question 3 循环数据输出

\r 回车符， 每次刷新光标移动到开头，不会换行

scroll_text[i:] + scroll_text[:i]：实现 循环滚动效果：
scroll_text[i:]：从索引 i 到 字符串末尾 的部分。
scroll_text[:i]：从索引 0 到 i 之前 的部分。
组合在一起就形成向左滚动的效果。

sys.stdout.flush()
作用：立即刷新标准输出 (sys.stdout)，确保 sys.stdout.write(...) 的内容立刻显示在终端上，而不是等到缓冲区填满后才显示。


```python
import time
import sys

scroll_text = "VISTANTES   "
print("南京信息工程大学校外访客：")

try:
    for i in range (len(scroll_text)):
        sys.stdout.write("\r" + scroll_text[i:] + scroll_text[:i])
        sys.stdout.flush()  #
        time.sleep(0.3)  # 暂停0.3s

except KeyboardInterrupt:
    print("\n程序已退出")
```

    南京信息工程大学校外访客：
     VISTANTES  

### question 4 违禁词检测


```python
word = input("请输入或者拷贝含有敏感词的宣传文字：\n")
sensitive = ["第一", "国家级", "高级", "最佳", "独一无二", "一流", "仅此一次", "顶级", "顶尖", 
             "尖端", "极品", "极佳", "绝佳", "绝对", "终极", "极致", "首个", "首选", "独家", 
             "首次", "首发", "首款", "金牌", "名牌", "王牌", "领袖", "领先", "领导", "缔造者", 
             "巨星", "掌门人", "至尊", "巅峰", "奢侈", "资深", "之王", "王者", "冠军"]

sensitive_find = []
sensitives_times = 0

for item in sensitive:
    if item in word:
        sensitive_find.append(item)
        # word = word.replace(item, '**'+item+'**')
        word = word.replace(item, '*' + item + '*') 

print("\nsensitive words found:")
for item in sensitive_find:
    print(item)
    sensitives_times += 1
print("detect", sensitives_times, "words:")

print("\ncheck here:\n", word)
```

    请输入或者拷贝含有敏感词的宣传文字：
     南信大是世界第一的大学，是国家级的大学，是独一无二的
    

    
    sensitive words found:
    第一
    国家级
    独一无二
    detect 3 words:
    
    check here:
     南信大是世界*第一*的大学，是*国家级*的大学，是*独一无二*的
    

### question 5 lambda


```python
list_dict = [
    {"name": "无语", "python": 99, "c": 89},
    {"name": "wgh", "python": 100, "c": 80},
    {"name": "琦琦", "python": 95, "c": 97},
    {"name": "明日", "python": 91, "c": 96}
]

num = "1314521"

sorted_list = sorted(list_dict, key=lambda x: x["python"])
print(sorted_list)

max_num = max(num, key=lambda x:int(x))
print("字符串中的最大数字是:", max_num)

```

    [{'name': '明日', 'python': 91, 'c': 96}, {'name': '琦琦', 'python': 95, 'c': 97}, {'name': '无语', 'python': 99, 'c': 89}, {'name': 'wgh', 'python': 100, 'c': 80}]
    字符串中的最大数字是: 5
    
