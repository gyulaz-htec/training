ARG FROM_IMAGE_NAME=compute-artifactory.amd.com:5000/rocm-plus-docker/framework/compute-rocm-dkms-no-npi-hipclang:15624_ubuntu22.04_py3.10_pytorch_release-2.4_8d1b92f
FROM ${FROM_IMAGE_NAME}

ENV DEBIAN_FRONTEND=noninteractive
ENV RCLONE_VER=v1.67.0

# apt dependencies
RUN apt-get update
RUN apt-get install -y ffmpeg libsm6 libxext6

# Remove the opencv version shipped with the base image
# https://github.com/opencv/opencv-python/issues/884
RUN pip uninstall -y opencv
RUN rm -rf /usr/local/lib/python3.10/dist-packages/cv2/

WORKDIR /workspace/code

COPY . .
RUN pip install -r requirements.txt
