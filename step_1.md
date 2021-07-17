
## DeeptCar 자율주행 1단계: OpenCV 차선인식 주행  

### 1단계에서는...
1단계에서는 OpenCV를 이용한 차선인식 주행을 실행할 수 있습니다. 카메라 영상을 이용해서 차선을 인식하는 기능은 이미 ADAS(Advanced Driver Assistance System)라는 이름으로 사용화 되어 있습니다. DeeptCar는 OpenCV 라이브러리를 이용해서 ADAS와 유사하면서 기초적인 차선인식 주행을 실행할 수 있습니다. 1단계에서는 OpenCV를 통한 차선인식 주행을 할 뿐 아니라 차선을 따라 주행하는 영상 데이터를 얻을 수 있습니다. 2단계에서는 이 영상 데이터를 가공해서 딥러닝 트레이닝에 필요한 데이터셋을 얻는 라벨링 작업을 하게 됩니다. 

### 필요한 모듈 import 하기 
1단계 차선인식 주행을 위해서 다음 파이썬 모듈들을 임포트 해야 합니다. cv2 모듈은 OpenCV 모듈 입니다. ServoKit 모듈은 앞바퀴 조향용 서보모터를 제어하기 위한 모듈 입니다.     
CobitOpencvLaneDetect 모듈은 실제적으로 OpenCV를 이용해서 차선을 인식하고, 차선의 각도를 파악해서 알려주는 모듈 입니다.     
CobitCarMotorL9110 모듈은 뒷바퀴 기어드 DC모터를 제어하는 모듈 입니다. 

```python
import cv2
from adafruit_servokit import ServoKit
from cobit_opencv_lane_detect import CobitOpencvLaneDetect
from cobit_car_motor_l9110 import CobitCarMotorL9110
import time 
```

### 필요한 모듈 객체 만들기 
차선인식 주행을 시작하기 전에 필요한 모듈의 객체를 생성하고 초기화를 합니다. 
1. 앞바퀴 서보 모터 제어를 위한 SerovKit 모듈의 객체를 만듭니다. 
2. 차선인식에 사용할 OpenCV 모듈의 객체를 만듭니다. 
3. 뒷바퀴 구동용 DC모터를 위한 L9110 DC 모터 드라이버 모듈의 객체를 만듭니다. 

'''python
  servo = ServoKit(channels=16)
  cv_detector = CobitOpencvLaneDetect()
  motor = CobitCarMotorL9110()
'''

### 카메라 셋팅하기 
DeeptCar 전방에 설치된 Pi카메라를 셋팅합니다. 해상도를 320x240으로 셋팅 합니다. 그 이상의 해상도는 WiFi와 VNC를 통한 원격 제어에 문제가 생기게 됩니다. 

```python
	SCREEN_WIDTH = 320
	SCREEN_HEIGHT = 240

	cap = cv2.VideoCapture(0)
	cap.set(3, int(SCREEN_WIDTH))
	cap.set(4, int(SCREEN_HEIGHT))
```

### 영상 레코딩 준비
Pi카메라 영상을 레코딩 하기 위해서 셋팅을 합니다. 레코딩 된 영상은 /data 폴더에 car_video.avi 라는 이름으로 저장 됩니다. 

```python
  fourcc =  cv2.VideoWriter_fourcc(*'XVID')
	try:
		if not os.path.exists('./data'):
			os.makedirs('./data')
	except OSError:
		pass
	video_orig = cv2.VideoWriter('./data/ car_video.avi', fourcc, 20.0, (SCREEN_WIDTH, SCREEN_HEIGHT))
```
  

