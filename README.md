# LaTeX OCR 的数据仓库

本数据仓库是专为 [LaTeX_OCR](https://github.com/LinXueyuanStdio/LaTeX_OCR) 及 [LaTeX_OCR_PRO](https://github.com/LinXueyuanStdio/LaTeX_OCR) 制作的数据，来源于 `https://zenodo.org/record/56198#.V2p0KTXT6eA` 以及 `https://www.isical.ac.in/~crohme/` 以及我们自己构建。

数据已经同步到 huggingface，欢迎使用！https://huggingface.co/datasets/linxy/LaTeX_OCR

## 数据集

本仓库暂时有 4 个数据集

1. `small` 是小数据集，测试用
2. `full` 是印刷体约 100k 的完整数据集。实际上略小于 100k，因为用 LaTeX 的抽象语法树剔除了很多不能渲染的 LaTeX。
3. `fullhand` 是手写体 100k 的完整数据集。实际上略小于 100k，理由同上。
4. `hand` 是手写体较小数据集，更符合人类在电子屏上的手写体。主要来源于 `CROHME`。我们用 LaTeX 的抽象语法树校验过了。
5. `chinese` 是混有中文的数学公式数据集。基于上面的 `full` 数据集，通过对 LaTeX 的抽象语法树指定节点替换为中文而构建。

## 目录结构规范

每个数据集务必按以下结构来

```shell
small
├── formulas
│   ├── train.formulas.norm.txt 规范化后的公式，以空格为分隔符直接构造字典
│   ├── test.formulas.norm.txt
│   ├── val.formulas.norm.txt
│   └── vocab.txt 根据公式文件 XXX.formulas.norm.txt 构建的字典
├── images
│   ├── images_train 图片目录
│   ├── images_test
│   └── images_val
├── matching
│   ├── train.matching.txt 样式为 <image.png>, <formulas_id> 的匹配文件
│   ├── test.matching.txt
│   └── val.matching.txt
├── data.json
├── vocab.json
└── README.md
```

注意 `<image.png>=='0.png', <formulas_id>=='0' 对应 XXX.formulas.norm.txt 的行号，从 0 开始`