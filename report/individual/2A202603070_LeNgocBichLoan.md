# Báo cáo cá nhân — LeNgocBichLoan-2A202603070

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.
Số frame trong báo cáo ghi theo CVAT (0–149).

## 0. Thông tin học viên

- Họ tên: Lê Ngọc Bích Loan
- MSSV: 2A202603070
- Mã đề (A/B/C): **B** (P1–P5 = ID MOT17 1, 19, 20, 21, 22)
- Email: lengocbichloan5@gmail.com
- Link repository: https://github.com/panii273/K5-L2-DAY05-LeNgocBichLoan-2A202603070-MOTTracking
- Giờ bắt đầu: 00:44 ngày 18/11/2026 (GMT+7)
- Giờ kết thúc: 02:20 ngày 18/11/2026 (GMT+7)

## 1. Xem trước đoạn video (CP0)

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---|---|---|---|---|
| P1 | 0 | 149 | Đi sang phải trong cửa hàng 0–90, gần như đứng yên 90–149 | 30–60 (ông áo đen đi ngang phía trước) | Người mặc đồ tối **bên trong** cửa hàng Vodafone, sau kính; người bị che của bài |
| P2 | 0 | 149 | Đi chéo từ phải vào giữa, **tiến dần về camera** suốt đoạn, nhanh hơn từ ~110 | Không | Bà áo khoác xanh lá, xách túi đen; box cao từ ~344 lên ~835 px |
| P3 | 3 | 149 | Vào từ mép phải; tiến về camera, tăng tốc từ ~93 | 3–72 bị mép khung cắt / P2 che một phần | Ông áo xanh dương, đội mũ |
| P4 | 0 | 146 | Đi sang phải 0–40 rồi gần như đứng yên | ~109–146 (P2 rồi P3 đi ngang phía trước) | Bé gái áo sáng trước màn hình Woolworths, box nhỏ (~125 px) |
| P5 | 0 | 132 | Đi sang phải 0–30 rồi đứng cạnh bé gái | ~100–132 (P2, P3 đi ngang phía trước) | Người lớn đi cùng bé gái |

## 2. Keyframe và thời gian (CP1, CP4)

Số keyframe lấy từ kết quả `src/check_submission.py`.

| Mã | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---|---|---|---|---|---|
| P1 | 13 | 0, 20, 30, 49, 50, 60, 70, 80, 90, 110, 120, 130, 149 | 140 | 9,3 | ~15 (gồm vẽ lại) | Đoạn bị che 30–60; lúc đầu track bắt đầu nhầm ở f20 nên phải vẽ lại từ f0 |
| P2 | 22 | 0, 3, 10, 15, 20, 39, 40, 50, 65, 75, 76, 80, 92, 103, 107, 110, 119, 126, 130, 137, 144, 149 | 150 | 14,7 | ~30 (gồm tỉa keyframe) | Tiến về camera nên kích thước tăng liên tục; lần đầu đặt 65 keyframe, tỉa lại |
| P3 | 24 | 3, 13, 23, 29, 33, 39, 43, 49, 53, 59, 63, 73, 83, 93, 103, 105, 113, 123, 125, 133, 136, 138, 143, 149 | 147 | 16,3 | ~10 | Bị mép khung cắt lúc vào; tiến sát camera và tăng tốc cuối đoạn |
| P4 | 17 | 0, 10, 20, 30, 40, 50, 70, 105, 109, 110, 136, 137, 138, 139, 140, 144, 145 | 122 | 13,9 | ~8 | Box nhỏ, bị che hai lần liên tiếp bởi P2 và P3 |
| P5 | 9 | 0, 10, 20, 30, 50, 100, 105, 125, 126 | 115 | 7,8 | ~7 | Đứng sát P4; bị che, lấp ló lại ở 125–132 |
| **Tổng** | **85** | | **674** | **12,6** | **~70** | |

Keyframe / 100 frame của cả bài = 85 ÷ 674 × 100 = **12,6**.

Bạn đặt keyframe nhiều nhất ở người nào? Vì sao?

P3 (24) và P2 (22). Cả hai đi **tiến lại gần camera**: chiều cao box tăng gần gấp 2,5 lần (P2 344 → 835 px, P3 391 → 955 px) và tăng nhanh dần, trong khi nội suy tuyến tính giả định tốc độ đổi kích thước không đổi, nên box nội suy luôn nhỏ hơn người thật ở giữa hai keyframe. P3 còn thêm đoạn bị mép khung cắt lúc mới vào (f3–72) và tăng tốc ở cuối. Với P2, lần đầu tôi chỉnh gần như mọi frame lệch nhẹ (65 keyframe ≈ 43/100 frame); sau đó tỉa còn 22, chỉ giữ chỗ box lệch rõ (IoU < 0,7).

