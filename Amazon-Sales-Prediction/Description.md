Feature int and float = price, discount_percent, quantity_sold, rating, review_count,
discounted_price, total_revenue

feature object/string = product_category,customer_region, payment_method


from xgboost import XGBClassifier
from sklearn.pipeline import Pipeline

modelXGB = Pipeline(steps=[
    ('preprocessor', preprocessor),
    ('model', XGBClassifier(
        n_estimators=300,
        learning_rate=0.05,
        max_depth=6,
        random_state=42,
        use_label_encoder=False,
        eval_metric='logloss'
    ))
])


scoresXGB = cross_val_score(
    modelXGB,
    TrainX,
    TrainY,
    scoring='f1',
    cv=5
)

print("XGB F1:", scoresXGB.mean())


bsk up desc
