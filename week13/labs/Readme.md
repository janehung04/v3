## Week 13 labs - everything accelerated!

### Triton Inference Server primer
Triton Inference server is designed to help you create services out of your trained models.  In this lab, we will follow the [Triton IS QuickStart](https://github.com/triton-inference-server/server/blob/main/docs/quickstart.md). A few quick notes:
* First, provision a g4dn.2xlarge virtual machine in AWS. Use the Nvidia Deep Learning AMI.
* Go to your home diretory and clone the Triton IS server repo, e.g. ```https://github.com/triton-inference-server/server.git```
* The current tag is 21.11, so the pull commands are:
```
docker pull nvcr.io/nvidia/tritonserver:21.11-py3-sdk (client)
docker pull nvcr.io/nvidia/tritonserver:21.11-py3 (server)
```
A few quick questions:
* is your server using the GPU?  
  *  Yes
* Can you change the number of classes for scoring in the example?
  *  Yes
* Which model is being used for inference? Can you change it to a different model?
  *  densenet_onnx
* Can you get the metrics for your server?
  *  Yes

### RAPIDS primer
RAPIDS is an open source project that targets to bring GPU acceleration to typical data science tasks.  Please refer to the async materials for more information on the project or visit [The RAPIDS homepage](https://rapids.ai/)
For this lab, we'll be using the latest rapids container. From your home directory in your VM, pull and start the rapids container.  Note that this will start Jupyter by default and you will need to open port 8888 to connect to it.
```
docker run -p 8888:8888 --gpus=all -ti nvcr.io/nvidia/rapidsai/rapidsai:21.10-cuda11.2-runtime-ubuntu20.04 
```
Try the following notebooks:
* Download the [Colab example](https://colab.research.google.com/drive/1rY7Ln6rEE1pOlfSHCYOVaqt8OvDO35J0#forceEdit=true&offline=true&sandboxMode=true) and run it in your Jupyter notebook.  Skip the cells that deal with RAPIDS installation. Note how easy it is to use CuDF and CuML
* Under the cuml folder, run through the K-means demo example. What is the speedup you get?
* Under the same folder, run through the random forest example.  What is the speedup you get?
* Under the xgboost folder, run the XGBoost demo. Repeat on the CPU. What is the speedup?

### DALI primer
DALI stands for Data Loading Library.  This Open Source project is another tool in our arsenal to eliminate or at least reduce CPU bottlenecks in our pipelines.  We did not cover DALI in the async material since it was very new, but now it's part of most Nvidia accelerated pipelines and is present in all Deep Learning NGC containers.

* Please glance through the [DALI Documentation](https://docs.nvidia.com/deeplearning/dali/user-guide/docs/index.html)
* Start the pytorch ngc container, e.g. ```docker run --rm --gpus all -p 8888:8888 --ipc=host -ti  nvcr.io/nvidia/pytorch:21.11-py3``` and then start jupyter lab , e.g. ```jupyter lab --ip=0.0.0.0 --allow-root```
* Upload the [Getting Started](getting_started_dali.ipynb) example to your jupyter environment and run through it. What acceleration did you get in the last cell? Can you suggest what contributes to that number?


