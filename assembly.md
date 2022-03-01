(아직 작성중입니다.)
## deepThinCar 조립하기 
deepThinkCar를 조립하기 전에 박스안에 포함되어 있는 키트구성품을 확인합니다. 구매하신 deepThinkCar키트 안에는 다음 사진과 같은 키트 구성품이 있습니다. 
![kit_packing_list](https://user-images.githubusercontent.com/76054530/156093512-84e86691-c5c4-4d36-a879-f395e886b58c.jpg)

키트의 박스안에는 역시 키트 구성품의 패킹 리스트가 있습니다. 키트 패킹 리스트와 실제 구성품이 일치하는지 확인합니다. 

### 1 라즈베리파이를 뺀 나머지 차체의 조립이 끝나면 차체에 라즈베리파이를 설치합니다.
라즈베리파이 부분을 뺀 나머지 차체가 조립이 끝이 나면 아래 사진과 같이 조립이 되어 있어야 합니다.    
![조립_라즈베리파이_1](https://user-images.githubusercontent.com/76054530/141405330-6402406c-1a85-4a70-9f03-2493838750c8.jpg)

### 2. 라즈베리파이 체결용 나사, PCB마운트 준비 
라즈베리파이 보드를 마운트 하기위해서 다음과 같이 PCB 지지대(M2.5x 12mm)두개와 M2.5 나사 2개가 필요합니다.    
![조립_라즈베리파이_0](https://user-images.githubusercontent.com/76054530/141405341-43e582d7-d54b-4cc9-abfc-7f7be85651bf.jpg)

### 3. M2.5 나사 체결
라즈베리파이를 차체에 올려놓고 M2.5 나사 2개를 아래 사진과 노란색 원과 같이 체결합니다. 플라스틱 나사이므로 너무 세게 체결하지 마십시오.    
![조립_라즈베리파이_2](https://user-images.githubusercontent.com/76054530/141406404-982bcd4f-53c8-4a75-8e5d-28891791313a.jpg)


### 4. M2.5 x 12mm PCB 지지대 체결 
다음에는 아래 사진의 노란색원과 같이 M2.5 x 12 PCB 지지대를 체결합니다.    
![조립_라즈베리파이_3](https://user-images.githubusercontent.com/76054530/141406423-f5de8d82-d9cf-4b54-972b-16765d8cb450.jpg)

### 5. 파이카메라 케이블 연결 
HAT 보드를 설치하기 전에 먼저 파이카메라의 케이블을 라즈베리파이 카메라 커넥터에 연결 합니다. 연결할 때 케이블의 은색 부분이 차체 뒤쪽으로 향하게 합니다.   
케이블 반대편인 은색 부분이 차체 뒤쪽으로 항하게 라즈베리파이 카메라 커넥터에 깊게 장착을 합니다.    
![조립_라즈베리파이_4](https://user-images.githubusercontent.com/76054530/141406431-d4dc5422-4940-4c50-9c55-528b424532b1.jpg)
![조립_라즈베리파이_5](https://user-images.githubusercontent.com/76054530/141406438-4ce3fb97-27e0-45d3-85f2-a61bca7b5b92.jpg)


### HAT 보드 장착 
카메라 케이블 연결이 끝이 났으면, 다음에는 HAT 보드를 라즈베리파이 GPIO 커넥터에 장착합니다. 이때 정확하게 연결했는지 확인 해야 합니다.    
연결이 잘못된 상태로 전원을 연결하면 일부 라즈베리파이 GPI가 손상될 수 있습니다.    
![조립_라즈베리파이_6](https://user-images.githubusercontent.com/76054530/141406442-b637fc54-18a9-4117-ba33-b4dcb5e2938e.jpg)


### 링크
[라즈베리파이 OS 이미지 만들기](https://cobit-git.github.io/deepThinkCar_doc/os)    
[라즈베리파이 소프트웨어 설치 및 셋업](https://cobit-git.github.io/deepThinkCar_doc/setup)   
[deepThinkCar 라즈베리파이 VNC 환경 구축](https://cobit-git.github.io/deepThinkCar_doc/vnc)   
[deepThinkCar 조립순서](https://cobit-git.github.io/deepThinkCar_doc/assembly)    
[deepThinkCar 하드웨어 테스트](https://cobit-git.github.io/deepThinkCar_doc/hardware)   
[1단계 OpenCV 차선인식 주행](https://cobit-git.github.io/deepThinkCar_doc/step_1)   
[2단계 차선인식 데이터 라벨링](https://cobit-git.github.io/deepThinkCar_doc/step_2)   
[3단계 딥러닝 트레이닝](https://cobit-git.github.io/deepThinkCar_doc/step_3)   
[4단계 딥러닝 차선인식 주행](https://cobit-git.github.io/deepThinkCar_doc/step_4)      
[5단계 오브젝트 디텍션](https://cobit-git.github.io/deepThinkCar_doc/step_5)
