# Distributed Arcface Training in Pytorch

容器选择为tomzhai_pytorch_gpu/python

insightface在dgx上的路径为

/data/tomzhai/face_feature/insightface

进入/data/tomzhai/face_feature/insightface/recognition/arcface_torch文件夹

```
mkdir weights
mkdir onnx
```

weights文件只需要下载backbone即可

修改torch2onnx.py，注释掉如下代码块

```
# graph.input[0].type.tensor_type.shape.dim[0].dim_param = 'None'

convert_onnx(backbone_onnx, input_file, output_file, opset=9, simplify=args.simplify)
```

运行

```
python torch2onnx.py ./weights/glint360k_cosface_r50_fp16_0.1/backbone.pth --output ./onnx/glint360k_cosface_r50_fp16_0.1

python torch2onnx.py ./weights/glint360k_cosface_r100_fp16_0.1/backbone.pth --output ./onnx/glint360k_cosface_r100_fp16_0.1

python torch2onnx.py ./weights/glint360k_cosface_r18_fp16_0.1/back
bone.pth --output ./onnx/glint360k_cosface_r18_fp16_0.1

python torch2onnx.py ./weights/glint360k_cosface_r34_fp16_0.1/backbone.pth --output ./onnx/glint360k_cosface_r34_fp16_0.1
```