## 3. Đoạn bị che (CP2)

Người bị che: `P1` (người bên trong cửa hàng Vodafone; người che là ông áo khoác đen đeo balô đi ngang phía trước, không thuộc 5 người).

| Mốc | Frame |
|---|---:|
| Bắt đầu bị che một phần (bật `occluded`) | 30 |
| Mất hẳn (bật `outside`) | 39 |
| Hiện lại (tắt `outside`) | 49 |
| Thấy rõ trở lại (tắt `occluded`) | 60 |

- Thời gian khuất hẳn: **10 frame** (39–48) = **0,33 giây**.
- Quyết định: **giữ cùng ID**.
- Lý do:
  1. Khuất 10 frame, thấp hơn nhiều ngưỡng 60 frame của lớp.
  2. Ngoại hình khớp: cùng áo tối, quần jean, cùng kích thước (box cao ~254 px trước và sau).
  3. Chỗ hiện lại đúng vị trí và hướng cũ: người đang đi chậm sang phải trong cửa hàng, hiện lại ngay sau lưng ông áo đen vừa đi qua.

Trong đoạn `occluded`, box giữ kích thước toàn thân ước lượng (107 × 254 px), không co theo phần nhìn thấy.

Ảnh chụp màn hình (MOT17, MOTChallenge (Milan et al., 2016)):

![Trước khi che — frame 25](images/che_1_truoc.png)
![Giữa đoạn che — frame 44, panel object của P1 (ID 6) hiện cờ outside](images/che_2_giua.png)
![Sau khi hiện lại — frame 55, vẫn ID 6, còn occluded](images/che_3_sau.png)

Ngoài P1, hai người khác cũng có đoạn khuất ngắn và đều giữ cùng ID: P4 khuất hẳn 111–135 (25 frame), P5 khuất hẳn 107–124 (18 frame), đều < 60 frame.

## 4. Tự review ID (CP3)

Lượt 1 theo người (đi ngược từ frame 149 về 0 trên CVAT), lượt 2 theo cảnh (nhảy 10 frame).

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| 3–123 | (người ngoài) | `false_track` | Gán nhầm ông áo khoác đen đeo balô (không thuộc đề B) thành một track | Lượt 1 (đối chiếu bảng nhận diện) | Có, đã xoá track |
| 0–19 | P1 | `lost` | Track P1 bắt đầu từ f20 trong khi P1 thấy được từ f0 | Lượt 1 | Có, vẽ lại track từ f0 |
| 29–58 | P3 | `flag` | Cờ `occluded` bật/tắt xen kẽ mỗi vài frame trong lúc P3 vẫn bị mép khung cắt | Lượt 1 | Có, để `occluded` liên tục 3–72 |
| 105–110 | P4 | `flag` | Thiếu `occluded` ngay trước khi bé gái bị P2 che hẳn (nhảy thẳng sang `outside`) | Lượt 2 | Có, bật `occluded` từ 109 |
| 125–132 | P5 | `lost` | Bật `outside` từ 110 tới hết, trong khi P5 lấp ló lại giữa P2 và P3 ở 125–132 | Lượt 2 | Có, tắt `outside` 125–132, bật `occluded` |

Tổng hợp số lỗi theo loại:

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 2 | 0 | 1 | 0 | 2 |

Lỗi nào chỉ lượt 2 (theo cảnh) mới thấy, lượt 1 (theo người) không thấy? Vì sao?

Lỗi `lost` của P5 ở 125–132 và `flag` của P4 ở 105–110. Khi xem theo từng người, tôi chỉ nhìn box của người đó: box đã tắt thì không có gì để nhìn, nên không nhận ra người vẫn lấp ló. Khi xem theo cảnh, nhìn cả nhóm P2, P3 đi ngang qua trước P4, P5 thì mới thấy phần thân của P5 vẫn lộ ra giữa hai người đó, và thấy P4 bị che dần chứ không biến mất ngay.

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `src/exports/LeNgocBichLoan_mot.zip` |
| Tên file CVAT for video 1.1 | `src/exports/LeNgocBichLoan_cvat_video.zip` |
| Số track ID khác nhau trong `gt/gt.txt` (phải là 5) | 5 |
| Frame `outside` không có dòng trong `gt.txt` (đúng / sai) | Đúng (track của P1 không có dòng ở frame 39–48) |
| Job đã completed trên CVAT máy cá nhân | Có |

