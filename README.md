# DeepFace React

deepface-react-ui is a comprehensive user interface for facial recognition and facial attribute analysis (age, gender, emotion and race prediction) built with ReactJS, designed specifically for streamlined face verification tasks using the [DeepFace](https://github.com/serengil/deepface) library. Whether you're working on identity verification systems, security applications, or simply exploring facial recognition technology, this UI provides an intuitive platform to harness the power of DeepFace within your web applications.

Facial recognition technology plays a pivotal role in modern applications, from enhancing security measures to enabling personalized user experiences. The deepface-react-ui empowers developers and researchers to harness these capabilities effortlessly within their web applications.

## Cloning The Service

Firstly, you should clone both deepface and deepface-react-ui repos in same directory.

```shell
# clone deepface repo
git clone https://github.com/serengil/deepface-react-ui.git \
    && git clone https://github.com/serengil/deepface.git
```

## Facial Database Configuration

There is `.env.example` file in the root of the project. You should copy this as `.env`. Required modifications are mentioned as comments. You basically need to add your facial database items into this file, prefixing each with `REACT_APP_USER_`, where the identity name with that prefix serves as the key and the base64-encoded string of their images serves as the value.

```yaml
# define your facial database
REACT_APP_USER_ALICE=data:image/png;base64,...
REACT_APP_USER_BOB=data:image/png;base64,...
REACT_APP_USER_CAROL=data:image/png;base64,...
```

Both facial recognition models and face detectors can be set in the `.env` file.

```yaml
# Set facial recognition model: VGG-Face, Facenet, Facenet512, OpenFace, DeepFace, DeepId, ArcFace, Dlib, SFace, GhostFaceNet
REACT_APP_FACE_RECOGNITION_MODEL=Facenet

# Set face detector: opencv, ssd, mtcnn, dlib, mediapipe, retinaface, yolov8, yunet, centerface
REACT_APP_DETECTOR_BACKEND=opencv

# Set distance metric: cosine, euclidean, euclidean_l2
REACT_APP_DISTANCE_METRIC=cosine
```

## Running Service Directly

Firstly, you should run the deepface service as

```shell
# go to project's directory
cd deepface/scripts

# run the dockerized service
./dockerize.sh

# or instead of running dockerized service, run it directly if you installed requirements.txt
# ./service.sh
```

In seperate terminal, you should run deepface react ui as

```shell
# go to project's directory
cd deepface-react-ui/scripts

# run the dockerized service
./dockerize.sh

# or instead of running dockerized service, run it directly
# ./service.sh
```

## Running via Docker Compose

Instead of running deepface and deepface react ui seperately in different terminals, you can run the standalone docker compose.

```shell
# clone source code
git clone https://github.com/serengil/deepface-react-ui.git \
    && git clone https://github.com/serengil/deepface.git

# go to project's directory
cd deepface-react-ui/scripts

# run services
./compose.sh
```

## Using The App

Once you start the service, the DeepFace service will be accessible at `http://localhost:5005/`, and the DeepFace React UI will be available at `http://localhost:3000/`.

To use the DeepFace React UI, open `http://localhost:3000/` in your browser. The UI will prompt access to your webcam and search for identities within the current frame using the facial database specified in the `.env` file when you click on the "Verify" button.