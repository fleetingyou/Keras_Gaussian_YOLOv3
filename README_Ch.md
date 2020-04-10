
# 训练VOC格式的自己数据集：
	1、python setup.py build
	2、python setup.py install
	3、在voc2007中Annotations存在自己的xml标签，在JPEGImages放入图片
	4、执行label.py生成ImageSets目录文件下Main里面生成四个个文件用于生成训练数据文件路径
	5、在generators文件夹下面pascal里面修改v oc_classes= {'xx1',0 ,'xx2',1}类型
	5、使用我修改后的voc_annotation.py生成训练数据集
	6、使用kmeans脚本生成新的voc_anchors_416
	
# 下载yolov3_weights.h5权重文件：
	将文件放入checkpoints

# 执行命令开始训练：
	python3 train.py  --gpu 0 --batch-size 64 --random-transform --compute-val-loss pascal voc2007

# 如果出现ImportError: No module named‘.utils.compute_overlap'报错：
	执行该命令 python setup.py build_ext --inplace
	
# 存在如下问题需要解决：
	1、CPU的利用率是修改过显卡ID但是跑起来batchszie调节发现利用率始终2%左右，原作者没法联系，工作原因我时间不够没法修改。（个人认为多显卡和单显卡调用使用代码存在问题）
	2、算法我没写acc和loss可视化分析，没有进行测试希望大家可以按照原作者的进行测试

# 原作者相关工作：
	https://gitee.com/ijijjjjjj/keras-GaussianYOLOv3
	https://github.com/xuannianz/keras-GaussianYOLOv3
