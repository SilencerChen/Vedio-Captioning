# Vedio-Captioning

Vedio-Captioning当前主要的方式：
  1 encoder部分使用CNN，attention模型
  2 encoder部分使用LSTM
  
encoder后得到包含所有视频信息的向量，LSTM输入只需要h和x
x为单词（向量表示），h根据上一时刻的h求得（h0来自视频信息的向量）
对h使用softmax（with cross entropy）得到当前单词
  PS：相当于将词典内每个单词当作一个label的分类任务
训练时，提供视频和GT语句，根据高频词汇保存词典（几千到一万）
视频提供给encoder，GT的每个词汇提供给相应时刻的decodeer
  
当encoder部分使用LSTM时：
  encoder部分每个LSTM的output作为当前decoder部分LSTM的visual feature
  decoder部分每个LSTM的output作为当前选词的依据
  
改进点：
  encoder部分使用LSTM无法解释，可以改进
  decoder部分softmax中的loss和实际语言模型关系不密切，可以改进