Dán phần tóm tắt in ra từ `src/check_submission.py`:

```text
Số frame in theo CVAT (bắt đầu từ 0). Trong gt.txt, frame_id = frame CVAT + 1.

=== File MOT 1.1: LeNgocBichLoan_mot.zip ===
  Số track ID: 5   |   Tổng số box: 674
  [OK]        Đúng 5 track ID.

  Track | Frame có mặt | Số frame | Đoạn vắng (outside)
      1 |   0–149      |      150 | -
      2 |   0–149      |      140 | 39–48
      3 |   0–146      |      122 | 111–135
      4 |   0–132      |      115 | 107–124
      5 |   3–149      |      147 | -

=== File CVAT for video 1.1: LeNgocBichLoan_cvat_video.zip ===

  Track | Nhãn   | Frame thấy | Keyframe | KF/100 frame | Frame occluded | Lần bật outside
      0 | person |        150 |       22 |         14.7 |              0 |               0
      1 | person |        140 |       13 |          9.3 |             20 |               1
      2 | person |        122 |       17 |         13.9 |              7 |               2
      3 | person |        115 |        9 |          7.8 |             15 |               2
      4 | person |        147 |       24 |         16.3 |             70 |               0

  Tổng: 85 keyframe / 674 frame có mặt = 12.6 keyframe / 100 frame
  [OK]        Đọc được 5 track từ annotations.xml.

=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 0
  Đạt. Dán phần tóm tắt này vào báo cáo mục 5.
```

Đối chiếu ID: trong `gt.txt` 1 = P2, 2 = P1, 3 = P4, 4 = P5, 5 = P3; trong `annotations.xml` track 0–4 theo cùng thứ tự.

## 6. Ba câu kết

1. Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?

   Với P2 và P3 (đi về phía camera), tôi sẽ đặt keyframe thưa ở đầu và dày dần về cuối thay vì chỉnh gần như mọi frame ngay từ đầu, vì kích thước người tăng nhanh dần khi lại gần nên nội suy tuyến tính chỉ sai nhiều ở đoạn cuối. Tôi cũng sẽ đặt keyframe che khuất bằng cách dò từng frame (`F`/`D`) ngay từ đầu, không đặt theo bước 10 frame rồi sửa lại.

2. Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?

   Chỗ không chắc nhất là P5 ở 125–132: người lấp ló giữa P2 và P3 có thể là P5 hoặc một người đi phía sau. Tôi giữ cùng ID vì vị trí (x ≈ 1380) và chiều cao box khớp với P5 trước khi bị che, P5 đang đứng yên cạnh bé gái, và chỉ khuất 18 frame (< 60). Cả ba trường hợp khuất (P1 10 frame, P5 18 frame, P4 25 frame) đều dưới ngưỡng 60 frame nên giữ cùng ID.

3. Một lỗi ID trong job của bạn có thể làm xe tự lái dự đoán sai chuyển động của người đó như thế nào? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?

   Lấy lỗi đã sửa của P5: nếu để `outside` tới hết rồi khi P5 hiện lại lại gán ID mới, tracker học từ nhãn này sẽ coi P5 là "người mới xuất hiện" không có lịch sử vận tốc, nên không dự đoán được P5 đang đứng chờ cạnh bé gái và có thể bước ra. Lỗi đứt track / đổi ID ảnh hưởng **IDF1** nhiều hơn, vì IDF1 đo tỉ lệ frame giữ đúng một ID trên cả quỹ đạo; MOTA chỉ cộng thêm một lần IDSW, trong khi phần frame thiếu box (`lost`) thì làm tăng FN và kéo cả MOTA xuống.

## 7. Tài liệu tham khảo và công cụ AI đã dùng

- Tài liệu lớp: `docs/GUIDELINE.md`, `CHECKPOINTS.md`, `docs/CVAT_CHEATSHEET.md`, `docs/MOT_FORMAT.md`.
- Dữ liệu: MOT17-09, MOTChallenge (Milan et al., 2016).
- Công cụ AI: Claude (Anthropic) dùng để đọc hướng dẫn, sửa lỗi tải 150 frame về.
