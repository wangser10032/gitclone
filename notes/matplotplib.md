### import matplotlib.pyplot as plt

`matplotlib.pyplot` 是 Matplotlib 库的一个子模块，用于绘制各种类型的图形，包括折线图、散点图、柱状图、饼图、热力图等。它提供了一组函数和工具，使得在 Python 中创建和自定义图形变得相对容易。下面是一些常见的 `plt` 函数以及它们的作用：

1. `plt.plot(x, y, label='label', color='color', linestyle='linestyle')`：用于绘制折线图。`x` 和 `y` 分别表示 x 轴和 y 轴上的数据，`label` 用于设置线条的标签，`color` 设置线条的颜色，`linestyle` 设置线条的样式。
2. `plt.scatter(x, y, c='color', marker='marker', label='label')`：用于绘制散点图。`x` 和 `y` 分别表示 x 轴和 y 轴上的数据，`c` 设置散点的颜色，`marker` 设置散点的标记形状，`label` 用于设置散点的标签。
3. `plt.bar(x, height, width=width, label='label')`：用于绘制柱状图。`x` 表示每个柱的位置，`height` 表示柱的高度，`width` 设置柱的宽度，`label` 设置柱状图的标签。
4. `plt.pie(sizes, labels=labels, autopct='%1.1f%%')`：用于绘制饼图。`sizes` 是每个扇形区域的大小，`labels` 是每个扇形区域的标签，`autopct` 用于设置百分比标签的格式。
5. `plt.imshow(data, cmap='cmap')`：用于绘制热力图。`data` 是要显示的数据矩阵，`cmap` 设置颜色映射。
6. `plt.title('title')`：设置图表的标题。
7. `plt.xlabel('xlabel')` 和 `plt.ylabel('ylabel')`：设置 x 轴和 y 轴的标签。
8. `plt.legend(loc='best')`：显示图例，`loc` 用于设置图例的位置。
9. `plt.show()`：显示绘制的图形。
10. `plt.savefig('filename.png')`：保存图形为文件，常用的文件格式包括 PNG、JPG、PDF 等。