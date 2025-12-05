# RESUMEN COMPLETO DEL ANÁLISIS DE DATOS - WINE QUALITY (WHITE WINE)

1. INFORMACIÓN DEL DATASET
--------------------------------------------------------------------------------
   - Nombre: Wine Quality - White Wine
   - Fuente: UCI Machine Learning Repository
   - Dimensiones: 4,898 registros x 14 columnas
   - Variables continuas: 11
   - Variable objetivo: quality (valores 3 a 9)
   - Registros duplicados: 937

2. CALIDAD DE LOS DATOS
--------------------------------------------------------------------------------
   - Valores faltantes: 0 (0.0000%)
   - Total de outliers (IQR): 1,063
   - Variables con más outliers: citric acid, chlorides, volatile acidity

3. DISTRIBUCIÓN DE LA VARIABLE OBJETIVO
--------------------------------------------------------------------------------
   Calidad  Frecuencia  Porcentaje (%)  Acumulado (%)
0        3          20          0.4100         0.4100
1        4         163          3.3300         3.7400
2        5        1457         29.7500        33.4900
3        6        2198         44.8800        78.3700
4        7         880         17.9700        96.3400
5        8         175          3.5700        99.9100
6        9           5          0.1000       100.0100

   Categorías:
   - Baja (3-4): 183 (3.74%)
   - Media (5-6): 3655 (74.62%)
   - Alta (7-9): 1060 (21.64%)

4. ESTADÍSTICAS DESCRIPTIVAS
--------------------------------------------------------------------------------
                         mean     std    min      max  mediana  asimetria  curtosis
fixed acidity          6.8548  0.8439 3.8000  14.2000   6.8000     0.6478    2.1722
volatile acidity       0.2782  0.1008 0.0800   1.1000   0.2600     1.5770    5.0916
citric acid            0.3342  0.1210 0.0000   1.6600   0.3200     1.2819    6.1749
residual sugar         6.3914  5.0721 0.6000  65.8000   5.2000     1.0771    3.4698
chlorides              0.0458  0.0218 0.0090   0.3460   0.0430     5.0233   37.5646
free sulfur dioxide   35.3081 17.0071 2.0000 289.0000  34.0000     1.4067   11.4663
total sulfur dioxide 138.3607 42.4981 9.0000 440.0000 134.0000     0.3907    0.5719
density                0.9940  0.0030 0.9871   1.0390   0.9937     0.9778    9.7938
pH                     3.1883  0.1510 2.7200   3.8200   3.1800     0.4578    0.5308
sulphates              0.4898  0.1141 0.2200   1.0800   0.4700     0.9772    1.5909
alcohol               10.5143  1.2306 8.0000  14.2000  10.4000     0.4873   -0.6984
quality                5.8779  0.8856 3.0000   9.0000   6.0000     0.1558    0.2165

5. TESTS DE NORMALIDAD
--------------------------------------------------------------------------------
                Variable  Shapiro-Wilk (p)  D'Agostino (p) Normal
0          fixed acidity            0.0000          0.0000     No
1       volatile acidity            0.0000          0.0000     No
2            citric acid            0.0000          0.0000     No
3         residual sugar            0.0000          0.0000     No
4              chlorides            0.0000          0.0000     No
5    free sulfur dioxide            0.0000          0.0000     No
6   total sulfur dioxide            0.0000          0.0000     No
7                density            0.0000          0.0000     No
8                     pH            0.0000          0.0000     No
9              sulphates            0.0000          0.0000     No
10               alcohol            0.0000          0.0000     No

6. ANÁLISIS DE CORRELACIONES
--------------------------------------------------------------------------------
   TOP 10 CORRELACIONES MÁS FUERTES:
              Variable 1            Variable 2  Correlación  |Correlación|
1         residual sugar               density       0.8390         0.8390
2                density               alcohol      -0.7801         0.7801
3    free sulfur dioxide  total sulfur dioxide       0.6155         0.6155
4   total sulfur dioxide               density       0.5299         0.5299
5         residual sugar               alcohol      -0.4506         0.4506
6   total sulfur dioxide               alcohol      -0.4489         0.4489
7                alcohol               quality       0.4356         0.4356
8          fixed acidity                    pH      -0.4259         0.4259
9         residual sugar  total sulfur dioxide       0.4014         0.4014
10             chlorides               alcohol      -0.3602         0.3602

   CORRELACIONES CON CALIDAD:
                Variable  Pearson  Spearman
