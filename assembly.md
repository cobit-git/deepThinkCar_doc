(아직 작성중입니다.)
## deepThinCar 조립하기 
deepThinkCar를 조립하기 전에 박스안에 포함되어 있는 키트구성품을 확인합니다. 구매하신 deepThinkCar키트 안에는 다음 사진과 같은 키트 구성품이 있습니다. 
![deepThinkCar 패킹 리스트](https://user-images.githubusercontent.com/76054530/156094930-f58e972f-d33c-4b0d-b4a7-4a39dc458763.jpg)  
키트의 박스안에는 역시 키트 구성품의 패킹 리스트가 있습니다. 키트 패킹 리스트와 실제 구성품이 일치하는지 확인합니다. 
OS SD카트, 여분의 나사는 패킹 리스트에 기록되어 있지는 않지만 필요합니다. **라즈베리파이 보드는 포함되어 있지 않습니다. 별도 구매하셔야 합니다.** 

### 1. 아크릴 본체 상판에 모터보드 연결 
패킹 리스트를 통해서 구성품을 확인했으면 그 다음에는 아크릴 본체 상판에 모터보드를 연결 조립합니다. 모터보드를 연결하기 위해서는 다음 구성품이 필요합니다. 

- 0번 아크릴 본체 상판
- 19번 모터보드
- 2번 연결부품
- 조립을 위해 20번 드라이버 렌치
 
![motor_board_assy_1](https://user-images.githubusercontent.com/76054530/156096834-2a1e4fba-d572-49b6-931e-b922a4772674.jpg)

2번 연결부품에는 다음 부품이 포함되어 있습니다. 드라이버와 렌치를 이용해서 이 연결 부품을 아크릴 본체 상판에 장착합니다. 

- M2.5 너트 4개
- M2.5x12 PCB서포터 4개
- M2.5x5 볼트 4개 

아크릴 본체 상판을 확인 하시고, 아크를 상판의 사진을 잘 확인해서 연결하시면 됩니다. 
![motor_board_assy_2](https://user-images.githubusercontent.com/76054530/156097901-8867b3ce-71be-499e-a436-17bf01baa2ee.jpg)

### 2. 앞바퀴 제어용 서보모터 연결 
모터보드 연결 다음에는 앞바퀴 제어용 서버모터를 연결합니다. 서보모터를 연결하기 위해서는 다음 구성품이 필요합니다. 

 - 아크릴 본체 상판: 모터보드 연결된 상태
 - 19번 서보모터 키트 
 - 8번 서버모터 고정부품: M2x8 볼트 2개 M2 너트 2개   
    
![servo_assy_1](https://user-images.githubusercontent.com/76054530/156100671-e7be2876-fc65-41e7-8529-c30048323ff2.jpg)

19번 서보키트에서 서보모터만 준비합니다. 서보키트 안에 있는 여러 arm부품과 나사 부품은 나중에 사용 합니다. 
서보모터를 M2x8 볼트.너트롤 아크릴 본체 상판에 고정합니다. 아래 사진의 위치를 참고해서 조립하면 됩니다. 부품이 작아서 조립이 조금 어려운 점 참고하십시오.   
![servo_assy_2](https://user-images.githubusercontent.com/76054530/156101053-be4eeed1-a5e5-4e54-8df9-2a8b17dccc3c.jpg)

### 3. 배터리홀더 연결 
서보모터를 조립한 후에는 배터리홀더를 연결합니다. 배터리홀더를 연결하기 위해서는 다음 구성품이 필요합니다.
**사용가능한 배터리는 18650 충전배터리입니다. 키트에는 포함되어 있지 않습니다. 별도 구매하셔야 합니다.**

- 아크릴 본체 상판: 모터보드, 서보모터 연결 상태 
- 14번 배터리홀더 
- 5번 배터리홀더 연결 부품 

![battery_holder_assy_1](https://user-images.githubusercontent.com/76054530/156103537-c32c4c6e-168b-4080-b4e9-36a96f66c3d0.jpg)  

배터리홀더를 아크릴 본체 상판에서 서보모터와 모터보드가 연결된 반대방향에 부착하고 볼트/너트를 연결합니다. 
배터리홀더 연결부품은 M3x8 접시머리 나사와 M3 너트가 사용됩니다. 배터리홀더에 배터리를 넣기 위해서는 돌출부가 없어야 하므로 접시머리를 사용합니다. 

![battery_holder_2](https://user-images.githubusercontent.com/76054530/156104431-608d1c1d-0dc7-45c1-9ee2-d573df8ba921.jpg)


### 4. 라즈베리파이 보드 연결 
배터리홀더를 연결한 다음에는 라즈베리파이 보드를 연결합니다. deepThinkCar에 사용할 수 있는 라즈베리파이 보드는 라즈베리파이 3B+, 4B 입니다. 
라즈베리파이 제로나 라즈베리파이 3A+ 는 사용할 수 없습니다. 또한 3B+ 이전 보드는 성능 문제가 있어서 사용하지 마시기 바랍니다. 
라즈베리파이를 연결하기 위해서는 아크릴 본체 상판(모터보드 결합), 3번 HAT 보드 연결부품, 12번 HAT 보드, 그리고 라즈베리파이 보드가 필요 합니다. 
라즈베리파이 보드 연결을 위해서는 다음 구성품이 필요합니다. 

- 아크릴 본체 상판: 모터보드, 서보모터, 배터리홀더 연결상태 
- **라즈베리파이 보드 (키트에는 포함되어 있지 않습니다. 별도 구매하셔야 합니다.)**
- 3번 HAT보드 연결 부품 
- 12번 HAT보드: 라즈베리파이 위에 올려지는 보드입니다.   

![라즈베리파이 조립에 필요한 구성품](https://user-images.githubusercontent.com/76054530/156106023-0d468151-4cb6-4697-8f46-322107780567.jpg)

3번 HAT보드 연결부품은 다음 부품이 포함되어 있습니다. 드라이버와 렌치를 이용해서 이 연결 부품을 아크릴 본체 상판에 장착합니다. 

- M2.5x5 볼트 4개
- M2.5x12 PCB 서포터 6개
- M2.5 너트 4개 

라즈베리파이 보드 및 HAT 보드 조립은 아래 사진의 순서대로 연결하면 됩니다. 제일 먼저 M2.5x12 PCB 서포트 4개와 너트 4개를 조립합니다. 

![rpi_assy_2](https://user-images.githubusercontent.com/76054530/156107749-29b5012e-c4f3-497f-b247-e3584e807408.jpg)

그 다음에는 M2.5x12 PCB 서포트 위에 라즈베리파이 보드를 얹고, 노란색 원의 표시와 같이 M2.5x5 볼트를 체결합니다. 

![rpi_assy_3](https://user-images.githubusercontent.com/76054530/156107894-17f91361-3236-46cb-b4ad-9e9186b22c73.jpg)

그 다음에는 

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
