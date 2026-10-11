# 沈丹高铁实际列车数据集

本项目提供沈丹高铁（沈阳北 ↔ 丹东）的列车运行数据集，包含完整上下行车次时刻表与线路车站基础信息，全部采用JSON格式。


### 数据文件
- `trains.json`：全部车次信息，车次号、运行方向、途经站点、到达/发车时间、里程
- `stations.json`：线路所有车站，以沈阳北为起点的基准里程

### 主要字段说明
**trains.json**
- `trainNo`：车次编号 D/G/C
- `direction`：`down`下行(沈阳→丹东) / `up`上行(丹东→沈阳)
- `path`：该车次途经站点数组，包含 station车站名、km里程、arr到达时间、dep发车时间

**stations.json**
- `name`：车站名称
- `km`：线路基准里程

### 快速使用示例
```python
import json

with open("trains.json", "r", encoding="utf-8") as f:
    trains = json.load(f)

# 获取所有下行车次
down_list = [t for t in trains if t["direction"] == "down"]
print(f"下行车次共 {len(down_list)} 班")
