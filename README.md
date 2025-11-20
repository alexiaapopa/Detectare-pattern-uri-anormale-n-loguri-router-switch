2. Descrierea Setului de Date

2.1 Sursa datelor

Origine: loguri simulate de routere și switch-uri

Modul de achiziție: ☑ Generare programatică

Perioada / condițiile colectării: simulare locală pe calculator, 2500 loguri generate, timestamp variabil

2.2 Caracteristicile dataset-ului

Număr total de observații: 2500

Număr de caracteristici (features): 5

Tipuri de date: ☑ Numerice / ☑ Categoriale / ☑ Temporale

Format fișiere: ☑ CSV

2.3 Descrierea fiecărei caracteristici
Caracteristică	Tip	Unitate	Descriere	Domeniu valori
timestamp	temporal	–	Timpul la care a fost generat logul	Datetime (ex: 2025-11-20 12:30:45)
device	categorial	–	Numele dispozitivului (router/switch)	{R1, R2, SW1, SW2}
severity	numeric	–	Nivel de severitate log	0–7
message	text	–	Mesaj log (normal sau anomalie)	Text liber
label	numeric	–	Clasificare normal (0) / anomalie (1)	{0,1}

Fișier recomandat: data/README.md

3. Analiza Exploratorie a Datelor (EDA) – Sintetic
3.1 Statistici descriptive aplicate

Medie, mediană, deviație standard pentru severity și anomaly_score

Min–max și quartile pentru severity

Distribuții pe caracteristici (histograme pentru severitate și label)

Identificarea outlierilor prin scorul modelului de anomalie

3.2 Analiza calității datelor

Nu există valori lipsă

Toate datele sunt consistente și coerente

Clasele sunt ușor dezechilibrate: ~18% anomalii, 82% normal

3.3 Probleme identificate

Distribuția label-ului este ușor neuniformă (anomalie ~18%)

4. Preprocesarea Datelor
4.1 Curățarea datelor

Eliminare duplicate (dacă există)

Curățare text mesaje (regex, lowercase, spații multiple)

Nicio valoare lipsă, nu se aplică imputare

4.2 Transformarea caracteristicilor

Normalizare pentru severity (StandardScaler)

Vectorizare TF-IDF pentru message

Label binar pentru anomalie (0/1)

4.3 Structurarea seturilor de date

Împărțire recomandată: 70% train, 15% validation, 15% test

Stratificare după label pentru menținerea proporției anomalii/normal

Statisticile de normalizare calculate doar pe setul de train și aplicate pe validation/test

4.4 Salvarea rezultatelor preprocesării

Date preprocesate în data/processed/

Seturi train/validation/test în foldere dedicate

Parametrii de preprocesare în config/preprocessing_config.* (opțional)

5. Fișiere Generate în Această Etapă

data/raw/generated_logs.csv – date brute generate programatic

data/processed/predicted_logs.csv – date cu predicții și scor anomalie

data/processed/anomaly_timeline.png – grafic timeline cu anomalii

src/data_acquisition/ – codul de generare loguri

src/preprocessing/ – cod pentru curățare și vectorizare

6. Stare Etapă (de completat de student)

 Structură repository configurată

 Dataset analizat (EDA realizată)

 Date preprocesate

 Seturi train/val/test generate

 Documentație actualizată în README + data/README.md
