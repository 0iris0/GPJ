import openpyxl
from collections import Counter
import pandas as pd
import random
import matplotlib.pyplot as plt
import csv
import datetime
import statistics
import numpy as np
file = open("raw homemade.csv", encoding="utf-8")
data = pd.read_csv(file)
# print(df)
data["安全評估日期"] = pd.to_datetime(data["安全評估日期"])
# 17
data["逾期天數"] = (pd.Timestamp.now().normalize() - data["安全評估日期"]).dt.days
# 18
data["幾天結案"] = ((pd.to_datetime(data["安全評估日期"]) -
                pd.to_datetime(data["建立時間"])).dt.days+1)

# over6m計算
ddata = data.fillna(0)
ddata = ddata[(ddata["幾天結案"] > 0)]
ddata = ddata[(ddata["HS結案確認"] == True)] # 94筆資料
# 共用
a = Counter(ddata["預計使用廠區"])
b = Counter(ddata["設備狀態"])
ax = list(a)  # ['T2', 'T5', 'T3', 'T1']
bx = list(b)  # ['驗收', '上線', '設計', '製造']

# 廠區vs結案天數
with open("ax.csv", mode="w", newline="") as file:
    writer = csv.writer(file)
    for site in ax:
        ah = ddata[ddata["預計使用廠區"] == site]
        ahh = round(statistics.mean(ah["幾天結案"]), 2)  # 結案平均天數
        al = [site, ahh]
        writer.writerow(al)
with open("ax.csv", mode="r", newline="") as file:
    reader = csv.reader(file)
    data = pd.DataFrame(reader)
    aa = data[1].astype(float)  # ['68.35', '39.46', '72.53', '28.22']
    # print(list(aa))  # [68.35, 39.46, 72.53, 28.22]
plt.rc('font', family='Microsoft JhengHei')
plt.bar(ax, list(aa), color=["b", "m", "c", "g"], edgecolor="k")
plt.show()

# 狀態vs結案天數
with open("bx.csv", mode="w", newline="") as file:
    writer = csv.writer(file)
    for status in bx:
        bh = ddata[ddata["設備狀態"] == status]
        bhh = round(statistics.mean(bh["幾天結案"]), 2)  # 結案平均天數
        bl = [status, bhh]
        writer.writerow(bl)
with open("bx.csv", mode="r", newline="") as file:
    reader = csv.reader(file)
    data = pd.DataFrame(reader)
    bb = data[1].astype(float)
    # print(list(bb))
plt.rc('font', family='Microsoft JhengHei')
plt.bar(bx, list(bb), color=["orange", "brown",
        "pink", "gray"], edgecolor="k")
plt.show()
