# Sel Taşkını Tahmin Projesi

Bu proje, sel olaylarını makine öğrenmesi teknikleri kullanarak tahmin etmeyi amaçlamaktadır. Veri seti, yağış miktarı, sıcaklık ve nem gibi çeşitli çevresel parametreleri içermektedir. Proje, sel olaylarını tahmin etmek için farklı modelleri kullanmakta ve bu modellerin performansını karşılaştırmaktadır. Bu çalışma, bir Kaggle yarışmasında gerçekleştirilmiş olup, doğruluk oranı %86.379 olarak elde edilmiştir.

<a href="https://www.kaggle.com/code/mevltbaaran/flood-prediction" target="_blank|_top">Kaggle Proje Sayfası</a>


## İçindekiler
1. [Giriş](#giriş)
2. [Veri Seti Tanımı](#veri-seti-tanımı)
3. [Veri Ön İşleme](#veri-ön-işleme)
4. [Model Eğitimi](#model-eğitimi)
5. [Sonuç](#sonuç)
6. [Gelecek Çalışmalar](#gelecek-çalışmalar)
7. [Kaynaklar](#kaynaklar)

## Giriş

Bu projede, sel olaylarını tahmin etmek için çeşitli makine öğrenmesi modelleri kullanılmıştır. Bu modellerin performans değerlendirmesi Kaggle tarafından yapılmış olup, yarışma sıralaması için doğruluk oranı %86.379 olarak elde edilmiştir.

## Veri Seti Tanımı

Veri seti, çeşitli kaynaklardan toplanan ve sel tahminine yardımcı olabilecek yağış miktarı, sıcaklık ve nem gibi çevresel parametreleri içermektedir. Bu veriler, sel olaylarının gerçekleşme olasılığını belirlemek için kullanılmıştır.
```
import pandas as pd

# Veri setini yükleme
data = pd.read_csv('dataset.csv')

# Eksik verileri tamamlama
data.fillna(method='ffill', inplace=True)
```

## Veri Ön İşleme

Veri setindeki eksik ve tutarsız veriler temizlenmiş ve ölçeklendirilmiştir. Bu aşama, modellerin daha doğru sonuçlar vermesi için oldukça önemlidir.

```
from sklearn.preprocessing import StandardScaler

# Verileri ölçeklendirme
scaler = StandardScaler()
scaled_data = scaler.fit_transform(data)

```

## Model Eğitimi

Projede kullanılan model:
- Yapay Sinir Ağları

```
import numpy as np
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

# Model oluşturma
model = Sequential()
model.add(Dense(64, input_dim=scaled_data.shape[1], activation='relu'import numpy as np
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

# Model oluşturma
model = Sequential()
model.add(Dense(64, input_dim=scaled_data.shape[1], activation='relu'))
model.add(Dense(32, activation='relu'))
model.add(Dense(1, activation='sigmoid'))

# Modeli derleme
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy', 'mae'])

# Modeli eğitme
history = model.fit(X_train, y_train, epochs=100, batch_size=32, validation_data=(X_test, y_test))
))
model.add(Dense(32, activation='relu'))
model.add(Dense(1, activation='sigmoid'))

# Modeli derleme
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy', 'mae'])

# Modeli eğitme
history = model.fit(X_train, y_train, epochs=100, batch_size=32, validation_data=(X_test, y_test))

```
## Sonuç

Yapay Sinir Ağları modeli, sel tahmininde iyi bir performans göstermiştir. Kaggle yarışmasında %86.379 doğruluk oranı elde edilmiştir. Gelecekte daha büyük veri setleri ve daha gelişmiş modeller kullanarak tahmin doğruluğunu artırmayı planlıyoruz.

## Gelecek Çalışmalar

- Veri setinin genişletilmesi
- Daha gelişmiş modellerin kullanılması


---
<a href="https://www.kaggle.com/code/mevltbaaran/flood-prediction" target="_blank|_top">Kaggle Proje Sayfası</a>

