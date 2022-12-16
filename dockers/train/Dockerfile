# SageMaker PyTorch image
FROM 763104351884.dkr.ecr.ap-south-1.amazonaws.com/pytorch-training:1.12.1-gpu-py38-cu113-ubuntu20.04-sagemaker

WORKDIR /opt/ml
ENV PATH="/opt/ml/code:${PATH}"

# this environment variable is used by the SageMaker PyTorch container to determine our user code directory.
ENV SAGEMAKER_SUBMIT_DIRECTORY /opt/ml/code


# /opt/ml and all subdirectories are utilized by SageMaker, use the /code subdirectory to store your user code.
# COPY cifar10.py /opt/ml/code/cifar10.py
COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt && rm -rf /root/.cache/pip
COPY infer.py preprocess.py train.py ./code/

# Defines cifar10.py as script entrypoint 
ENV SAGEMAKER_PROGRAM train.py