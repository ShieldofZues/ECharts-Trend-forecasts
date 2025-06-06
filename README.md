# Performance Trend Chart

一个基于 Vue 3 和 ECharts 的性能趋势预测图表组件，用于展示和预测性能指标数据。
![截屏2025-06-06 17 47 10](https://github.com/user-attachments/assets/57b42d1b-2c28-4899-9991-f0ca10d9aafb)


## 功能特点

- 📊 使用 ECharts 5.0 实现高性能图表展示
- 🔮 支持实时数据展示和趋势预测
- 🎨 美观的 UI 设计，包含渐变效果
- 📱 响应式设计，支持自适应布局
- 🔍 支持数据缩放和提示框交互
- 📈 自动格式化数据单位（bit/s, Mbit/s, Gbit/s）

## 技术栈

- Vue 3
- ECharts 5.0
- Vue-ECharts 6.0

## 安装

1. 克隆项目
```bash
git clone https://github.com/ShieldofZues/ECharts-Trend-forecasts.git
cd ECharts-Trend-forecasts
```

2. 安装依赖
```bash
npm install
# 或
yarn install
```

3. 运行开发服务器
```bash
npm run serve
# 或
yarn serve
```

4. 构建生产版本
```bash
npm run build
# 或
yarn build
```

## 使用方法

1. 在 Vue 组件中引入：
```vue
import PerformanceChartEcharts from '@/components/PerformanceChartEcharts.vue'

export default {
  components: {
    PerformanceChartEcharts
  }
}
```

2. 在模板中使用：
```vue
<template>
  <PerformanceChartEcharts />
</template>
```

## 数据格式

组件接受两种数据格式：

1. 实际数据格式：
```javascript
{
  "time": "2025/06/06 15:29:00",
  "value": "2027712800"
}
```

2. 预测数据格式：
```javascript
{
  "time": "2025/06/06 16:31",
  "value": "2041244800.0"
}
```

## 图表特性

- 蓝色实线表示实际接收速率
- 橙色虚线表示预测接收速率
- 支持鼠标悬停查看详细数据
- 自动格式化数据单位
- 支持图表缩放和拖动
- 包含图例说明

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT License 