1                alcohol   0.4356    0.4404
2                density  -0.3071   -0.3484
3              chlorides  -0.2099   -0.3145
4       volatile acidity  -0.1947   -0.1966
5   total sulfur dioxide  -0.1747   -0.1967
6          fixed acidity  -0.1137   -0.0845
7                     pH   0.0994    0.1094
8         residual sugar  -0.0976   -0.0821
9              sulphates   0.0537    0.0333
10           citric acid  -0.0092    0.0183
11   free sulfur dioxide   0.0082    0.0237

7. TESTS ESTADÍSTICOS (DIFERENCIAS ENTRE GRUPOS DE CALIDAD)
--------------------------------------------------------------------------------
                Variable  ANOVA (F)  ANOVA (p)  Kruskal (H)  Kruskal (p) Significativo
0          fixed acidity    12.8948     0.0000      40.8677       0.0000            Sí
1       volatile acidity    61.9167     0.0000     286.1334       0.0000            Sí
2            citric acid     3.2457     0.0035      13.1197       0.0412            Sí
3         residual sugar    21.2703     0.0000      94.5187       0.0000            Sí
4              chlorides    42.4723     0.0000     512.9901       0.0000            Sí
5    free sulfur dioxide    19.7237     0.0000     115.0662       0.0000            Sí
6   total sulfur dioxide    45.2009     0.0000     266.6681       0.0000            Sí
7                density   105.8564     0.0000     652.6084       0.0000            Sí
8                     pH    10.1033     0.0000      65.4727       0.0000            Sí
9              sulphates     3.6423     0.0013      13.7802       0.0322            Sí
10               alcohol   229.7348     0.0000    1014.0723       0.0000            Sí

   Variables con diferencias significativas (Kruskal-Wallis, p<0.05):
   fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulphates, alcohol

8. ANÁLISIS DE COMPONENTES PRINCIPALES (PCA)
--------------------------------------------------------------------------------
   - Componentes para 80% de varianza: 6
   - Componentes para 95% de varianza: 9
   - Varianza del primer componente: 29.29%
   - Varianza de los primeros 3 componentes: 54.72%

   Loadings PC1:
density                 0.5115
alcohol                -0.4372
residual sugar          0.4274
total sulfur dioxide    0.4067
free sulfur dioxide     0.3003
chlorides               0.2120
fixed acidity           0.1572
citric acid             0.1440
pH                     -0.1288
sulphates               0.0434
volatile acidity        0.0051

9. CLUSTERING
--------------------------------------------------------------------------------
   - Número de clusters óptimo (Silhouette): 2
   - Clusters utilizados: 4
   - Distribución: {0: np.int64(107), 1: np.int64(1697), 2: np.int64(1459), 3: np.int64(1635)}

   Perfil de clusters (medias):
         fixed acidity  volatile acidity  citric acid  residual sugar  chlorides  free sulfur dioxide  total sulfur dioxide  density     pH  sulphates  alcohol  quality
cluster                                                                                                                                                                 
0               6.6930            0.3170       0.4410          4.6250     0.1630              40.1640              144.0750   0.9940 3.0960     0.4640   9.5660   5.4860
1               6.9710            0.2810       0.3590         11.5030     0.0490              46.4020              173.2590   0.9970 3.1590     0.4980   9.4910   5.6160
2               7.4370            0.2730       0.3490          3.9600     0.0400              26.2580              115.4280   0.9930 3.0960     0.4520  11.0580   5.9100
3               6.2250            0.2780       0.2880          3.3710     0.0400              31.5520              122.2290   0.9920 3.3070     0.5170  11.1530   6.1470

10. RESULTADOS DE MACHINE LEARNING - CLASIFICACIÓN
--------------------------------------------------------------------------------
                Modelo  Accuracy  Precision  Recall  F1-Score  CV Mean  CV Std
1        Random Forest    0.6755     0.6840  0.6755    0.6644   0.6628  0.0109
4        Decision Tree    0.5939     0.5954  0.5939    0.5942   0.5753  0.0099
2    Gradient Boosting    0.5755     0.5798  0.5755    0.5620   0.5911  0.0169
0  Logistic Regression    0.5490     0.5314  0.5490    0.5155   0.5352  0.0091
3                  KNN    0.5265     0.5199  0.5265    0.5191   0.5424  0.0047

    Mejor modelo: Random Forest
    - Accuracy: 0.6755
    - F1-Score: 0.6644
    - Cross-Validation: 0.6628 (+/- 0.0109)

