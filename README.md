# LOL_game
### Khám phá dữ liệu quan trọng nhất: Tại sao lại dự đoán được thắng/thua?

Vẽ pairplot giữa 6 chỉ số cốt lõi của Liên Minh Huyền Thoại và kết quả trận đấu (Win = xanh dương đậm, Loss = xanh nhạt):

![image alt](https://github.com/NTThanh0405/LOL_game/blob/1e1fa55ca93813785bdcea480140d392b3671bd4/image/Pairplot.png) 

| Chỉ số            | Người thắng (màu đậm)                          | Người thua (màu nhạt)                         | Kết luận cực mạnh                                   |
|-------------------|------------------------------------------------|-----------------------------------------------|------------------------------------------------------|
| **Kills**         | Tập trung ở vùng 10–25                         | Rất nhiều người 0–5 kills                     | Giết nhiều = thắng cực kỳ rõ rệt                    |
| **Deaths**        | Phần lớn dưới 10 chết                          | Rất nhiều người chết 15–30+                   | Chết ít = lợi thế thắng khổng lồ                    |
| **Assists**       | Nhiều người có 20–60 assist                    | Ít người vượt quá 30                          | Hỗ trợ tốt → đóng góp lớn vào chiến thắng           |
| **MinionsKilled** | Tập trung dày đặc ở 200–400 lính              | Nhiều người chỉ ăn dưới 100 lính              | Farm tốt = nền tảng chiến thắng                     |
| **DmgDealt**      | Hầu hết trên 150k–300k sát thương              | Rất nhiều người dưới 100k                     | Gây sát thương nhiều = gần như chắc thắng           |
| **TotalGold**     | Đa số trên 15k–25k vàng                        | Phần lớn dưới 12k vàng                        | Nhiều tiền = thắng (gần như là chân lý)             |

Một bức hình thống kê:  
Những người chơi có chỉ số cao (kills, assists, farm, damage, gold) và chỉ số thấp (deaths) gần như luôn luôn là người thắng trận.

## Kết quả mô hình (Results)

Sau khi thực hiện feature engineering và tối ưu mô hình, chúng tôi đạt được hiệu suất dự đoán vượt trội:

| Metric                | Score    | Ghi chú                                    |
|-----------------------|----------|--------------------------------------------|
| **Accuracy**          | **78.05%** | Cao hơn 18% so với mô hình baseline cũ    |
| **ROC AUC**           | **0.86**   | Excellent discrimination (rất tốt)         |
| Precision (dự đoán thắng) | ~79%   | 10 trận dự đoán thắng → đúng ~8 trận      |
| Recall (bắt được người thắng) | ~78% | Không bỏ sót quá nhiều người thực sự thắng |

### Confusion Matrix
![image alt](https://github.com/NTThanh0405/LOL_game/blob/1e1fa55ca93813785bdcea480140d392b3671bd4/image/heatmap.png) 
- Đúng 12.293/15.773 trường hợp (78.05%)
- Sai lầm phân bố đều → không bị bias dự đoán toàn thắng hoặc toàn thua

### ROC Curve
![image alt](https://github.com/NTThanh0405/LOL_game/blob/1e1fa55ca93813785bdcea480140d392b3671bd4/image/ROC.png) 
- AUC = 0.86 → nằm trong khoảng “Very Good” đến “Excellent”
- So sánh: mô hình cũ chỉ đạt AUC ~0.63

Kết quả này hoàn toàn đủ để triển khai thực tế cho các ứng dụng:
- Dự đoán kết quả trận đấu theo thời gian thực
- Hệ thống gợi ý build trang bị/phép bổ trợ
- Phân tích sức mạnh tướng trong từng patch
