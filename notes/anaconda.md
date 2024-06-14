conda create -n 虚拟环境名字 python=版本 （-c 镜像地址）创建虚拟环境

conda remove -n 虚拟环境名称 --all 移除虚拟环境

conda activate pytorch 激活虚拟环境

conda deactivate 退出当前虚拟环境

conda list 查看当前有哪些包

conda install pytorch torchvision torchaudio pytorch-cuda=11.7 -c pytorch -c nvidia

conda info --envs

conda install 

conda config --add channels 通道地址 添加和删除镜像通道地址

conda config --remove channels 通道地址

-i https://pypi.tuna.tsinghua.edu.cn/simple

conda config --show

conda install xxx -c 镜像地址

清华镜像 https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main

阿里巴巴镜像 http://mirrors.aliyun.com/anaconda/pkgs/main

conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c http://mirrors.aliyun.com/anaconda/cloud/pytorch/win-64/ -c nvidia



```
conda install pytorch==1.7.1 torchvision==0.8.2 torchaudio==0.7.2 cudatoolkit=11.0 -c pytorch
```

算力，cuda driver version cuda runtime version

CUDA Driver版本应该大于 CUDA Runtime

算力 4060 8.9

nvidia-smi 查看当前CUDA支持版本

NVIDIA-SMI 528.92       Driver Version: 528.92       CUDA Version:	 12.0



sklearn