# DBSACN_Example
python自写DBSCAN算法
## Requirements
- python3.x
- matplotlib
- numpy
## Usage
**Step 1.** Download this repository with git or click the [download ZIP ](https://github.com/guoswang/DBSACN_Example.git)button
```
$ git clone https://github.com/guoswang/DBSACN_Example.git
$ cd DBSACN_Example
```
**Step 2.** run DBSACN_Example.py
```
$ python DBSACN_Example.py
```
## 数据集
数据集是周志华《机器学习》中的西瓜数据集4.0
```
0.697,0.46
0.774,0.376
0.634,0.264
0.608,0.318
0.556,0.215
0.403,0.237
0.481,0.149
0.437,0.211
0.666,0.091
0.243,0.267
0.245,0.057
0.343,0.099
0.639,0.161
0.657,0.198
0.36,0.37
0.593,0.042
0.719,0.103
0.359,0.188
0.339,0.241
0.282,0.257
0.748,0.232
0.714,0.346
0.483,0.312
0.478,0.437
0.525,0.369
0.751,0.489
0.532,0.472
0.473,0.376
0.725,0.445
0.446,0.459

```
## 数据处理
```
def loadDataSet(filename):
    dataSet = []
    fr = open(filename)
    for line in fr.readlines():
        curLine = line.strip().split(',')
        fltLine = map(float, curLine)
        #python2.x map函数返回list
        #dataSet.append(fltLine)
        #python3.x map函数返回迭代器
        dataSet.append(list(fltLine))
    return dataSet
```
## 画图方法
```
def draw(C , dataSet):
    color = ['r', 'y', 'g', 'b', 'c', 'k', 'm']
    for i in C.keys():
        X = []
        Y = []
        datas = C[i]
        for j in range(len(datas)):
            X.append(dataSet[datas[j]][0])
            Y.append(dataSet[datas[j]][1])
        plt.scatter(X, Y, marker='o', color=color[i % len(color)], label=i)
    plt.legend(loc='upper right')
    plt.show()
```
## 主函数
```
def main():
    dataSet = loadDataSet("dataSet.txt")
    print(dataSet)
    C = DBSCAN(dataSet, 0.11, 5)
    draw(C, dataSet)

if __name__ == '__main__':
    main()

```
## 结果
![这里写图片描述](http://img.blog.csdn.net/20180304082030519)
