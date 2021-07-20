## DeeptCar 자율주행 3단계: 딥러닝 트레이닝 

### 3단계에서는...
3단계에서는 2단계에서 라벨링 된 데이터를 CNN을 통해서 딥러닝 트레이닝을 실행합니다. 이 단계는 라즈베리파이에서 실행하지 않고 PC에서 실행하게 됩니다.    
라즈베리파이는 CNN을 통한 딥러닝 트레이닝을 실행하기에는 성능이 많이 부족해서 PC를 이용합니다. CNN 딥러닝 트레이닝을 하기 위해서는 다음의 단계를 실행합니다. 

### deeptcar/data 폴더의 라벨링 데이터를 PC로 옮깁니다. 
라즈베리파이의 워킹 폴더인 deeptcar/data 폴더에 저장된 라벨링 데이터인 PNG 파일들을 압축합니다.    
압축을 하는 이유는 라즈베리파이에서 PC로 라벨링 데이터를 쉽게 전달하기 위해서 입니다. 압축을 하기 위해서는 다음 코드를 실행합니다.    
<pre><code>
$python3 cobit_label_data_compress.py
['./data/car_video.avi_016_075.png', './data/car_video.avi_143_104.png',  ...
... './data/car_video.avi_158_097.png']
$ ls -al
...
-rw-r--r--  1 pi pi 17087793 Jul 20 11:29 car_image_angle.zip
...
</code></pre>

압축을 위해 "cobit_label_data_compress.py" 스크립트를 실행하면 "car_image_angle.zip"이라는 압축파일이 하나 생깁니다.    
이 파일을 주피터 노트북을 이용해서 PC로 옮겨야 합니다. 이를 위해 먼저 주피터 노트북을 다음과 같이 실행합니다. 
<pre><code>
pi@raspberrypi:~/deeptcar $ jupyter-notebook --ip=172.31.99.111 --no-browser
....    
    To access the notebook, open this file in a browser:
        file:///home/pi/.local/share/jupyter/runtime/nbserver-1170-open.html
    Or copy and paste one of these URLs:
        http://172.31.99.111:8888/?token=c36b6ef9dc40a49e25e5b4c8cc1653e098f7ee72e23dc1e6
     or http://127.0.0.1:8888/?token=c36b6ef9dc40a49e25e5b4c8cc1653e098f7ee72e23dc1e6
</code></pre>

주피터 노트북이 실행된 다음에는 PC에서 웹브라우저를 열어서 라즈베리파이에서 실행되고 있는 주피터 노트북에 접속을 합니다.   
PC웹브라우저 URL 창에 아래와 같이 입력을 합니다. 
<pre><code>
 http://172.31.99.111:8888/?token=c36b6ef9dc40a49e25e5b4c8cc1653e098f7ee72e23dc1e6
