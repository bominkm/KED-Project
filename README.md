# 디지털 산업혁신 빅데이터 플랫폼 공모전
## [분석] 사업목적을 활용한 업종코드 예측


|대회|기간|수행내용|결과|
|----|----|-----------|-------|
|예선|21.04.09 ~ 21.05.23|사업목적을 활용한 업종코드 예측|본선 진출|
|본선|21.06.12|프레젠테이션|우수상(2위)|

<br>


## 📌 Techniques
**NLP**       

<br>


## 📌 Process

### 1. Tokenizer - Mecab    

- 다음과 같이 git-clone하여 사용하실 수 있습니다.         

      %cd /content/
      !git clone https://github.com/SOMJANG/Mecab-ko-for-Google-Colab.git
      %cd Mecab-ko-for-Google-Colab
      ! bash install_mecab-ko_on_colab190912.sh

### 2. Embedding - Fasttext   
 
- 위키피디아 pretrain model 사용하였습니다.


### 3. Modeling - BILSTM    

- 단어 구성에 주목할 수 있는 양방향 순환신경망 고려한 모델을 적용하였습니다.
  
      def build_model():
        model = tf.keras.Sequential()
        model.add(tf.keras.layers.Bidirectional(tf.keras.layers.LSTM(128, return_sequences=True), input_shape=(None, n_features)))
        model.add(tf.keras.layers.Bidirectional(tf.keras.layers.LSTM(128)))
        model.add(tf.keras.layers.Dense(100, kernel_initializer= 'he_normal', activation='relu'))
        model.add(tf.keras.layers.Dropout(0.3))
        model.add(tf.keras.layers.Dense(19, activation='softmax'))    
        return model      


<br>

## 📌 실행 환경

- Tensorflow **2.4.0** 버전에서 작성되었습니다. 
- colab pro 환경에서 작성되었습니다. 


