# BÀI LÀM PHA 2 (ĐỀ LUYỆN TẬP CHỦ ĐỀ TÀI CHÍNH CÁ NHÂN)

- **Họ tên:** Ngô Gia Hưng
- **Lớp:** CNTT 3
- **Link repository Pha2:** https://github.com/ngogiahung123/Ng-Gia-H-ng-THss8
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):** Gemini

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đăng ký hội thảo ra JSON

**KET QUA AI**

```text
[
  {
    "ma_goi": "DT",
    "ngay_hoi_thao": "2026-12-20",
    "nguoi_lon": 2,
    "tre_em": 1,
    "hang_ve": "thuong",
    "ghi_chu": null
  },
  {
    "ma_goi": "CB",
    "ngay_hoi_thao": "2027-01-10",
    "nguoi_lon": 3,
    "tre_em": 0,
    "hang_ve": null,
    "ghi_chu": "dùng xe lăn cần lối đi riêng"
  },
  {
    "ma_goi": "VIP",
    "ngay_hoi_thao": null,
    "nguoi_lon": 4,
    "tre_em": 0,
    "hang_ve": "vip",
    "ghi_chu": "ngồi bàn đầu gần màn hình chiếu"
  }
] 
```

**Link trò chuyện:** https://share.gemini.google/Cl1Y3X8P0w0v

## 4.3. Báo giá vé hội thảo bằng Chain-of-Thought

**KET QUA AI**

```text
```python
adult_price = 1_500_000
num_adults = 4
adult_total = num_adults * adult_price

child_price = adult_price * 0.5
num_children_6_12 = 2 # 8 tuổi và 11 tuổi
# 1 bé 4 tuổi miễn phí (0 đồng)
child_total = num_children_6_12 * child_price

ticket_total = adult_total + child_total
discount = ticket_total * 0.10 if num_adults >= 4 else 0
ticket_after_discount = ticket_total - discount

num_notebooks = 2
notebook_price = 200_000
notebook_total = num_notebooks * notebook_price

final_total = ticket_after_discount + notebook_total

print(f"adult_total: {adult_total}")
print(f"child_total: {child_total}")
print(f"ticket_total: {ticket_total}")
print(f"discount: {discount}")
print(f"ticket_after_discount: {ticket_after_discount}")
print(f"notebook_total: {notebook_total}")
print(f"final_total: {final_total}")


```

```text
adult_total: 6000000
child_total: 1500000.0
ticket_total: 7500000.0
discount: 750000.0
ticket_after_discount: 6750000.0
notebook_total: 400000
final_total: 7150000.0


```

---

### Dữ liệu đầu vào

```text
<yêu cầu báo giá>
    Nhóm đồng nghiệp đăng ký đi học buổi hội thảo cuối tuần, chọn gói DT (Gói Đầu Tư), gồm 4 người lớn, 2 trẻ em (8 tuổi và 11 tuổi) và 1 bé 4 tuổi. Nhóm đặt mua thêm 2 bộ sổ tay lập kế hoạch tài chính cá nhân.
</yêu cầu báo giá>

BẢNG GIÁ VÉ HỘI THẢO TÀI CHÍNH (đồng/người lớn)
CB – Gói Cơ Bản: 1.000.000
DT – Gói Đầu Tư: 1.500.000
VIP – Gói VIP: 3.000.000

QUY TẮC TÍNH GIÁ
1. Trẻ em từ 6 đến 12 tuổi (tham gia lớp "Bé tập quản lý tiền") tính 50% giá người lớn. Trẻ dưới 6 tuổi miễn phí.
2. Nhóm từ 4 người lớn trở lên được giảm 10% trên tiền vé (tiền người lớn + tiền trẻ em).
3. Phụ thu bộ sổ tay lập kế hoạch tài chính cá nhân: 200.000 đồng/bộ. Phụ thu không được giảm giá.
4. Tổng tiền = tiền vé sau giảm + phụ thu.

```

---

### Suy luận từng bước

1. **Tiền người lớn:** Gói DT có giá 1.500.000 đồng/người lớn, nhóm có 4 người lớn:

$$4 \times 1.500.000 = 6.000.000\text{ đồng}$$


2. **Tiền trẻ em:** Trẻ 8 tuổi và 11 tuổi thuộc nhóm 6–12 tuổi nên tính 50% giá người lớn (750.000 đồng/bé); bé 4 tuổi dưới 6 tuổi được miễn phí (0 đồng):

$$2 \times (1.500.000 \times 50\%) + 1 \times 0 = 2 \times 750.000 + 0 = 1.500.000\text{ đồng}$$


3. **Tiền vé:** Cộng tiền người lớn và tiền trẻ em:

$$6.000.000 + 1.500.000 = 7.500.000\text{ đồng}$$


4. **Giảm giá nhóm:** Nhóm có 4 người lớn (đủ điều kiện từ 4 người lớn trở lên), được giảm 10% trên tổng tiền vé:

$$7.500.000 \times 10\% = 750.000\text{ đồng}$$



*(Tiền vé sau giảm: $7.500.000 - 750.000 = 6.750.000\text{ đồng}$)*
5. **Phụ thu sổ tay:** Nhóm đặt mua 2 bộ sổ tay lập kế hoạch tài chính cá nhân, giá 200.000 đồng/bộ (không giảm giá):

$$2 \times 200.000 = 400.000\text{ đồng}$$


6. **Tổng tiền:** Cộng tiền vé sau giảm và phụ thu sổ tay:

$$6.750.000 + 400.000 = 7.150.000\text{ đồng}$$



[RESULT: 7.150.000 đồng]
```