11. FEATURE IMPORTANCE (RANDOM FOREST)
--------------------------------------------------------------------------------
                Variable  Importancia  Importancia (%)
1                alcohol       0.1165          11.6547
2                density       0.1030          10.2992
3       volatile acidity       0.1005          10.0544
4    free sulfur dioxide       0.0922           9.2152
5   total sulfur dioxide       0.0908           9.0794
6                     pH       0.0866           8.6568
7              chlorides       0.0864           8.6446
8         residual sugar       0.0863           8.6262
9            citric acid       0.0818           8.1790
10             sulphates       0.0783           7.8324
11         fixed acidity       0.0776           7.7581

12. RESULTADOS DE REGRESIÓN
--------------------------------------------------------------------------------
                    Modelo    MSE   RMSE    MAE     R²
0        Linear Regression 0.5794 0.7612 0.5909 0.2619
1  Random Forest Regressor 0.3834 0.6192 0.4449 0.5116

   Coeficientes de Regresión Lineal (intercepto: 5.8780):
                Variable  Coeficiente
1                density      -0.4291
2         residual sugar       0.4034
3                alcohol       0.2508
4       volatile acidity      -0.1907
5                     pH       0.1047
6              sulphates       0.0685
7    free sulfur dioxide       0.0574
8          fixed acidity       0.0481
9            citric acid       0.0142
10             chlorides      -0.0128
11  total sulfur dioxide      -0.0015

13. COMPARACIÓN CALIDAD BAJA vs ALTA
--------------------------------------------------------------------------------
                Variable  Media (Baja)  Media (Alta)  Diferencia  Diferencia (%)
0          fixed acidity        7.1809        6.7251     -0.4557         -6.3465
1       volatile acidity        0.3760        0.2653     -0.1106        -29.4254
2            citric acid        0.3077        0.3261      0.0184          5.9641
3         residual sugar        4.8210        5.2615      0.4405          9.1364
4              chlorides        0.0506        0.0382     -0.0124        -24.5207
5    free sulfur dioxide       26.6339       34.5505      7.9166         29.7238
6   total sulfur dioxide      130.2322      125.2453     -4.9870         -3.8293
7                density        0.9943        0.9924     -0.0019         -0.1942
8                     pH        3.1834        3.2151      0.0317          0.9972
9              sulphates        0.4760        0.5001      0.0242          5.0814
10               alcohol       10.1735       11.4160      1.2425         12.2133

14. ANÁLISIS DE OUTLIERS DETALLADO
--------------------------------------------------------------------------------
                Variable       Q1       Q3     IQR  Límite Inferior  Límite Superior  Outliers (IQR)  % Outliers
0          fixed acidity   6.3000   7.3000  1.0000           4.8000           8.8000             119      2.4296
1       volatile acidity   0.2100   0.3200  0.1100           0.0450           0.4850             186      3.7975
2            citric acid   0.2700   0.3900  0.1200           0.0900           0.5700             270      5.5125
3         residual sugar   1.7000   9.9000  8.2000         -10.6000          22.2000               7      0.1429
4              chlorides   0.0360   0.0500  0.0140           0.0150           0.0710             208      4.2466
5    free sulfur dioxide  23.0000  46.0000 23.0000         -11.5000          80.5000              50      1.0208
6   total sulfur dioxide 108.0000 167.0000 59.0000          19.5000         255.5000              19      0.3879
7                density   0.9917   0.9961  0.0044           0.9852           1.0027               5      0.1021
8                     pH   3.0900   3.2800  0.1900           2.8050           3.5650              75      1.5312
9              sulphates   0.4100   0.5500  0.1400           0.2000           0.7600             124      2.5316
10               alcohol   9.5000  11.4000  1.9000           6.6500          14.2500               0      0.0000

15. OBSERVACIONES CLAVE
--------------------------------------------------------------------------------
   - El alcohol es la variable más importante para predecir calidad (11.7% de importancia)
   - Existe una fuerte correlación negativa entre densidad y alcohol (-0.780)
   - La mayoría de vinos son de calidad media (5-6), representando 74.6% del dataset
   - 11 de 11 variables muestran diferencias significativas entre grupos de calidad
   - El modelo Random Forest logra un accuracy de 67.6%
   - Ninguna variable sigue una distribución normal (todas tienen p < 0.05 en tests de normalidad)
   - Los vinos de alta calidad tienen en promedio 12.2% más alcohol que los de baja calidad
