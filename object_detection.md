#目标检测  
##R-CNN系列  
*R-CNN  
使用selective search方法生成2k个region proposals，将其warp到同样分辨率尺寸和长宽比，并将它们输入到CNN backbone中做特征提取，最终的tokens送入SVM和Bbox reg模块进行分类和bbox预测修正。  
问题：计算速度过慢，需要2k次CNN forward feed，同时selective search算法是fix的，无法自适应变化。
*Fast RCNN  
在selective search输出region proposals的基础上，不是直接将它们送入CNN，而是将整张图片送入CNN，在得到的feature map上裁切出相应的区域，得到对应的ROI feature vector。然后将其送入ROI Pooling模块，进行scale调整和spatial ratio调整，到统一分辨率，然后送入两个FC层，得到的结果分别使用softmax和bbox regressor处理后输出。  
*Faster-RCNN  
引入了region proposal network来在feature map上直接产生region，而不是在原图上使用SR方法产生，SR方法耗时且缺乏diversity

##YOLO系列  


