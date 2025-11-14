# BP 手写数字识别

简短说明：

这是我的人工智能基础的作业，做的很烂。模型没训练好，对MNIST数据集的识别度很高，但是对于我自己的手写用于测试的图片识别率有点低（以MNIST为数据集，MNIST是一个手写数字0-9的数据集，有60000个训练样本和10000个测试样本）

本项目基于一个简单的 BP（两层）神经网络实现对 MNIST 手写数字的识别，并提供 Jupyter Notebook（bp_digit0_9_recognition.ipynb / bp_0_9_recog.ipynb）用于训练、测试和通过 ipywidgets 交互式加载本地图片进行识别。

## 文件结构
- data/mnist/ — MNIST 二进制数据文件（train / t10k）
- digit/ — 准备用来识别的图片（目前包含 num3.npy）
- bp_digit0_9_recognition.ipynb — 主要 notebook（训练 + widgets 识别）
- bp_0_9_recog.ipynb — 备选实现（纯 Python 实现）
- README.md — 本文件

## 依赖（Windows）
在命令行或 Anaconda prompt 中运行：
pip install numpy matplotlib pillow ipywidgets

启用 widgets（如果使用 Jupyter Lab）：
jupyter nbextension enable --py widgetsnbextension --sys-prefix
（Jupyter Lab 可能需要 jupyterlab-widgets 扩展）

## 快速运行
1. 在 VS Code 或 Jupyter Notebook 中打开 `bp_digit0_9_recognition.ipynb`。  
2. 逐单元格运行（或运行整个 notebook）。训练部分可能较慢，建议先注释或缩小训练迭代用于调试。  
3. 训练完成后，Notebook 下方会显示一个输入框和“识别”按钮，输入图片路径或选择现有的 .npy/.png 文件，点击按钮查看识别结果。

## 效果展示
<img width="361" height="378" alt="效果展示" src="https://github.com/user-attachments/assets/3fe1c439-7dbc-4fee-bde4-f82addcbafa0" />
<img width="395" height="376" alt="联想截图_20251114233112" src="https://github.com/user-attachments/assets/b7e7776e-9ad9-4a63-b8c1-9e963da8bb31" />

(也是毫无悬念的把5识别成3了QAQ)

## 使用说明（widgets）
- 默认路径为 `.\digit\num0.png`（可在 notebook 中修改）。当前仓库下 `digit/` 含0-9的png图片 和一个`num3.npy`，也可以输入 `.\digit\num3.npy`。
- 若使用 PNG/JPG，程序会用 `png_to_mnist_array` 做预处理（居中、缩放到 28x28 并归一化）。

### 修改按钮颜色
在 notebook 中找到创建按钮的代码并修改 `button_style`：
````python
button = Button(
    description='识别',
    button_style='success',  # 'info' 'success' 'warning' 'danger' 或 ''
    tooltip='点击识别手写数字',
    icon='check'
)