</code></pre>
위 URL이 입력되면 PC 웹브라우저 페이지에 다음과 같이 라즈베리파이 deeptcar 폴더의 파일들이 보입니다. 여기서 "car_image_angle.zip" 파일을 선택하고 다운로드 하면 PC로 다운로드가 됩니다.    
![image](https://user-images.githubusercontent.com/76054530/126255147-17637578-1075-4e70-bf5d-505f224585f7.png)
   
### PC에 deeptcar용 아나콘다 가상환경을 구성합니다. 
CNN 딥러닝 트레이닝을 실행하려면 여러가지 라이브러리를 설치해야 합니다. 이 과정이 복잡한 편이어서 미리 만들어진 파이썬용 아나콘다 가상환경을 사용합니다. 

#### 아나콘다 다운로드 및 설치
아나콘다로 가상환경을 사용하기 위해서 PC에 아나콘다가 설치되어 있지 않다면 아나코다를 설치합니다. 아나콘다를 설치하는 방법은 아래의 URL을 참고하면 됩니다.    
   
[아나콘다 윈도 설치](https://docs.anaconda.com/anaconda/install/windows/)
 
#### deeptCar용 아나콘다 가상환경 다운로드 
아나콘다가 PC에 잘 설치가 되었으면 deeptcar 트레이닝용 가상환경을 다운로드 받습니다.    
<pre><code>
C:\Users\user\Downloads>git clone https://github.com/cobit-git/deeptcar-tf-PC.git
Cloning into 'deeptcar-tf-PC'...
remote: Enumerating objects: 617, done.
remote: Counting objects: 100% (617/617), done.
remote: Compressing objects: 100% (608/608), done.
remote: Total 617 (delta 12), reused 606 (delta 8), pack-reused 0R
Receiving objects: 100% (617/617), 51.12 MiB | 22.53 MiB/s, done.
Resolving deltas: 100% (12/12), done.

C:\Users\user\Downloads>
</code></pre>

#### YML 파일을 이용한 deeptCar용 아나콘다 가상환경 설치 
deeptCar 아나코다 가상환경을 다운로드 했으면, YML 파일을 이용하여 가상환경을 설치합니다. 다운로드 받은 deeptCar용 아나콘다 가상화경에 보면 "cobit-tensor-env.yml"이라는 파일이 있습니다. 이 YML 환경파일을 이용해서 deeptCar용 아나콘다 가상환경을 만들 수 있습니다.
아나콘다에서 "Ananconda PowerShell Prompt"를 실행합니다. 
![image](https://user-images.githubusercontent.com/76054530/126259373-2343277b-3438-4770-b5e8-a5dc66d3f5de.png)
그러면 다음과 같은 윈도 파워쉘 기반의 프롬프트윈도가 열립니다. 
![image](https://user-images.githubusercontent.com/76054530/126259745-43d96931-6e75-480d-9c43-bbf60b510dca.png)
이 프롬프트에서 다음과 같이 명령을 입력해서 현재 만들어진 가상환경을 확인합니다. 
   
<pre><code>
(base) PS C:\Users\user> conda env list
# conda environments:
#

base                  *  C:\Users\user\anaconda3

(base) PS C:\Users\user>
</code></pre>
   
아나콘다를 처움 설치하고 가상환경을 만들지 않았다면 "base" 가상환경만 존재 합니다. deeptCar용 가상환경을 만들기 전에 다은로드 받은 deeptCar용 아나콘다 가상환경 소스코드 폴더로 이동합니다.   그리고 "ls" 명령을 입력해서 deeptCar용 아나콘다 가상환경 파일들을 확인합니다. 

<pre><code>
(base) PS C:\Users\user\Downloads> cd .\deeptcar-tf-PC\
(base) PS C:\Users\user\Downloads\deeptcar-tf-PC> ls


    디렉터리: C:\Users\user\Downloads\deeptcar-tf-PC


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2021-07-20  오후 12:14                data
d-----      2021-07-20  오후 12:14                docs
d-----      2021-07-20  오후 12:14                output
d-----      2021-07-20  오후 12:14                sphinx-gen-doc
d-----      2021-07-20  오후 12:14                __pycache__
-a----      2021-07-20  오후 12:14           2206 cobit-tensor-env.yml
-a----      2021-07-20  오후 12:14           5715 cobitlab.yml
-a----      2021-07-20  오후 12:14           8744 cobit_deep_learning.py
-a----      2021-07-20  오후 12:14            171 README.md


(base) PS C:\Users\user\Downloads\deeptcar-tf-PC>
</code></pre>

이 중에서 "cobit-tensor-env.yml" 환경파일을 이용해서 deeptCar용 아나콘다 가상환경을 만들게 됩니다. YML 환경파일을 확인 했으면 다음과 같이 명령을 입력합니다. 
<pre><code>
(base) PS C:\Users\user\Downloads\deeptcar-tf-PC> conda env create --file cobitlab
</code></pre>

4분 정도 지나고 다음과 같은 메시지가 프롬프트 윈도에 나타나면 가상환경 설치가 완료된 것입니다. 설치된 가상환경의 이름은 자동으로 "cobitlab_win"으로 만들어 집니다. 
<pre><code>
done
#
# To activate this environment, use
#
#     $ conda activate cobitlab_win
#
# To deactivate an active environment, use
#
#     $ conda deactivate

(base) PS C:\Users\user\Downloads\deeptcar-tf-PC>
</code></pre>   

"cobitlab_win" 가상환경의 설치가 완료된 후, 다음과 같은 명령을 통해 가상환경을 활성화 합니다. 

<pre><code>   
(base) PS C:\Users\user\Downloads\deeptcar-tf-PC> conda activate cobitlab_win
(cobitlab_win) PS C:\Users\user\Downloads\deeptcar-tf-PC>
</code></pre>   

### CNN 딥러닝 트레이닝 실행 




   












