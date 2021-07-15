## DeeptCar에 사용할 라즈베리파이 OS 이미지 만들기 

라즈베리파이 OS 이미지를 만드는 방법은 여러가지 있습니다. 이 중에서 많이 사용되는 두가지 방법을 사용해서 라즈베리파이 OS 이지미를 만들 수 있습니다.
첫번째 방법은 라즈베리파이 재단에서 권장하는 Raspberry Pi Imager를 사용하는 방업입니다. 두번째는 balenaEcher라는 프로그램을 사용하여 이미지를 만들 수 있습니다. 

### Raspberry Pi Imager를 사용하여 OS 이미지 만들기 
#### 개요 및 다운로드 하기 
Raspberry Pi Imager는 OS 이미지 다운로드와 SD카트 라이팅을 한번에 할 수 있는 라이팅 툴 입니다. 다운로드를 받으려면 다음 사이트에서 다운로드 받을 수 있습니다.   
[다운로드](https://www.raspberrypi.org/software/)
#### Raspberry Pi Image 사용법 
라즈베리파이 OS를 이미지를 만들려면 먼저 Raspberry Pi Imager를 실행합니다. 
![image](https://user-images.githubusercontent.com/76054530/125730638-d5382a8e-d0c4-4c94-a7b6-a428a8768aeb.png)   
그 다음에는 "CHOOS OS"를 클릭합니다. 클릭을 하면 여러가지 OS가 제시되는데 RAspbery PI OS (32bit)를 선택합니다. 
![image](https://user-images.githubusercontent.com/76054530/125730874-a9d9d455-672c-4f64-abaa-862f60856d77.png)   
그 다음에는 OS 이미지를 라이팅 할 SD카드를 선택합니다. 미리 PC에 16GB의 SD카드를 연결해 놓아야 합니다. SD카드가 연결되어 있으면 위 그림과 같이 SD카드가 용량과 함께 표시되는 것을 볼 수 있습니다.
![image](https://user-images.githubusercontent.com/76054530/125731640-0dde51e3-eb39-4b19-88a2-35ae9013cffa.png)   
SD카드 연결를 선택했으면 그 다음에는 "WRITE"를 클락합니다. 그러면 아래 그림과 같이 라이팅이 시작이 됩니다.    
SD카드 라이팅이 완료되면 SD카드를 PC에서 뽑아서 라즈베리파이의 SD카드 슬롯에 넣고 전원을 넣으면 부팅이 됩니다.   
초기에는 셋팅을 편하게 하기 위해서 모니터/키모드/마우스를 라즈베리파이에 연결을 해 놓고 라즈베리파이 셋업을 하는 것이 편리합니다.
![image](https://user-images.githubusercontent.com/76054530/125731053-6599c2d0-460b-4222-8932-82360e83afc9.png)   
간혹 아래 그림처럼 SD카드 이미지 라이팅이 실패하는 경우가 생깁니다. SD카드 리더기의 문제일 가능성이 있습니다. 이럴 경우에는 BalenaEcher를 사용하여 이미지를 라이팅 해야합니다.
![image](https://user-images.githubusercontent.com/76054530/125731337-65715557-c4b1-4fbc-a467-4746ba7d54cd.png)   
### balenaEtcher를 사용하여 OS 이미지 만들기 
#### 개요 및 다운로드 하기 
balenaEtcher는 라즈베리파이 OS를 별도로 다운 받아놓고 SD카드에 라이팅을 할 수 있습니다. 상황에 따라 라브베리파이 OS 다운로드 시간이 많이 걸리는 경우가 종종 있는데 OS이미지를 계속 라이팅을 하려면 balenaEtcher가 더 편리합니다. beleanEtcher는 아래 링크에서 다운 받을 수 있습니다. 
[balenaEtcher](https://www.balena.io/etcher/)
### balenaEtcher 사용법 
먼저 

balenaEtcher를 실행합니다. 이 프로그램을 실행하면 다음과 같은 화면을 볼 수 있습니다. 
![image](https://user-images.githubusercontent.com/76054530/125732538-e59a94e1-6e6d-4618-b2ae-98cff665fded.png)   
여기서 "

 
