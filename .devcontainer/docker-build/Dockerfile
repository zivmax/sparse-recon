# Use an official Miniconda runtime as a parent image
FROM pytorch/pytorch:2.2.1-cuda12.1-cudnn8-devel

# Set the working directory in the container
WORKDIR /workspace

ENV TZ=Asia/Shanghai
ENV DEBIAN_FRONTEND=noninteractive

RUN sed -i -e 's|http://archive.ubuntu.com/ubuntu|https://mirrors.shanghaitech.edu.cn/ubuntu|g'  \
	-i -e 's|http://security.ubuntu.com/ubuntu|https://mirrors.shanghaitech.edu.cn/ubuntu|g' \
	/etc/apt/sources.list

RUN apt update
RUN apt upgrade -y --fix-missing
RUN apt install -y curl 
RUN apt install -y wget 
RUN apt install -y systemd 
RUN apt install -y git 
RUN apt install -y p7zip-full

# Clean up to reduce image size
RUN apt clean && \
    rm -rf /var/lib/apt/lists/*

# Install any needed packages specified in requirements.txt
RUN pip config set global.index-url https://mirrors.shanghaitech.edu.cn/pypi/web/simple
RUN ["python3", "-m", "pip", "install", "--upgrade", "pip"]
COPY requirements.txt ./
COPY requirements-dev.txt ./
RUN pip install --no-cache-dir -r requirements.txt
RUN pip install --no-cache-dir -r requirements-dev.txt
RUN rm ./requirements.txt
RUN rm ./requirements-dev.txt


# Make port 80 available to the world outside this container
EXPOSE 80

