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
