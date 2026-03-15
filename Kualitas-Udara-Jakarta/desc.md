Progress nya sekarang:
1.  Data ISPU udah digabungin semua
2.  data cleaning
3.  check anomaly
4.  pokok nya nanti bersih dulu semua nya

terus kalo udah bersih kita proses predict tanpa make data yang lain, dan kita pake data yang lain ketika udah predict data ISPU dulu
from sklearn.metrics import classification_report

print(classification_report(y_test, y_pred))


1. Predict menggunakan Data ISPU (baseline)

model : xgb, accuracy = ~0.99, learning curve tidak menunjukan overfit

insight : PM2.5 dan o3 (ozon) menjadi polutan yang paling berpengaruh karena hal ini sesuai dengan sikon rill di kota besar di mana debu halus kendaraan dan populasi gas kimia adalah masalah utama


