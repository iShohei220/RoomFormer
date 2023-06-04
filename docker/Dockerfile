FROM nvidia/cuda:11.1.1-devel-ubuntu18.04

RUN apt update && apt install -y wget git libgl1-mesa-dev libglib2.0-0
RUN wget https://repo.anaconda.com/archive/Anaconda3-2023.03-1-Linux-x86_64.sh
RUN bash Anaconda3-2023.03-1-Linux-x86_64.sh -b
RUN rm Anaconda3-2023.03-1-Linux-x86_64.sh
ENV PATH $PATH:/root/anaconda3/bin

RUN mkdir /workspace
WORKDIR /workspace
RUN git clone https://github.com/ywyue/RoomFormer.git
WORKDIR /workspace/RoomFormer

RUN conda create -n roomformer python=3.8
SHELL ["conda", "run", "-n", "roomformer", "/bin/bash", "-c"]
RUN pip install torch==1.9.0+cu111 torchvision==0.10.0+cu111 -f https://download.pytorch.org/whl/torch_stable.html && \
    pip install -r requirements.txt

RUN echo "source activate roomformer" >> ~/.bashrc
