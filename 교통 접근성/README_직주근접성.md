## 직주 근접성

<details>
<summary>Data Preprocessing</summary>
<div>

- 활용 데이터
    -  100대 기업 (24년 기준) 회사명 및 도로명 주소 데이터
    -  2024.10월 기준 아파트 실거래가 데이터
    -  전국 지하철 역 위치 데이터
      
- 진행방식
    - 100대 기업 (24년 기준) 회사명 및 도로명 주소 데이터 
      - 서울시에 위치한 회사로 1차 필터링
      - 1차 필터링된 회사 기반, 구별로 순위 설정
      - 1~5위에 해당하는 구의 회사들로 2차 필터링
      - 필터링된 회사들의 도로명 주소 기반 위도-경도 데이터 수집 (API 및 라이브러리 이용)
      - 구별로 회사들 Grouping 후, `위도-경도 기반 회사들 간 중간지점` 도출
     
    - 2024.10월 기준 아파트 실거래가 데이터, 전국 지하철 역 위치 데이터
      - 분당 및 일산 신도시에 위치하는 아파트 및 지하철 역 데이터 1차 필터링
      - 필터링된 데이터들에 대해 위도-경도 데이터 수집 (API 및 라이브러리 이용)
      - haversine을 활용한 지하철 역과 아파트 간 `직선거리` 도출 후, 역 별 최소 거리 3순위에 속하는 아파트들 2차 필터링
      - 필터링된 아파트 - `위도-경도 기반 회사들 간 중간지점` 간 직선거리 도출
      - 필터링된 아파트 - `위도-경도 기반 회사들 간 중간지점` 간 KAKAO Mobility API를 활용한 평일 미래운행정보 (241202~241206) 시간대별 수집
      - 수집된 미래운행정보 데이터 내 소요시간 및 이동 거리 도출 후 평균

- 원시 데이터 테이블 예시 (Filtering 후 67개 기업)

    | Name         | Address                                       | Latitude       | Longitude       |
    |--------------|-----------------------------------------------|----------------|-----------------|
    | LG에너지솔루션 | 서울특별시 영등포구 여의대로 108 (여의도동)         | 37.5251913154781 | 126.929112756574 |
    | LG화학        | 서울특별시 영등포구 여의대로 128                  | 37.5279271045092 | 126.929241174348 |

</div>
</details>


- 서울시 구별 등록된 회사 수
    ![seoul_company_count](https://github.com/user-attachments/assets/146cea31-3a44-4888-80e4-7dbee472c47b)

- 분당/일산 최단 직선거리 기준 시각화
    ![shortest_result_map_cropped](https://github.com/user-attachments/assets/6f8cd8fd-017e-4dde-9466-18e5a96f0a11)

- 분당/일산 최단 직선거리 기준 자차 운행 소요거리(km) - 시간
    ![image](https://github.com/user-attachments/assets/5b250fff-66bb-443d-a581-508d08ccc4b2)
    ![image](https://github.com/user-attachments/assets/00561b82-ba6e-473b-a9b1-64e34297efe4)


- 분당/일산 최장 직선거리 기준 시각화
    ![longest_result_map_cropped](https://github.com/user-attachments/assets/b018adf8-3c5d-4177-9309-d8ab415a190e)

- 분당/일산 최장 직선거리 기준 자차 운행 소요거리(km) - 시간
    ![image](https://github.com/user-attachments/assets/d004f877-587d-4c8d-a3a4-f584a6b7d460)
    ![image](https://github.com/user-attachments/assets/9a98dcad-b165-49ab-aacc-3054c0ee5249)

</body>
</html>




