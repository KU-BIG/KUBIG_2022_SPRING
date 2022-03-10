# 헤어 세그멘테이션

## 데이터셋 소개


 -input: 헤어스타일 이미지 (512x512)  
 -output: 헤어 부분에 대한 polygon 좌표
 
 ## 데이터 구성
 - Train:  
  --- `images/` : jpg 파일 39211장  
  --- `labels.json` : 이미지의 파일명, 폴리곤 좌표(polygon)이 담긴 딕셔너리
 - Test:   
  --- `images/` : jpg 파일 2456장

 ## 1. mask 생성
 
 labels.json 파일의 polygon 좌표를 binary mask 이미지로 변환하는 함수  
 
 ## 2. model 생성
 
 ### -FCN: 분류에서 성능을 검증 받은 기존의 네트워크 기반
accuracy가 높았으나 loss가 제대로 계산이 되지않아 확인해보니 mask 데이터가 정상적으로 적용되지 못하는 문제 확인.  

### -UNet: Biomedical 분야에서 이미지 분할(Image Segmentation)을 목적으로 제안된 End-to-End 방식의 Fully-Convolutional Network 기반 모델 


## 3. 시도

1. 데이터 수가 너무 많아서 학습에 사용할 사진의 수를 1k, 3k, 5k로 나눠서 실험  
2. learning rate, batch size, epoch 바꿔서 실험  
3. flip, rotate, elastic transformation 등 data augmentation 적용  
4. loss는 cross entropy, optimizier는 Adam 사용
 
## 4. 결과

learning rate=0.01 ,epoch=7, elastic transform, motion blir, gauss noise, random contrasst augmentation 적용한 모델이 가장 loss 값이 작게 나왔음.
