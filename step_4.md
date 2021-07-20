## DeeptCar 자율주행 4단계: 딥러닝 기반 자율주행

### 4단계에서는...
4단계에서는 3단계에서 생성한 추론파일을 이용해서 딥러닝 기반 자율주행을 실행합니다. 카메라 영상을 추론파일로 처리해서 앞바퀴의 각도를 추출합니다. 깃허브에서 다운받은 DeeptCar 파이썬 코드 중에서 딥러닝 자율주행을 실행하는 코드는 "cobit_5_lane_follower_deep.py" 입니다. 핵심적인 딥러닝 자율주행 라이브러리는 "cobit_deep_lane_detect.py" 파이썬 코드에 있습니다. 

### 필요한 모듈 import 하기
4단계 딥러닝 자율주행을 위해서는 다음 파이썬 모듈들을 임포트 해야 합니다. cv2 모듈은 OpenCV 모듈 입니다. ServoKit 모듈은 앞바퀴 조향용 서보모터를 제어하기 위한 모듈 입니다.     
CobitDeepLaneDetect 모듈은 딥러닝 추론파일을 이용해서 차선을 인식하고, 차선의 각도를 파악해서 알려주는 차선인식모듈 입니다. CobitCarMotorL9110 모듈은 뒷바퀴 기어드 DC모터를 제어하는 모듈 입니다.

```python
import cv2
from adafruit_servokit import ServoKit
from cobit_deep_lane_detect import CobitDeepLaneDetect
from cobit_car_motor_l9110 import CobitCarMotorL9110
```

### 필요한 모듈 객체 만들기
딥러닝 차선인식 주행을 시작하기 전에 필요한 모듈의 객체를 생성하고 초기화를 합니다. 
1. 앞바퀴 서보 모터 제어를 위한 SerovKit 모듈의 객체를 만듭니다. 
2. 차선인식에 사용할 딥러닝 차선인식모듈의 객체를 만듭니다. 이 때 model 폴더의 추론파일을 로드 합니다. 
3. 뒷바퀴 구동용 DC모터를 위한 L9110 DC 모터 드라이버 모듈의 객체를 만듭니다.

```python
deep_detector = CobitDeepLaneDetect("./models/lane_navigation_final.h5")
motor = CobitCarMotorL9110()
servo = ServoKit(channels=16)
```

### 카메라 셋팅하기 
DeeptCar 전방에 설치된 Pi카메라를 셋팅합니다. 해상도를 OpenCV 주행때와 같게 320x240으로 셋팅 합니다. 그 이상의 해상도는 WiFi와 VNC를 통한 원격 제어에 문제가 생기게 됩니다.
```python
SCREEN_WIDTH = 320
SCREEN_HEIGHT = 240

cap = cv2.VideoCapture(0)
cap.set(3, int(SCREEN_WIDTH))
cap.set(4, int(SCREEN_HEIGHT))
```
### 출발전 차선에 맞게 앞바퀴 스티어링 앵글 조정 
DeeptCar는 출발 전에 앞바퀴 스티어링 앵글을 현재 차선의 굽어짐에 맞게 조정해야할 필요가 있습니다. 딥러닝으로 현재 차선의 굽어짐을 파악하는 데는 약간의 시간이 필요합니다.    
출발을 바로 하면 딥러닝으로 차선의 굽어짐을 파악하기도 전에 차선을 벗어날 가능성이 있습니다. 그래서 출발 전 몇초 동안은 뒷바퀴를 구동하지 않고 제자리에서 딥러닝으로 먼저 차선인식을 구동합니다. 

```python
for i in range(30):
    ret, img_flip = cap.read()
    img_org = cv2.flip(img_flip, 0)
    if ret:
        angle_deep, img_angle = deep_detector.follow_lane(img_org)
        if img_angle is None:
            print("angle image out!!")
            pass
        else:
            print(angle_deep)
            servo.servo[0].angle = angle_deep + servo_offset			
            cv2.imshow("img_angle", img_angle)
            cv2.waitKey(1)
    else:
        print("cap error")
```	    
		
### 메인 루프  
앞바퀴 스티어링 앵글 조정이 끝나면 DeeptCar를 출발시키고 딥러닝 차선인식 주행을 실행합니다. 아래 코드는 차선인식 주행을 하는 메인 루프 코드 입니다.  
```python
while cap.isOpened():
    ret, img_org = cap.read()
    angle_deep, img_angle = deep_detector.follow_lane(img_org)
    if img_angle is None:
        print("angle image out!!")
        pass
    else:
        print(angle_deep)
        servo.servo[0].angle = angle_deep + servo_offset

        cv2.imshow("img_angle", img_angle)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
```

카메라를 통해서 이지미를 읽어오는 코드는 다음과 같습니다. 
```python
ret, img_org = cap.read()
```
이 이미지를 입력값으로 deep_detector.follow_lane() 함수를 통해서 차선 각도를 추출합니다. 코드는 다음과 같습니다. 
```python
angle_deep, img_angle = deep_detector.follow_lane(img_org)
```

### 앞바퀴 스티어링 각도를 이용한 서보 제어
앞바퀴 스티어링 각도가 결정 되면 이 각도로 서보를 제어합니다. 서보 각도를 제어할 때, 주행 정밀도를 높이기 위해 필요하다면 오프셋 값을 조정할 수 있습니다.
카메라의 이미지에 차선이 검출되지 않으면 그 이지미는 무시합니다. 
```python
if img_angle is None:
    print("angle image out!!")
        pass
else:
    print(angle)
        servo.servo[0].angle = angle + servo_offset
```
### 주행의 마무리
딥러닝 차선인식 주행을 실행할 때, VNC로 DeeptCar를 제어 한다면 'q'키를 입력해서 주행을 종료할 수 있습니다.    
종료를 처리하는 코드는 다음과 같습니다. 
```python
motor.motor_stop()
cap.release()
cv2.destroyAllWindows() 
```
### 그 다음 단계
딥러닝 차선인식 주행에 성공하면, 그 다음 단계는 MobileNet SSD와 트랜스퍼 러닝(Transfer Learning)를 사용하여 보행자, 신호등, 및 교통신호를 인식하는 오브젝트 디텍션(Object Detection)을 실행하게 됩니다. 다음 링크를 통해서 5단계로 갈 수 있습니다.     
[5단계 오브젝트 디텍션](https://cobit-git.github.io/deeptcar_doc/step_5)


