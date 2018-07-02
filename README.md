本项目针对中移在线的问题，通过客服与用户的对话，对用户意图进行预测。
程序包含两大部分：直接分类预测和二级分类预测。

下面对本项目中包含的文件进行介绍：
code文件夹下，包含classification和two_level_classification两个文件夹：classification是直接分类程序，two_level_classification是二级分类程序

classification文件夹包含四个主要程序：
data_process.py用于对原数据进行处理，得到分词和去停用词的对应文件。
model.py包含对文件的训练预测程序
statistics.py用于对预测结果的可视化
helper.py用于储存上述三个程序所需要的文件路径和参数

two_level_classification文件夹包含六个主要程序
model1.py用于训练一级模型，区分投诉（含抱怨），咨询（含查询）和办理。
model2.py用于训练二级模型，区分投诉（含抱怨），咨询（含查询）和办理的各种子情况，使用多进程同时训练三种模型。
test是对整个训练模型进行测试，包含model1，model21，model22，model23等四个模型和对应的tfidf值，流程如下：对于文本content先进行model1预测，如果分类结果为第二类，则再使用model22预测，得到最终的分类结果。
two_helper.py用于储存上述五个程序所需的文件路径和基本参数。

data文件文件夹下，包含八个文件夹
1文件夹储存的是各个情况下，客服的数据
2文件夹储存的是各个情况下，用户的数据
all文件夹储存的是各个情况下，客服和用户的数据
raw_data文件夹下储存的是原始文件
statistics文件夹储存的是各种统计结果
stopwords储存的是停止词
train_bunch和test_bunch储存的是训练过程中产生的bunch文件，用于储存对应的label，content和label，tfidf

model文件夹下储存的是训练产生的训练模型和tfidf模型。

各个程序中均有详细的注释，具体细节就不在这里一一展示了。


总结：通过调整数据的规模，选取了较为合适的文本长度，将F1提高了0.7%。最终F1值为45.4%
     构建二级分类最终得到的分类结果，要低于直接分类的结果。
     尝试过通过分析概率的去提高二级分类结果，但是概率区分并不明显。没有提高二级分类结果。