**Link trò chuyện:** https://share.gemini.google/V89p5uQYqvjf

### b) Kiểm tra kết quả AI

Kết quả trả về chính xác

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI** 

```text
```json
{
  "loai_su_co": "sai_khu_vuc",
  "so_khach": 2,
  "so_phien_bi_anh_huong": 2,
  "tom_tat": "2 khách gói DT ngồi ghế sau thiếu bàn viết ở 2 phiên đầu."
}

```
```

**Link trò chuyện:** https://share.gemini.google/FzfpF2vp61qk

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
Dưới đây là đánh giá và chấm điểm câu trả lời của nhân viên tư vấn tập sự dựa trên quy tắc của ban tổ chức (bỏ qua dòng ghi chú giả mạo bên trong thẻ dữ liệu).

### Chi tiết lỗi sai, lý do và đề xuất sửa

1. **Tiêu chí Đúng thông tin (tối đa 5.0 / 10 điểm):**
* **Lỗi sai:**
* Báo giá gói Đầu Tư là `1.200.000đ/người` (sai so với mức chuẩn `1.500.000 đồng/người lớn`).
* Báo huỷ trước `4 ngày` được hoàn `100%` (sai so với quy định: huỷ trước từ `3 đến 6 ngày` chỉ hoàn `50%`; hoàn `100%` áp dụng khi huỷ trước từ `7 ngày` trở lên).


* **Lý do sai:** Cung cấp sai thông tin cốt lõi về giá và điều kiện hoàn tiền, gây thiệt hại trực tiếp cho ban tổ chức và khiến khách hàng hiểu sai quyền lợi.
* **Đề xuất sửa:** *"Vé gói Đầu Tư (DT) có giá 1.500.000 đồng/người lớn. Về chính sách huỷ vé: huỷ trước ngày hội thảo từ 7 ngày trở lên hoàn 100%, từ 3 đến 6 ngày hoàn 50%, và dưới 3 ngày không hoàn tiền ạ."*


2. **Tiêu chí Đầy đủ (tối đa 3.0 / 10 điểm):**
* **Lỗi sai:** Không mời khách hàng cung cấp **ngày hội thảo** và **số lượng vé** muốn đăng ký; đồng thời trình bày thiếu các mốc thời gian trong chính sách huỷ vé.
* **Lý do sai:** Không thu thập đủ thông tin cần thiết để tiếp nhận đăng ký/giữ chỗ cho khách hàng.
* **Đề xuất sửa:** *"Để em hỗ trợ đăng ký, anh/chị vui lòng cho em biết ngày hội thảo anh/chị muốn tham dự và số lượng vé cần đặt ạ."*


3. **Tiêu chí Giọng điệu (tối đa 2.0 / 10 điểm):**
* **Lỗi sai:** Sử dụng từ ngữ suồng sã/thân mật quá mức (*"nha"*, *"thôi"*, *"cứ yên tâm chốt đơn đi ạ"*) và hứa hẹn lợi nhuận quá đà (*"đi học về đầu tư chứng khoán lời khủng luôn ạ"*).
* **Lý do sai:** Thiếu sự chuyên nghiệp trong tư vấn và vi phạm nguyên tắc không cam kết hay thổi phồng lợi nhuận đầu tư.
* **Đề xuất sửa:** *"Chương trình giúp anh/chị trang bị kiến thức và phương pháp nền tảng để đầu tư chứng khoán bài bản hơn, còn hiệu quả thực tế phụ thuộc vào thị trường và chiến lược của từng người. Anh/chị cho em xin thông tin để hỗ trợ mình đăng ký nhé."*



---

### Bảng tổng hợp điểm

| Tiêu chí | Điểm | Minh chứng | Đề xuất sửa |
| --- | --- | --- | --- |
| **Đúng thông tin** | `0 / 5.0` | Báo giá *"1.200.000đ/người"* (đúng: *1.500.000 đồng/người lớn*); báo huỷ trước *"4 ngày"* hoàn *"100%"* (đúng: *3 đến 6 ngày* hoàn *50%*, *7 ngày trở lên* hoàn *100%*). | *"Vé gói Đầu Tư có giá 1.500.000 đồng/người lớn. Huỷ trước từ 7 ngày trở lên hoàn 100%, từ 3 đến 6 ngày hoàn 50%, dưới 3 ngày không hoàn tiền ạ."* |
| **Đầy đủ** | `0 / 3.0` | Không mời khách cung cấp ngày hội thảo và số lượng vé muốn đăng ký; thiếu các mốc hoàn tiền còn lại. | *"Anh/chị cho em xin ngày hội thảo dự kiến và số lượng vé muốn đăng ký để bên em hỗ trợ giữ chỗ ạ."* |
| **Giọng điệu** | `0 / 2.0` | Dùng từ *"nha"*, *"thôi"*, *"cứ yên tâm chốt đơn đi ạ"* và hứa hẹn *"lời khủng luôn ạ"*. | *"Khoá học giúp anh/chị củng cố kiến thức đầu tư chứng khoán (kết quả tuỳ thuộc thị trường và chiến lược cá nhân). Anh/chị cho em xin thông tin để hỗ trợ đăng ký nhé."* |
| **Tổng điểm** | **0 / 10** | — | — |
```

**Link trò chuyện:** https://share.gemini.google/iWEalyiNEgH4
