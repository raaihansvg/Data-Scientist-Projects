“This project aims to predict students’ Final GPA based on academic, behavioral, and demographic features using regression models.”


Fitur:
math score, science score, english score, history score, computer score, attendance rate, assignment avg, quiz avg,
project_score,previous gpa,study hours daily,revision_hours,family_size,parent_education,family_income,sleep_hours,physical_activity,screen_time,ilness_days,
mental_stress,sleep quality,private tuition,tuition hours, study room, parent involvement,scholarship_flag,part time job hours, financial stress,digital literacy, device availability, stress index


Target: 
final gpa

Model :
Ridge Regression (alpha tuning)

Bandingkan dengan Linear Regression

*Kesimpulan korelasi negatif(Non Target)*

1. Sleep Hours -> Ilness Days : Jika jam tidur terjaga maka kemungkinan untuk terkena penyakit akan turun
2. Sleep Hours -> Stress Index : Jika jam tidur terjaga maka kemungkinan stress juga akan menurun
3. Physical Activity -> Ilness Days : Jika sering melakukan kegiatan fisik(olahraga dll) maka kemungkinan terkena penyakit akan menurun
4. Physical Activity -> Stress Index : Jika sering melakukan kegiatan fisik
(olahraga dll) maka kemungkinan stress juga akan menurun
5. Ilness Days -> Sleep Quality : Jika kualitas tidur terjaga maka kemungkinan untuk terkana penyakit juga akan menurun
6. Sleep Quality -> Stress Index : Jika kualitas tidur terjaga maka kemungkinan stress juga akan menurun
________________________________________________________________________________
*Kesimpulan korelasi negatif(Target)*
1. Screen Time -> Final Gpa : Jika mengontrol aktivitas penggunaan gadget dll maka untuk mendapatkan gpa yang lebih baik akan meningkat
2. Mental Stress -> Final Gpa : Jika sesorang tidak mengalami stress mental maka untuk kemungkinan mendapatkan gpa yang bagus akan meningkat
3. Stress Index -> Final Gpa : Jika sesorang tidak mengalami stress maka kemungkinan untuk mendapatkan gpa yang bagus akan meningkat
4. Parent Involvement -> Financial Stress : Jika keterlibatan orang tua dalam faktor ekonomi kepada anak nya terjaga maka kemungkinan anak untuk stress financial juga akan menurun


belum selesai, next split data
from sklearn.linear_model import Ridge

ridge = Ridge(alpha=1.0)

rmse_scores = -cross_val_score(
    ridge, TrainX, TrainY,
    scoring='neg_root_mean_squared_error',
    cv=5
)

print("Ridge RMSE")
print("Mean:", rmse_scores.mean())
print("Std:", rmse_scores.std())
---
alphas = [0.01, 0.1, 1, 10, 50]

for a in alphas:
    ridge = Ridge(alpha=a)
    rmse = -cross_val_score(
        ridge, TrainX, TrainY,
        scoring='neg_root_mean_squared_error',
        cv=5
    ).mean()
    print(f"alpha={a}, RMSE={rmse}")





