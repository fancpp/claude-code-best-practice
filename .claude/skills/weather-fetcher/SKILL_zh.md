---
name: weather-fetcher
description: 从 Open-Meteo API 获取阿联酋迪拜当前气温数据的指令
user-invocable: false
allowed-tools:
  - "WebFetch(*)"
---

# Weather Fetcher Skill（天气获取技能）

本技能提供获取当前天气数据的指令。

## 任务

以请求的单位（摄氏度或华氏度）获取阿联酋迪拜的当前气温。

## 指令

1. **获取天气数据**：使用 WebFetch 工具从 Open-Meteo API 获取迪拜的当前天气数据。

   对于**摄氏度**：
   - URL：`https://api.open-meteo.com/v1/forecast?latitude=25.2048&longitude=55.2708&current=temperature_2m&temperature_unit=celsius`

   对于**华氏度**：
   - URL：`https://api.open-meteo.com/v1/forecast?latitude=25.2048&longitude=55.2708&current=temperature_2m&temperature_unit=fahrenheit`

2. **提取温度**：从 JSON 响应中提取当前温度：
   - 字段：`current.temperature_2m`
   - 单位标签位于：`current_units.temperature_2m`

3. **返回结果**：清晰地返回温度值和单位。

## 预期输出

完成本技能指令后：
```
Current Dubai Temperature: [X]°[C/F]
Unit: [Celsius/Fahrenheit]
```

## 注意事项

- 仅获取温度，不执行任何转换或写入任何文件
- Open-Meteo 免费使用，无需 API 密钥，使用基于坐标的查询以确保可靠性
- 迪拜坐标：纬度 25.2048，经度 55.2708
- 清晰返回数值型温度值和单位
- 根据调用者的请求支持摄氏度和华氏度两种单位
