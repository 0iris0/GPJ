from collections import Counter
import pandas as pd
import random
import matplotlib.pyplot as plt
import csv
import datetime
file = open("raw homemade.csv", encoding="utf-8")
data = pd.read_csv(file)
# print(df)

# 畫案件數vs廠區&狀態pie
a = Counter(data["預計使用廠區"])
b = Counter(data["設備狀態"])
alabel = list(a)  # ['T2', 'T5', 'T3', 'T1']
blabel = list(b)  # ['驗收', '上線', '設計', '製造']
# print(blabel)
adata = dict(a)  # {'T2': 19, 'T5': 67, 'T3': 44, 'T1': 32}
bdata = dict(b)  # {'驗收': 39, '上線': 110, '設計': 7, '製造': 6}
ax = list(adata.values())  # [19, 67, 44, 32]
bx = list(bdata.values())  # [39, 110, 7, 6]


def fun(s, d):  # s百分比 d列表
    t = round(s/100*sum(d))  # 數值
    return f'{s:.1f}%,({t}件)'


plt.rc('font', family='Microsoft JhengHei')

plt.pie(ax, labels=alabel,
        autopct=lambda i: fun(i, ax),
        textprops={"weight": "bold", "size": 14},
        wedgeprops={"linewidth": 2, "edgecolor": "k"},
        labeldistance=1.2,
        explode=[0, 0.1, 0, 0])
plt.show()

plt.pie(bx, labels=blabel,
        autopct=lambda i: fun(i, bx),
        textprops={"weight": "bold", "size": 14},
        wedgeprops={"linewidth": 2, "edgecolor": "k"},
        labeldistance=1.2,
        explode=[0, 0.1, 0, 0])
plt.show()
