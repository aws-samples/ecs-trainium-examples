FROM amazonlinux:2

RUN echo $'[neuron] \n\
name=Neuron YUM Repository \n\
baseurl=https://yum.repos.neuron.amazonaws.com \n\
enabled=1' > /etc/yum.repos.d/neuron.repo

RUN rpm --import https://yum.repos.neuron.amazonaws.com/GPG-PUB-KEY-AMAZON-AWS-NEURON.PUB

RUN yum install aws-neuronx-collectives-2.* -y
RUN yum install aws-neuronx-runtime-lib-2.* -y
RUN yum install aws-neuronx-tools-2.* -y
RUN yum install -y tar gzip pip
RUN yum install -y python3 python3-pip
RUN yum install -y python3.7-venv gcc-c++ 
RUN python3.7 -m venv aws_neuron_venv_pytorch 

# Activate Python venv 
ENV PATH="/aws_neuron_venv_pytorch/bin:$PATH"
RUN python -m pip install -U pip 
RUN python -m pip install wget 
RUN python -m pip install awscli 

RUN python -m pip config set global.extra-index-url https://pip.repos.neuron.amazonaws.com
RUN python -m pip install torchvision tqdm torch-neuronx neuronx-cc==2.* pillow
RUN mkdir -p /opt/ml/mnist_mlp
COPY model.py /opt/ml/mnist_mlp/model.py
COPY train.py /opt/ml/mnist_mlp/train.py
RUN chmod +x /opt/ml/mnist_mlp/train.py
CMD ["python3", "/opt/ml/mnist_mlp/train.py"]