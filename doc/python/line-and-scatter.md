import plotly.graph_objs as go
import numpy as np

# 假设我们有一些模拟的心率监测数据
np.random.seed(1)  # 为了可重复性设置随机种子
time = np.arange(0, 3600, 60)  # 一个小时内每分钟记录一次
heart_rate = np.random.randint(50, 100, size=len(time))  # 心率在50到100之间随机

# 创建散点图
scatter = go.Scatter(
    x=time,
    y=heart_rate,
    mode='markers',  # 使用点来表示数据
    marker=dict(
        size=8,
        color=heart_rate,  # 使用心率值来决定点的颜色
        colorscale='Viridis',  # 颜色渐变
        showscale=True
    ),
    name='Heart Rate'
)

# 创建图表的布局
layout = go.Layout(
    title='Heart Rate Monitoring',
    xaxis=dict(title='Time (minutes)'),
    yaxis=dict(title='Heart Rate (bpm)'),
    height=400
)

# 创建图表对象
fig = go.Figure(data=[scatter], layout=layout)

# 显示图表
fig.show()
