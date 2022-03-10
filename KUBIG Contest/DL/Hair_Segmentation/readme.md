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
 
 ## 2.
 
 
