
## numpy
```python=
import numpy as np

# 1.基本創建與存取
# 建立一個ndarray物件 create a array
a = np.array([[[1, 2], [3, 4], [5, 6], [7, 8]]], dtype="int32")
# array == matrix建立時必須為矩形
# 可以自己指定資料型態像:float32
a = np.array(a, dtype="int32")  # 透過constructor 改類型
"""
參數:
dtype: 指定型態，只能在創建時使用
ndim: array 維度    shape: array 形狀
size: array裡有多少元素    itemsize: array裡每個元素的大小(byte)
nbytes(size*itemsize): array總共多少bytes
"""
print(a.ndim, a.shape, a.dtype, a.size, a.itemsize, a.nbytes)

a = np.array([[1, 2, 3, 4, 5, 6, 7], [8, 9, 10, 11, 12, 13, 14]])
a[:, 2:4] = [[77, 79], [22, 55]]
# arr[stinx: endinx: stepsize]
b = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
print(a, b[[3, 4, 5]], sep="\n\n")
# index裡可以放list來隨機一次存取多個值，slicing也可以存取多個值，但只能固定step
a = np.array([
    [[[1, 2], [3, 4]], [[5, 6], [7, 8]]], [
        [[9, 10], [11, 12]], [[13, 14], [15, 16]]]
])
# 使用...代表全都要
print(a[0, ..., 0], "\n=====")  # 指定前後維度的index0，中間維度全選
## becareful when copy array
b = a #copy reference!!!
b = a.copy() #or use constructor

# 2.利用內建函式快速創建array()
"""
np.empty(shape, dtype)              # 建立資料未指定的矩陣
np.zeros(shape, dtype)              # 建立資料都是零的矩陣
np.ones(shape, dtype)               # 建立資料都是一的矩陣
np.full(shape, value, dtype)        # 建立資料都是value的矩陣
np.arange(lenth, dtype)             # 建立連續資料的一維矩陣
np.full_like(array, value, dtype)   # 根據傳入的array建立同類型的矩陣
"""
all = [np.empty((2, 2)), np.zeros((3, 3), dtype="int32"),
       np.ones((2, 2, 2)), np.full((3, 2), 99), np.arange(50)]
for i in all:
    print(i, end="\n\n")
print(np.full_like(all[1], 33, dtype="int32"))

# 3.array 計算
a = np.array([3, 4, 1])
b = np.array([-2, 5, -8])
# 逐一元素運算
# 逐元運算shape(矩陣大小)要一樣
""""
a + b   a - b   a * b   a / b  a**b    a//b
a > b   a == b  a <= b
np.sin(ndarray), np.cos(ndarray)
"""
print(a+2, a-2, a*2, a//2, a+b, a*b, a > b, sep="\n")
### sin, cos
print(np.sin(a), np.cos(a), sep="\n")

a = [
    [1, 13, 21, 11, 196, 75, 4, 3, 34, 6, 7, 8, 0, 1, 2, 3, 4, 5],
    [3, 42, 12, 33, 766, 75, 4, 55, 6, 4, 3, 4, 5, 6, 7, 0, 11, 12],
    [1, 22, 33, 11, 999, 11, 2, 1, 78, 0, 1, 2, 9, 8, 7, 1, 76, 88]
]
"""
astype(str:type)
np.any(ndarray().bool.cal, axis)    np.all(ndarray().bool.cal, axis)
    ndarray().bool.cal: ndarray 的bool計算-> 整個都是bool型態
    any:只要有任何一個是True就輸出True
    all:全部都必須是True才輸出True
bool.cal:
    ~:not   &:and
    (~(a > 50) & (a < 100)) and need parenthese or -> 50 & a
"""
a = np.array(a)
a = a.astype("int32")  # type casting
print(a, a > 50, a[a > 50], np.any(a > 50, axis=0), np.all(a > 50), sep="\n")
print((~(a > 50) & (a < 100)))

# 矩陣計算
a = np.array(
    [2, 1]
)  # 1x2
b = np.array([
    [3, 2, 0],
    [3, 1, -1]
])  # 2x3
"""
a.dot(b) == a@b == np.matmul(a,b)   矩陣內積
np.outer(a, b)                      矩陣外積
np.cross(a, b)                      向量外積
np.identity(len)                    創造邊長為len的單位矩陣 
np.linalg.det(ndarray)              計算determinant
"""
print(a@b, np.outer(a, b), np.cross(a, b), sep="\n\n")
# 矩陣內積  a的column == b的row 才能進行運算
# 矩陣外積  輸出a每個元素對b每個row的值(array)
# 向量外積  長度相同可外積，若長度不足則往右補0，像a補0後變[2,1,0]
a = np.array([
    [2, 9, 4],
    [8, 6, 7],
    [5, 3, 0]
])
print(np.identity(5), np.linalg.det(a), sep="\n")

# 統計運算
"""
a.sum(axis) #全部加總
a.sum(axis=0) #加總column 第一個維度
a.sum(axis=1) #加總row    第二個維度
a.min(axis) a.max#全部最小值
a.cumsum(axis) #逐值累加    a.mean(axis) #平均數    a.std(axis) #標準差
"""
print(a.sum(), a.min(axis=0), a.cumsum(), a.mean(axis=1), a.std(), sep="\n")

# 4. array型態變換 array organization
a = np.array([1, 2, 3, 4])
b = np.array([5, 6, 7, 8])
a = np.vstack((a, b))  # Vertically stack: column量要相同
a = np.ones((2, 4))
b = np.zeros((2, 2))
b = np.hstack([a, b])  # Horizontal stack row量要相同
print(a, b, sep="\n")
# T屬性 reshape ravel
"""
T :轉置
reshape: 改變shape，資料量與之前相同 可配合arrange使用
ravel: 將dim改為1 
vstack(iterable:array) hstack(iterable:array) 
"""
a = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
print(b, "\n")
print(a.T, a.reshape((2, 2, 2)), a.ravel(), sep="\n")

data = np.array([
    [2, 4, 6, 8, 10, 12],
    [1, 3, 5, 7, 9, 11]
])#2x6
print(np.vsplit(data, 2), np.hsplit(data, 2), sep="\n")
# np.vsplit(dnarray, spilt)根據第一維度(row:2/2)進行分割(垂直分割)
# np.hsplit(dnarray, spilt)根據第二維度(col:6/2)進行分割(水平分割)
# 第二個參數為分割次數只要相除後是整數就能分割

# 5.load data from file
"""
filedata = np.genfromtxt("data.txt", delimiter=",")
#delimiter = sep
"""

# 6.random
"""
size: int,int  - like shape but not tuple
np.randon.rand(size)                        隨機生成0~1小數
np.random.random_sample(shape)              隨機生成0~1小數
np.random.randint(start, end, size=shape)   隨機生成start~end-1整數
np.repeat(ndarray, rep_times, axis)         重複生成元素rep_times次數
"""
a = np.random.rand(4, 2)  # 放入 size 會隨機生成0~1 小數
b = np.random.random_sample(a.shape)
c = np.random.randint(4, 7, size=(3, 3))
print(a, b, c, sep="\n")
a = np.repeat(np.array([1, 2, 3]), 3)  # 將array裡的元素repeat
b = np.repeat(np.array([[1, 2, 3]]), 3, axis=0)  # 將array裡第0維度的元素repeat
print(a, b, sep="\n")
```