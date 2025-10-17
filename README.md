flights = [
    [5, 500, 1, 1, 0],
    [15, 1000, 5, 15, 1],
    [0, 200, 3, 7, 0],
    [25, 1500, 7, 20, 1],
    [2, 800, 12, 12, 0]
]

X = [f[:4] for f in flights]
y = [f[4] for f in flights]

def predict_delay(features):
    dep_delay, distance, month, day = features
    if dep_delay > 15 or distance > 1000:
        return 1
    return 0

correct = 0
for xi, yi in zip(X, y):
    pred = predict_delay(xi)
    if pred == yi:
        correct += 1

accuracy = correct / len(y)
print("Model Accuracy:", round(accuracy, 2))

new_flight = [10, 1200, 5, 12] 
prediction = predict_delay(new_flight)
print("Predicted Delay:", "Yes" if prediction == 1 else "No")
