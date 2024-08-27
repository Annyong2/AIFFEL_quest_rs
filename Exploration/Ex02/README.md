# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 담안용
- 리뷰어 : 윤철희


# PRT(Peer Review Template)
- [O]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**



      기승전결 EDA -> 전처리 -> 모델학습 -> 예측 캐글 submission)을 구현했는가 ? 

    ![image](https://github.com/user-attachments/assets/02806a0d-9423-4fb5-aff1-52cf4d09edb2)
        
        EDA 과정에서 데이터의 feature들을 시각화를 통해 분포 형태를 알 수 있었고



   ![image](https://github.com/user-attachments/assets/0b584e73-3200-449a-b2e0-b311fbf66301)


      log1p을 사용해서 데이터의 분포가 어떻게 나타나는지 알 수 있었습니다.

    
      
    ![image](https://github.com/user-attachments/assets/f0115834-5b62-462b-89ea-cb72d97ed2f7)
    
    ![image](https://github.com/user-attachments/assets/e81947e2-4e48-4f10-a9a8-af0e85cfa824)

      학습 데이터만 정규 분포 형태로 맞추지 않고 Target data도 정규 분포 형태로 잘 맞추어서 데이터 EDA,전처리 부분은 잘 되어 있었습니다.


    Model GradientBoosting CV score : 0.8597
    Model XGBoost CV score : 0.8861
    Model LightGBM CV score : 0.8819

    k-fold validation으로 모델의 score을 잘 볼 수 있었습니다.
    
              # 사용함수 GridSearchCV
            def my_GridSearch(model, train, y, param_grid, verbose=2, n_jobs=5):
            # GridSearchCV 모델로 초기화
            grid_model = GridSearchCV(model, param_grid=param_grid, scoring='neg_mean_squared_error', \
                                      cv=5, verbose=verbose, n_jobs=n_jobs)
            
            # 모델 fitting
            grid_model.fit(train, y)
        
            # 결과값 저장
            params = grid_model.cv_results_['params']
            score = grid_model.cv_results_['mean_test_score']
            
            # 데이터 프레임 생성
            results = pd.DataFrame(params)
            results['score'] = score
            
            # RMSLE 값 계산 후 정렬
            results['RMSLE'] = np.sqrt(-1 * results['score'])
            results = results.sort_values('RMSLE')
        
            return results
        param_grid = {
            'n_estimators': [50, 100],
            'max_depth': [1, 10],
        }
        model = LGBMRegressor(random_state=random_state)


        마지막 submission.csv 파일까지 github에 올려 주셔서 쉽게 확인이 가능했습니다.

      

        
          
        
            
- [ O]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**

    Cross Validation
          교차 검증을 통해 모델의 성능을 간단히 평가하겠습니다.
        cross_val_score 평가 함수 사용.(해당 함수 회귀문제에서는 "R^2 score"사용)
            get_cv_score 함수 내부:
            models는 여러 모델을 포함한 리스트로 보입니다. 각 모델에 대해 교차 검증을 수행합니다.
           KFold는 데이터를 5개의 폴드로 나누어 교차 검증을 수행하며, 각 폴드에서 모델이 훈련되고 평가됩니다.
            cross_val_score가 수행된 후 np.mean()을 통해 각 폴드에서 계산된 점수들의 평균을 출력합니다.
            그러나 현재 함수에서 scoring 매개변수를 지정하지 않았기 때문에, 기본 설정(R^2 score)에 따라 점수가 계산됩니다.

          scoring 매개변수를 지정하지 않아서 R^2 score를 사용한 부분을 주석을 통해 쉽게 알 수 있었습니다. 

        
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 해결한 기록을 남겼거나
새로운 시도 또는 추가 실험을 수행해봤나요?**

    IndexError                                Traceback (most recent call last)
    /tmp/ipykernel_33/3261939851.py in <module>
      5 for row in range(3):
      6     for col in range(2):
----> 7         sns.kdeplot(data=data[columns[count]], ax=ax[row][col])
      8         ax[row][col].set_title(columns[count], fontsize=15)
      9         count += 1

    IndexError: list index out of range
        list index out of range 수정 필요 -> count =5 로 바꾸시면 될거에요

- [ ]  **4. 회고를 잘 작성했나요?**
      
        코드 설명 하실 때 말로 설명 들었습니다. -> 이번 과정의 목표는 실습 단계를 한 단계 거쳐 가시는게 목적이라고 하셨습니다. 
       

- [O]  **5. 코드가 간결하고 효율적인가요?**
           models = [{'model':gboost, 'name':'GradientBoosting'}, {'model':xgboost, 'name':'XGBoost'},
          {'model':lightgbm, 'name':'LightGBM'}]
      
          # 사용함수 GridSearchCV
        def my_GridSearch(model, train, y, param_grid, verbose=2, n_jobs=5):
            # GridSearchCV 모델로 초기화
            grid_model = GridSearchCV(model, param_grid=param_grid, scoring='neg_mean_squared_error', \
                                      cv=5, verbose=verbose, n_jobs=n_jobs)
        
        # 모델 fitting
        grid_model.fit(train, y)
    
        # 결과값 저장
        params = grid_model.cv_results_['params']
        score = grid_model.cv_results_['mean_test_score']
        
        # 데이터 프레임 생성
        results = pd.DataFrame(params)
        results['score'] = score
        
        # RMSLE 값 계산 후 정렬
        results['RMSLE'] = np.sqrt(-1 * results['score'])
        results = results.sort_values('RMSLE')

    return results

      반복적인 작업들을 function 형태로 간소화 잘 하신거 같습니다. 

    

# 회고(참고 링크 및 코드 개선)

 단순히 k-fold를 사용하는게 아니라 그 함수의 score 처리를 어떻게 하는지 깊게 분석하신 것 같습니다.
 
 그래프에서 오류여서 상관 없지만 list out of bound 치명적인 오류에요 과정을 다 한번 거치는 것도 좋지만 Error 부분도 관심 있게 봐주세요
 
 사실 어느정도 깊이를 원하시는지 잘 몰라서 제가 생각했을 때 저러면 좀 더 높게 나올거 같은 경우에만 공유했습니다. 
