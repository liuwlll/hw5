# 实验名称

多模态情感分类模型

## 概述

本实验旨在构建一个多模态情感分类模型，将图像和文本数据结合起来进行情感分类任务。通过将图像和文本的特征融合在一起试图获得更全面、准确的情感分类结果。


## 项目结构

主要的文件和文件夹结构如下所示：

```python
|-- dataset
    |-- train.txt
    |-- test_without_label.txt
    |-- data
        |-- guid.txt
        |-- guid.jpg
|-- best_model.pt
|-- README.md
|-- requirements.txt
|-- main.ipynb
|-- predict.txt
```

本实验使用了一个包含图像和文本数据的多模态数据集。数据集中的每个样本都包含一张图像和相应的文本描述，以及情感标签。数据集被分为训练集、验证集和测试集。其中，`dataset`文件夹存储了训练集和测试集的数据文件，`best_model.pt`保存了训练过程中的最佳模型参数，`README.md`为项目说明文件，`requirements.txt`列出了项目所需的依赖库，`main.ipynb`是代码的文件。

## 模型架构

本实验构建了一个多模态融合模型，该模型包括以下组件：

- 图像特征提取器：本实验使用预训练的VGG16模型作为图像特征提取器。通过VGG16的特征提取层和自适应平均池化层，本实验可以将图像转换为固定大小的特征向量。

- 文本特征提取器：本实验使用嵌入层和LSTM层作为文本特征提取器。通过嵌入层将文本数据转换为嵌入向量表示，并通过LSTM层对文本序列进行建模，获取最后一个时间步的隐藏状态作为文本特征。

- 多模态特征融合和分类器：本实验将图像特征和文本特征在特征维度上进行拼接，并通过全连接层进行分类预测。最终的输出是情感标签的概率分布。

## 环境设置

安装Jupyter Notebook以运行IPython Notebook文件。安装所需的Python库和依赖项。该代码基于Python 3，并使用了以下依赖库：

- pandas：用于数据处理和读取CSV文件。
- numpy：用于数值计算。
- cv2：OpenCV库，用于图像处理。
- torch：PyTorch库，用于构建和训练深度学习模型。
- torchvision.transforms：PyTorch中的图像变换函数。
- PIL：Python Imaging Library，用于图像处理。
- tensorflow.keras.preprocessing.text：Keras中的文本预处理模块。
- torch.optim：PyTorch中的优化器。
- torchvision.models：PyTorch中的预训练模型。
- torch.nn.functional：PyTorch中的函数接口。

可以通过以下命令安装所需依赖：

```python
pip install -r requirements.txt
```

## 实验步骤

1. 数据预处理：首先，对图像数据进行预处理，包括图像的缩放、归一化等操作。对文本数据进行分词和编码处理，生成词汇表。

2. 构建模型：根据上述模型架构，构建多模态融合模型，包括图像特征提取器、文本特征提取器和特征融合分类器。

3. 模型训练：打开train.ipynb文件并根据需要调整超参数，运行单元格以开始模型训练。定义损失函数和优化器，将模型迁移到GPU设备（如果可用），使用训练集数据进行模型训练，根据验证集的性能调整模型参数。

4. 模型评估：使用测试集数据对训练好的模型进行评估，计算模型在测试集上的损失和准确率。

5. 模型预测：逐个运行单元格以进行模型预测。预测结果将写入predict.txt文件中。

6. 消融实验：逐个运行单元格以进行消融实验，尝试将单模态模型（只使用图像或文本数据）作为对比实验，评估不同模态特征对情感分类任务的影响。



## 使用说明

1. 环境配置：确保你的环境中安装了所需的Python库和依赖项。

2. 数据准备：将图像数据、文本数据和情感标签组织成相应的训练集、验证集和测试集，并进行预处理操作，如图像缩放、文本分词等。

3. 模型训练：训练过程中，模型会自动保存在每个epoch中验证集上性能最好的模型参数。

4. 模型评估：获取模型在测试集上的性能指标。

5. 消融实验：运行消融实验脚本，指定单模态模型和多模态模型的设置，比较它们在验证集上的性能差异。
