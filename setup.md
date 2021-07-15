## DeeptCar용 라즈베리파이 보드 셋업 및 필요 소프트웨어 설치

### 라즈베리파이 보드 연결 
라즈베리파이 OS 이미지를 만든 후에는 라즈베리파이 보드를 부팅하고 보드를 셋업하는 작업을 해야 합니다. 아래 링크는 라즈베리파이 보드 셋업을 잘 설명하고 있습니다.   

[라즈베리파이 보드 셋업(영문)](https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up)

라즈베리파이 보드를 셋업하기 위해서는 모니터/키보드/마우스를 라즈베리파이에 연결해서 사용하는 것이 좋습니다. 연결하는 방법은 아래 그림을 참고하 주십시오.       
라즈베리파이 OS 이미지가 있는 SD카드를 라즈베리파이 SD카드 슬롯에 삽입합니다. 그리고 전원 단자에 전원을 연결합니다. 라즈베리파이는 1A 전후의 많은 전류를 소모 합니다.    
따라서 PC의 USB 포트를 전원으로 사용하지 마십시오. 향후 설명할 DeeptCar의 배터리를 사용하거나 스마트폰 충전용 USB 충전기를 사용하는 것이 좋습니다.    

![image](https://user-images.githubusercontent.com/76054530/125740222-dffcaeeb-1982-445d-b534-761ebd2c9a01.png)    
출처: 라즈베리파이 재단   

### 라즈베리파이 보드 일반 셋업 
라즈베리파이를 최초로 부팅했을 때는 여러가지 셋업 작업을 해야 합니다. 셋업해야 할 작업은 지역설정, WiFi, 모니터 해상도, 인터페이스 셋업이 있습니다. 
상세한 셋업은 다음 링크를 참고해 주십시오. 

[라즈베리파이 최초 부팅 셋업](https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up/4)   

다만 주의해야 할 것은 가능하면 지역 설정은 대한민국/서울로 하지만 "Use English Language"와 "Use US keyboard"를 체크해서 영어와 영문키보드를 사용하는 것으로 정합니다.    
개발 혹은 코딩교육용으로는 한글보다는 영어 및 영문 키보드로 설정하는 것이 좋습니다.    

![image](https://user-images.githubusercontent.com/76054530/125741576-5d470544-34ec-48c3-8fd2-c29dd48d039c.png)

### 라즈베리파이 인터페이스 셋업 
보드의 일반 셋업이 끝이나면 라즈베리파이 인터페이스를 셋업 합니다. 인터페이스를 셋업하려면 "Raspberry Pi Configuration"을 실행해야 합니다.    
"Raspberry Pi Configuration"은 다음 그림을 참고해서 실행하면 됩니다. 

![image](https://user-images.githubusercontent.com/76054530/125742284-d46cca9e-bd0b-42b1-8ee3-0820f8d2a06f.png)

인터페이스 셋업 화면이 실행이 되면 아래 그림과 같은 셋업 윈도가 뜨기 됩니다. 

![image](https://user-images.githubusercontent.com/76054530/125742457-61f1c74a-6ec1-482d-8efd-61d9e45a9489.png)

이 인터페이스 셋업 윈도에서 "Camera", "SSH", "VNC", "SPI", "I2C", "Serial Port"를 "Enalbe"을 체크해서 활성화 시킵니다.   
이후에는 라즈베리파이를 재부팅하면 인터페이스 셋업이 끝이 납니다.  


DeeptCar의 코드는 파이썬3로 작성되었습니다. 라즈베리파이 OS에 파이썬3를 설치하려면 터미널 프로그램을 이용해서 다음과 같이 설치하면 됩니다.   
<pre><code>$sudo apt-install pip3
$pip3 install python3
</code></pre>
##### 텐서플로
텐서플로는 구글에서 제공하는 딥러닝 라이브러리 입니다. DeeptCar 자율주행 코드는 텐서플로 라이브러리를 사용하여 딥러닝을 실행합니다. 그래서 텐서플로 라이브러리를 설치 합니다. 설치하는 방법은 다음과 같습니다. 

이 레포지터리의 자율주행 코드는 텐서플로 2.3.0을 사용하여 테스트 되었습니다. 
##### 케라스
케라스는 텐서플로와 같이 딥러닝에 사용되는 뉴럴네트워크 API 라이브러리 입니다. DeeptCar 자율주행 파이썬 코드는 텐서플로와 케라스를 사용하여 뉴럴네트워크 구성, 딥런닝 트레이닝, 추론 등을 수행합니다. 케라스를 설치하여면 다음과 같이 합니다. 
<pre><code>$pip3 install keras</code></pre>
이 레포지터리의 자율주행 코드는 케라스 2.4.3을 사용하여 테스트 되었습니다.
##### OpenCV
OpenCV는 DeeptCar의 카메라에서 출력되는 이미지를 프로세싱하는 컴퓨터 비젼 라이브러리 입니다. DeeptCar 자율주행 파이썬 코드는 OpenCV 라이브러리를 사용하여 차선인식을 수행합니다. OpenCV를 설치하려면 다음과 같이 합니다. 
<pre><code>$pip3 install opencv-python
$pip3 install opencv-contrib-python
</code></pre>
이 레포지터리의 자율주행 코드는 OpenCV 3.4.6을 사용하여 테스트 되었습니다.
##### 에이다프루트 서보 제어모듈(Adafruit=circuitpython-servokit)
DeeptCar 앞바퀴를 제어하는 서보모터를 동작시키기 위해서 이 라이브러리가 필요합니다. 이 라이브러리는 다음과 같이 설치가 가능합니다. 
<pre><code>$pip3 install adafruit-circuitpython-servokit</code></pre>
이 라이브러리를 사용하는 방법은 [여기](https://circuitpython.readthedocs.io/projects/servokit/en/latest/)을 참고하면 됩니다. 
https://circuitpython.readthedocs.io/projects/servokit/en/latest/
