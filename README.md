import numpy as np
from multiprocessing import Pool
from matplotlib import pyplot as plt

if __name__ == '__main__':  ### __name__이라는 변수값이 __main__이라면 아래의 코드를 실행
    N = 10000 ### 무작위시행 횟수 정의, N회 시행
    x = np.random.random([N, 2])  ### random() 함수: 0.0이상 1.0 미만의 (실수)난수를 생성
    distance = np.sum(x ** 2.0, axis=1)
    in_out = distance <= 1.0
    pi = np.sum(in_out)*4/N ### Pi 값은 천제 시행에서 원 안에 있는 점의 갯수로 정해짐
    color = list(map(lambda x: 'red' if x else 'blue', in_out)) ### 원의 안, 밖에 따른 색상 설정

    plt.figure(figsize=(5, 5)) ### 그림 사이즈 5x5
    plt.scatter(x[:,0], x[:,1], color = color, s=5, label ='Result : {}'.format(np.round(pi, 4))) ###plt.scatter: 정해진 범위 내에 산점도 그리기
    
    cx = np.cos(np.linspace(0, np.pi/2, 1000))
    cy = np.sin(np.linspace(0, np.pi/2, 1000))
    plt.plot(cx, cy, color = 'black', lw =2) ### 원의 경계를 그려주는 부분
    plt.legend(loc = 'upper right') ### 오른쪽 하단에 범례 표시

    plt.xlim(0, 1) ### x축을 0에서 1까지 고정
    plt.ylim(0, 1) ### y축을 0에서 1까지 고정
    plt.show() ### 그래프를 출력
