# LOL_game
## Kết quả mô hình (Results)

Sau khi thực hiện feature engineering và tối ưu mô hình, chúng tôi đạt được hiệu suất dự đoán vượt trội:

| Metric                | Score    | Ghi chú                                    |
|-----------------------|----------|--------------------------------------------|
| **Accuracy**          | **78.05%** | Cao hơn 18% so với mô hình baseline cũ    |
| **ROC AUC**           | **0.86**   | Excellent discrimination (rất tốt)         |
| Precision (dự đoán thắng) | ~79%   | 10 trận dự đoán thắng → đúng ~8 trận      |
| Recall (bắt được người thắng) | ~78% | Không bỏ sót quá nhiều người thực sự thắng |

### Confusion Matrix
![Confusion Matrix](images/confusion_matrix.png)
- Đúng 12.293/15.773 trường hợp (78.05%)
- Sai lầm phân bố đều → không bị bias dự đoán toàn thắng hoặc toàn thua

### ROC Curve
![ROC Curve](images/images/roc_curve.png)
- AUC = 0.86 → nằm trong khoảng “Very Good” đến “Excellent”
- So sánh: mô hình cũ chỉ đạt AUC ~0.63

Kết quả này hoàn toàn đủ để triển khai thực tế cho các ứng dụng:
- Dự đoán kết quả trận đấu theo thời gian thực
- Hệ thống gợi ý build trang bị/phép bổ trợ
- Phân tích sức mạnh tướng trong từng patch
