###############################
# Dockerfile build ruby
# in tensorflow/tensorflow:latest-gpu-py3-jupyter
#docker run --name 100D --rm -v /windows/workspace/100Day-ML-Marathon:/tf -p 80:8888 --runtime=nvidia tensorflow/tensorflow:latest-gpu-py3-jupyter
###############################

# Base image to tensorflow/tensorflow:latest-gpu-py3-jupyter
FROM tensorflow/tensorflow:latest-gpu-py3-jupyter

COPY requirements.txt /tf/

RUN pip install --upgrade pip \
 && pip install -r requirements.txt

CMD jupyter notebook --ip=$(hostname -i) --allow-root
