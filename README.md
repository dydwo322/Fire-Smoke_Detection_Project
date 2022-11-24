# Fire & Smoke Detection Project(Object Detection)

## 1.주제 선정
### ○ 프로젝트 주제 
- 연기감지를 통한 화재 예측 AI 경보시스템 구축<br> 

<img width="700"  src="https://user-images.githubusercontent.com/79880476/203837688-2f6c379e-0c87-49ab-a9fd-215854ca803e.jpg">

### ○ 프로젝트 기획의도 
- 매 해 반복되는 화재사고. 기존 화재감시 및 경보 시스템의 허점 대두

<img width="700"  src="https://user-images.githubusercontent.com/79880476/203837682-aa75530f-3078-4139-ac83-6471e5065e61.jpg">

### ○ 프로젝트 기간
- 2022.08.19. ~ 2022.09.02.


### ○ 프로젝트 목적
- 화재 발생 주요징후인 연기와 불꽃을 인식 가능하도록 모델을 학습 <br>
- 화재 예측 AI 기술 개발용 데이터셋 처리 및 학습기준 사전 확보 및 경험 공유<br>

### ○ 프로젝트 기대효과
- CCTV를 통해 불씨와 연기를 인식하여 자동으로 화재 예방
- 실제 화재 예측 AI 서비스 개발시 데이터셋 학습 시행착오 경감
- 화재사고 사전 예방을 통한 인명피해 및 재산피해 경감에 기여
<br>

## 2.데이터 수집
### ○ 데이터셋
- AI Hub 화재발생 예측 영상 데이터셋 (이미지 173만장, Bbox 199만개, Polygon 26만개) 中 Vaildation의 data를 Train의 data로 사용하여 학습시킴 (약 56,000여장)<br>
<div align=center>
  <img width="1200"  src="https://user-images.githubusercontent.com/79880476/203839675-a9d5f380-ae54-49e9-af2e-729c58e2d0fd.jpg"><br>
  <a>AI HUB 데이터 량</a>
</div>
<br>
<table width="600" style="text-align: center;">
  <tr align=center>
    <td><img src="https://user-images.githubusercontent.com/79880476/203839682-a429db74-7a74-422f-9a04-80ad35a0e2c8.jpg" ></td>
    <td><img src="https://user-images.githubusercontent.com/79880476/203839668-39833364-f878-434c-9e6f-ab7ba5c27fc5.jpg" ></td>
  </tr>
  <tr align=center>
    <td><a>데이터 정보</a></td>
    <td><a>데이터의 라벨</a></td>
  </tr>
</table>

## 3.데이터 전처리
### ○ 리사이즈(224X224,416X416,608X608)후 패딩 처리
<table style="text-align: center;">
  <tr align=center>
    <td><img src="https://user-images.githubusercontent.com/79880476/203842479-95ca0266-442c-4d22-a345-a49ba34825cf.jpg" ></td>
  </tr>
</table>

### ○ 폴리곤 좌표 → Bbox 좌표로 변환 / 상대좌표 → 절대좌표 전환
<table style="text-align: center;">
  <tr align=center>
    <td><img src="https://user-images.githubusercontent.com/79880476/203842490-bde17b46-0a99-4eef-8d99-6a9411b0ce28.jpg" ></td>
  </tr>
</table>
<br>

## 4.모델 선정
### ○ YOLO v4 - CSPDarknet53을 Backbone으로 사용하여 실시간 객체인식 성능이 우수함
<img width="800"  src="https://user-images.githubusercontent.com/79880476/203839698-9d1cce01-933a-48db-b405-0518cb55cb93.jpg"><br>

## 5.모델 성능 평가
### ○ 이미지 리사이즈별 성능 확인 (224X224, 416X416, 608X608)
<table style="text-align: center;">
  <tr align=center>
    <td><img src="https://user-images.githubusercontent.com/79880476/203845376-89d96aa8-665b-4ec3-b77c-d643f0cb210e.jpg" ></td>
  </tr>
</table>

### ○ ignore_thresh 설정 (max_batches = 22000 → 5500변경)
<table style="text-align: center;">
  <tr align=center>
    <td><img src="https://user-images.githubusercontent.com/79880476/203844482-7be7425c-29f9-4927-97fd-3984e22999ea.jpg" ></td>
  </tr>
</table>

### ○ IoU_thresh 설정
<table style="text-align: center;">
  <tr align=center>
    <td><img src="https://user-images.githubusercontent.com/79880476/203844474-c754ec1e-ecca-46f9-963e-a1cf966ac6c1.jpg" ></td>
  </tr>
</table>
<br>

## 6.결과

## 7.자체 평가 의견

