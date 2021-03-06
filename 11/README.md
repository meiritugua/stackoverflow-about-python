| rank | ▲ | ✰ | vote | url |
|:-:|:-:|:-:|:-:|:-:|
|  11  |  867 | 379 | 1107 | [url](http://stackoverflow.com/questions/613183/sort-a-python-dictionary-by-value) |

***

## 用字典的值对字典进行排序

我有个字典,字典的值来自于数据库:一个是字符串,一个是数字.字符串是唯一的,所以键就是字符串.

我可以用键来排序,但是怎么用值来排序呢?

注:我已经看过另一个问题[怎样对列表中的字典的键值对字典进行排序?](http://stackoverflow.com/questions/72899/how-do-i-sort-a-list-of-dictionaries-by-values-of-the-dictionary-in-python),或许这种方法可以,但是我确实只需要一个字典,我想看看还有其他更好的方法.

***

对字典进行排序是不可能的,只有把字典转换成另一种方式才能排序.字典本身是无序的,但是像列表元组等其他类型是有序的.所以你需要用一个元组列表来表示排序的字典.

例子:

```python
import operator
x = {1: 2, 3: 4, 4:3, 2:1, 0:0}
sorted_x = sorted(x.items(), key=operator.itemgetter(1))
```

`sorted_x`是一个元组列表,用每个元组的第二个元素进行排序.`dict(sorted_x) == x`.

如果想要用键来进行排序:

```
import operator
x = {1: 2, 3: 4, 4:3, 2:1, 0:0}
sorted_x = sorted(x.items(), key=operator.itemgetter(0))
```

***

你也可以:

```
sorted(d.items(), key=lambda x: x[1])
```
