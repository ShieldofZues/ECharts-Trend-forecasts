<template>
  <div class="chart-container">
    <v-chart class="chart" :option="chartOption" autoresize />
  </div>
</template>

<script>
import { use } from 'echarts/core';
import { CanvasRenderer } from 'echarts/renderers';
import { LineChart } from 'echarts/charts';
import {
  GridComponent,
  TooltipComponent,
  LegendComponent,
  DataZoomComponent, // Added for potential zooming/panning
  TitleComponent // Added for title and subtitle
} from 'echarts/components';
import VChart, { THEME_KEY } from 'vue-echarts';
import * as echarts from 'echarts'; // Import echarts for formatting

// 注册 Echarts 所需的组件
use([
  CanvasRenderer,
  LineChart,
  GridComponent,
  TooltipComponent,
  LegendComponent,
  DataZoomComponent,
  TitleComponent
]);

export default {
  name: 'PerformanceChartEcharts',
  components: {
    VChart
  },
  // 提供主题（可选，这里使用默认主题）
  // provide: {
  //   [THEME_KEY]: 'dark'
  // },
  data() {
    // 您的原始数据和预测数据
    const rawData = [
            {
                "time": "2025/06/06 15:29:00",
                "value": "2027712800"
            },
            {
                "time": "2025/06/06 15:30:00",
                "value": "1976133200"
            },
            {
                "time": "2025/06/06 15:31:00",
                "value": "2015209600"
            },
            {
                "time": "2025/06/06 15:32:00",
                "value": "2148640800"
            },
            {
                "time": "2025/06/06 15:33:00",
                "value": "2208900900"
            },
            {
                "time": "2025/06/06 15:34:00",
                "value": "1981190400"
            },
            {
                "time": "2025/06/06 15:35:00",
                "value": "2063413600"
            },
            {
                "time": "2025/06/06 15:36:00",
                "value": "2038007800"
            },
            {
                "time": "2025/06/06 15:37:00",
                "value": "1969284600"
            },
            {
                "time": "2025/06/06 15:38:00",
                "value": "2008441000"
            },
            {
                "time": "2025/06/06 15:39:00",
                "value": "2007629200"
            },
            {
                "time": "2025/06/06 15:40:00",
                "value": "2206531300"
            },
            {
                "time": "2025/06/06 15:41:00",
                "value": "2072471000"
            },
            {
                "time": "2025/06/06 15:42:00",
                "value": "2093956500"
            },
            {
                "time": "2025/06/06 15:43:00",
                "value": "1942075000"
            },
            {
                "time": "2025/06/06 15:44:00",
                "value": "1939850600"
            },
            {
                "time": "2025/06/06 15:45:00",
                "value": "1913988900"
            },
            {
                "time": "2025/06/06 15:46:00",
                "value": "1899806200"
            },
            {
                "time": "2025/06/06 15:47:00",
                "value": "2014782700"
            },
            {
                "time": "2025/06/06 15:48:00",
                "value": "1922553700"
            },
            {
                "time": "2025/06/06 15:49:00",
                "value": "1942948100"
            },
            {
                "time": "2025/06/06 15:50:00",
                "value": "1875393900"
            },
            {
                "time": "2025/06/06 15:51:00",
                "value": "1880110800"
            },
            {
                "time": "2025/06/06 15:52:00",
                "value": "1869694200"
            },
            {
                "time": "2025/06/06 15:53:00",
                "value": "1854544100"
            },
            {
                "time": "2025/06/06 15:54:00",
                "value": "1981559600"
            },
            {
                "time": "2025/06/06 15:55:00",
                "value": "1933494700"
            },
            {
                "time": "2025/06/06 15:56:00",
                "value": "1813451800"
            },
            {
                "time": "2025/06/06 15:57:00",
                "value": "1790450300"
            },
            {
                "time": "2025/06/06 15:58:00",
                "value": "1787188600"
            },
            {
                "time": "2025/06/06 15:59:00",
                "value": "1782352400"
            },
            {
                "time": "2025/06/06 16:00:00",
                "value": "1825428600"
            },
            {
                "time": "2025/06/06 16:01:00",
                "value": "2054252300"
            },
            {
                "time": "2025/06/06 16:02:00",
                "value": "2322347000"
            },
            {
                "time": "2025/06/06 16:03:00",
                "value": "1946520600"
            },
            {
                "time": "2025/06/06 16:04:00",
                "value": "1844358000"
            },
            {
                "time": "2025/06/06 16:05:00",
                "value": "1917766400"
            },
            {
                "time": "2025/06/06 16:06:00",
                "value": "1971387000"
            },
            {
                "time": "2025/06/06 16:07:00",
                "value": "1963967700"
            },
            {
                "time": "2025/06/06 16:08:00",
                "value": "1885023400"
            },
            {
                "time": "2025/06/06 16:09:00",
                "value": "2219398400"
            },
            {
                "time": "2025/06/06 16:10:00",
                "value": "1903031600"
            },
            {
                "time": "2025/06/06 16:11:00",
                "value": "1845716200"
            },
            {
                "time": "2025/06/06 16:12:00",
                "value": "1886388900"
            },
            {
                "time": "2025/06/06 16:13:00",
                "value": "1830184200"
            },
            {
                "time": "2025/06/06 16:14:00",
                "value": "1922084500"
            },
            {
                "time": "2025/06/06 16:15:00",
                "value": "1926140400"
            },
            {
                "time": "2025/06/06 16:16:00",
                "value": "2339577000"
            },
            {
                "time": "2025/06/06 16:17:00",
                "value": "2121456500"
            },
            {
                "time": "2025/06/06 16:18:00",
                "value": "2028973400"
            },
            {
                "time": "2025/06/06 16:19:00",
                "value": "2030299000"
            },
            {
                "time": "2025/06/06 16:20:00",
                "value": "1969887000"
            },
            {
                "time": "2025/06/06 16:21:00",
                "value": "1900967200"
            },
            {
                "time": "2025/06/06 16:22:00",
                "value": "1858994000"
            },
            {
                "time": "2025/06/06 16:23:00",
                "value": "2171118000"
            },
            {
                "time": "2025/06/06 16:24:00",
                "value": "2133232400"
            },
            {
                "time": "2025/06/06 16:25:00",
                "value": "1843060900"
            },
            {
                "time": "2025/06/06 16:26:00",
                "value": "1812853000"
            },
            {
                "time": "2025/06/06 16:27:00",
                "value": "1830508000"
            },
            {
                "time": "2025/06/06 16:28:00",
                "value": "1902345900"
            },
            {
                "time": "2025/06/06 16:29:00",
                "value": "1858712300"
            },
            {
                "time": "2025/06/06 16:30:00",
                "value": "2080458200"
            }
        ];
    const trendData = [
            {
                "time": "2025/06/06 16:31",
                "value": "2041244800.0"
            },
            {
                "time": "2025/06/06 16:32",
                "value": "1995744500.0"
            },
            {
                "time": "2025/06/06 16:33",
                "value": "1985532800.0"
            },
            {
                "time": "2025/06/06 16:34",
                "value": "1971958900.0"
            },
            {
                "time": "2025/06/06 16:35",
                "value": "1975791000.0"
            }
        ];

    // 处理数据格式，转换为 Echarts 需要的 [时间戳, 数值] 格式
    const processedRawData = rawData.map(item => [new Date(item.time).getTime(), parseFloat(item.value)]);
    const processedTrendData = trendData.map(item => [new Date(item.time).getTime(), parseFloat(item.value)]);

    // 创建连接原始数据和预测数据的点
    const connectingData = [
        processedRawData[processedRawData.length - 1], // 原始数据的最后一个点
        processedTrendData[0] // 预测数据的第一个点
    ];

    // 定义 chartOption 在 data 函数的同一个作用域内，以便 formatter 可以访问 processedRawData
    const chartOption = {
        // 标题配置
        title: [{
            text: '性能指标趋势预测',
            left: 'center',
            textStyle: {
                fontWeight: 'bold',
                fontSize: 20
            }
        }, {
            // 使用第二个标题作为副标题/说明
            text: '实际接收速率为蓝色实线，预测接收速率为橙色虚线',
            left: 'center',
            top: 30, // 调整位置在主标题下方
            textStyle: {
                fontWeight: 'bold',
                fontSize: 14 // 副标题字体大小
            }
        }],
        // 提示框配置 (Tooltip)
        tooltip: {
          trigger: 'axis', // 坐标轴触发
          formatter: function (params) {
            let tooltipContent = '';
            // Use the processedRawData and processedTrendData from the closure scope
            // Get timestamps for the connection points (last raw data and first trend data)
            const lastRawTime = processedRawData[processedRawData.length - 1][0];
            const firstTrendTime = processedTrendData[0][0];

            // Sort params by data index to ensure correct time display first
            params.sort((a, b) => a.dataIndex - b.dataIndex);

            let timeDisplayed = false;

            params.forEach(item => {
              const timestamp = item.value[0];
              const seriesName = item.seriesName;
              const value = item.value[1]; // 数据值

              // Check if it's the "连接线" at a connection point
              const isConnectingLineAtConnection = (seriesName === '连接线' && (timestamp === lastRawTime || timestamp === firstTrendTime));

              // If it's NOT the connecting line at a connection point, include it
              if (!isConnectingLineAtConnection) {
                  let formattedValue;
                  if (value >= 1e9) {
                    formattedValue = (value / 1e9).toFixed(2) + ' Gbit/s';
                  } else if (value >= 1e6) {
                    formattedValue = (value / 1e6).toFixed(2) + ' Mbit/s';
                  } else {
                    formattedValue = value.toFixed(2) + ' bit/s';
                  }

                  // Display time only once at the beginning
                  if (!timeDisplayed) {
                      const date = new Date(timestamp);
                      const year = date.getFullYear();
                      const month = ('0' + (date.getMonth() + 1)).slice(-2);
                      const day = ('0' + date.getDate()).slice(-2);
                      const hours = ('0' + date.getHours()).slice(-2);
                      const minutes = ('0' + date.getMinutes()).slice(-2);
                      const time = `${year}-${month}-${day} ${hours}:${minutes}`;
                      tooltipContent = `<b>${time}</b><br/>`;
                      timeDisplayed = true;
                  }

                  tooltipContent += `${item.marker} ${seriesName}: ${formattedValue}<br/>`;
              }
            });

            return tooltipContent;
          }
        },
        // 图例配置 (Legend)
        legend: {
          bottom: '0', // 放置在底部
          left: 'center', // 居中
          data: ['实际接收速率', '预测接收速率'], // 图例项
          itemWidth: 40, // 图例符号宽度 (长方形)
          itemHeight: 4, // 图例符号高度 (线条粗细)
          // icon: 'rect', // 使用矩形作为图例符号
          // symbolKeepAspect: false, // 确保 icon 不保持宽高比
          textStyle: {
              fontWeight: 'bold',
              fontSize: 16,
              color: '#333' // 文字颜色
          }
        },
        // 网格区域配置 (Grid)
        grid: {
          left: '3%',
          right: '4%',
          bottom: '10%', // 调整底部空间给图例
          containLabel: true
        },
        // X轴配置
        xAxis: {
          type: 'time', // 时间轴
          axisLabel: {
            formatter: '{yyyy}-{MM}-{dd} {HH}:{mm}' // 标签显示格式
          },
          axisLine: { // 坐标轴线
              lineStyle: {
                  color: '#000',
                  width: 2,
                  type: 'solid' // 将横坐标轴线改为实线
              }
          },
          axisTick: { // 刻度线
              lineStyle: {
                  color: '#000',
                  width: 2,
                  type: 'solid' // 将横坐标刻度线改为实线
              },
              length: 8,
              alignWithLabel: true
          },
          splitLine: {
              show: false // 隐藏纵向网格线
          }
        },
        // Y轴配置
        yAxis: {
          type: 'value', // 数值轴
          axisLabel: {
            formatter: function (value) {
              if (value >= 1e9) {
                return (value / 1e9).toFixed(2) + ' Gbit/s';
              } else if (value >= 1e6) {
                return (value / 1e6).toFixed(2) + ' Mbit/s';
              } else {
                return value.toFixed(2) + ' bit/s';
              }
            }
          },
          axisLine: {
              lineStyle: {
                  color: '#000',
                  width: 2,
                  type: 'solid' // 实线
              }
          },
           axisTick: {
              lineStyle: {
                  color: '#000',
                  width: 2,
                  type: 'solid' // 实线
              },
               length: 8
          },
          splitLine: {
            show: true, // 显示横向网格线
            lineStyle: {
              type: 'dashed', // 虚线
              color: '#ccc' // 将网格线颜色改为浅灰色
            }
          }
        },
        // 数据系列配置 (Series)
        series: [
          {
            name: '实际接收速率',
            type: 'line',
            data: processedRawData,
            smooth: false,
            itemStyle: {
                color: '#007bff'
            },
            lineStyle: {
                 width: 3
            },
            areaStyle: {
              opacity: 0.8,
              color: {
                type: 'linear',
                x: 0,
                y: 0,
                x2: 0,
                y2: 1,
                colorStops: [{
                  offset: 0, color: 'rgba(0, 123, 255, 0.1)'
                }, {
                  offset: 1, color: 'rgba(0, 123, 255, 0)'
                }],
                global: false
              }
            },
            legendSymbol: 'rect',
            legendHoverLink: true
          },
          {
            name: '连接线', // 新增连接线系列
            type: 'line',
            data: connectingData,
            smooth: false,
            showSymbol: false, // 不显示连接线上的点
            itemStyle: {
                color: '#ffa500' // 连接线颜色与预测线一致
            },
             lineStyle: {
                 width: 3,
                 type: 'dashed' // 连接线型与预测线一致
            },
            areaStyle: {
               opacity: 0.8,
               color: {
                type: 'linear',
                x: 0,
                y: 0,
                x2: 0,
                y2: 1,
                colorStops: [{
                  offset: 0, color: 'rgba(255, 165, 0, 0.1)' // 橙色渐变起始颜色 (透明度0.1)
                }, {
                  offset: 1, color: 'rgba(255, 165, 0, 0)' // 橙色渐变结束颜色 (完全透明)
                }],
                global: false
              }
            }
          },
          {
            name: '预测接收速率',
            type: 'line',
            data: processedTrendData,
            smooth: false,
            itemStyle: {
                color: '#ffa500'
            },
             lineStyle: {
                 width: 3,
                 type: 'dashed' // 虚线
            },
            areaStyle: {
               opacity: 0.8,
               color: {
                type: 'linear',
                x: 0,
                y: 0,
                x2: 0,
                y2: 1,
                colorStops: [{
                  offset: 0, color: 'rgba(255, 165, 0, 0.1)'
                }, {
                  offset: 1, color: 'rgba(255, 165, 0, 0)'
                }],
                global: false
              }
            }
          }
        ]
    };

    return {
      chartOption // Return the constructed chartOption
    };
  }
};
</script>

<style scoped>
.chart-container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.chart {
  height: 400px; /* 您可以根据需要调整图表高度 */
}
</style> 