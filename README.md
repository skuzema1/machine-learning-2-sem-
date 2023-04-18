# Лабораторная работа №1 (2 семестр)
### 1. Скачаем данные load_wine со следующими столбцами:
 1) alcohol - Алкоголь
 2) malic_acid - яблочная кислота
 3) ash - Ясень
 4) alcalinity_of_ash - Щелочность золы
 5) magnesium - Магний
 6) total_phenols - Общие фенолы
 7) flavanoids - Flavanoids  
 8) nonflavanoid_phenols - нефлаваноидные фенолы
 9) proanthocyanins - Proanthocyanins 
 10) color_intensity - Интенсивность цвета
 11) hue - оттенок
 12) od280/od315_of_diluted_wines - OD280 / OD315 разбавленных вин Спектральное измерение белка / концентрации разбавленных вин
 13) proline - Пролин
### 2. Построим диаграмму  рассеивания по двум базовым показательям яблочной кислоты и ясени (Malic acid; Ash)

![image](https://user-images.githubusercontent.com/93768556/232788281-d430d468-935c-435e-96b7-7507a8fe8789.png)

Наблюдения визуально сгруппированы на 3 группы (К1). Рассмотрим метод для определения наилучшего количества кластеров.
### 3. Определение оптимального количества кластеров по методу локтя

![image](https://user-images.githubusercontent.com/93768556/232788935-155deb83-277d-49eb-8454-bf959a06ac95.png)

 Как видно на графике, локоть расположен в k = 5, что свидетельствует о том, что k = 5 является хорошим выбором для этого набора данных. (K2)
 ### 4. Проведём кластеризацию методом К-средних и рассчитаем средний силуэтный коэффициент.
 
 *для k = 3 (K1)
 
 ![image](https://user-images.githubusercontent.com/93768556/232789430-4e26e009-639c-41da-886b-69ad7c6e6304.png)

*для k = 5 (K2)

![image](https://user-images.githubusercontent.com/93768556/232789643-f0e87138-33d3-43cb-b1d1-80e147cf3c45.png)

Средний коэффициент силуэта при k = 3 (K1) выше, чем при k = 5 (K2), поэтому формально k = 3 (K1) наиболее удачное разбиение.

### 5. Построим диаграмму рассеивания для выбранного варианта разбиения, на которой наблюденияиз разных кластеров будут выделены соответствующими цветами, и нанесены центроиды.

![image](https://user-images.githubusercontent.com/93768556/232789953-4efb8379-1a52-4bdb-96f9-bc2bc87fb6aa.png)

### 6. Добавим к выборке дополнительный показатель щелочности золы (Alcalinity of ash) и разделим выборку на обучающую и прогнозную в соотношении 80% - 20%.

### 7. Определение оптимального количества кластеров по методу локтя

![image](https://user-images.githubusercontent.com/93768556/232790286-ce8b74a9-5885-498a-85c3-1434a1630856.png)

По сравнению с графиком метода локтя для двух признаков на графике для трёх признаков наблюдается более плавный спуск, и оптимальное число кластеров снизилось с 5 до 4.

### 8-9.Проведём кластеризацию на обучающей и прогнозной выборке и сравним средний силуэтный коэффициент.

Средний коэффициент силуэта на обучающей выборке--  0.40843651293120686
Средний коэффициент силуэта на прогнозной выборке--  0.41933127504081935

Средний коэффициент силуэта выше на прогнозной выборке.

### Визуально проанализируем статистическое распределение в кластерах для обучающей выборке.

![image](https://user-images.githubusercontent.com/93768556/232790675-a8aec092-0186-4044-8b4a-2b53380c7505.png)

Визуально каждый кластер не
значительно отличается от прочих. Судя по графикам плотности, по показателю **ash** довольно схожи кластеры 0 и 1, а по **alcalinity_of_ash** - 2 и 3. По диаграммам разброса видно, что каждый из 4 кластеров не образует отдельное плотное множество точек, разбиение не строгое.

### (Дополнительное задание) Проведём оценку точности кластеризации с помощью Acc, сравнив оценки с фактическим разбиением на группы

1) при  n_clusters=4
*для двух показателей (Malic acid; Ash) Accuracy: 0.2303370786516854
*для трёх показателей (Malic acid; Ash; Alcalinity of ash) Accuracy: 0.14606741573033707
2) при  n_clusters=3
*для двух показателей (Malic acid; Ash) Accuracy: 0.398876404494382
*для трёх показателей (Malic acid; Ash; Alcalinity of ash) Accuracy: 0.3146067415730337
3) при  n_clusters=2
*для двух показателей (Malic acid; Ash) Accuracy: 0.37640449438202245
*для трёх показателей (Malic acid; Ash; Alcalinity of ash) Accuracy: 0.2303370786516854
3) при  n_clusters=5
*для двух показателей (Malic acid; Ash) Accuracy: 0.3258426966292135
*для трёх показателей (Malic acid; Ash; Alcalinity of ash) Accuracy: 0.14606741573033707

Из оценки кластеризации следует, что алгоритм(при разбиении на 3 кластера с двумя базовыми признаками) имеет наиболее высокую точность (=0.398876404494382). Тем не менее это низкое значение, что указывает на неправильную категоризацию большинства объектов данных.
