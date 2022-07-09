FROM mcr.microsoft.com/cntk/release:2.5.1-cpu-python3.5
 
RUN dpkg --add-architecture i386 && apt-get update && apt-get install -y build-essential git python3-pip python3-tk libglib2.0-0:i386 && rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install --upgrade pip==20.3.4
RUN pip3 install -U scikit-learn
RUN pip3 install numpy pandas sklearn matplotlib
RUN pip3 install scipy
RUN pip3 install opencv-python-headless
RUN pip3 install dlib -vvv
RUN pip3 install scikit-image
RUN pip3 install matplotlib
RUN pip3 install cntk
RUN pip3 install flask pillow

RUN mkdir /usr/src/nestle
WORKDIR /workspace
RUN chmod -R a+w /workspace
ADD /models /workspace/models
COPY shape_predictor_68_face_landmarks.dat /workspace/models
COPY haarcascade_eye.xml /workspace/models
COPY ResNet152_ImageNet_Caffe.model /workspace/models
COPY cntk_regression.dat /workspace/models
COPY main.py /workspace
COPY regressionModel.py /workspace
COPY getPatches.py /workspace
COPY model.py /workspace
RUN chmod +x /workspace/main.py
RUN ls /workspace
CMD python3 /workspace/main.py
 
EXPOSE 9580
