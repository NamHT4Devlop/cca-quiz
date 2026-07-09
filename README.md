# 🎓 Claude Certified Architect — Web ôn tập 300 câu trắc nghiệm

Website ôn tập trắc nghiệm tự chứa (một file `index.html` duy nhất, đã nhúng sẵn 300 câu).
Chọn **đúng → xanh**, **sai → đỏ**, hiện luôn **đáp án đúng + giải thích**.

## 🔗 Web đã online (miễn phí)
- **GitHub Pages (web chính, công khai):** https://namht4devlop.github.io/cca-quiz/
- **Repo mã nguồn:** https://github.com/NamHT4Devlop/cca-quiz
- **Bản Claude Artifact (riêng tư, chia sẻ tuỳ chọn):** https://claude.ai/code/artifact/28fd923c-79c2-4aaf-be4f-b4648ff2c9e9

## 🔄 Cập nhật web sau này
Sửa `index.html` (hoặc chạy lại `build.py` sau khi đổi `questions.json`) rồi:
```bash
cd /Users/MAC/Desktop/quiz-website
git add -A && git commit -m "Cập nhật nội dung"
git push
```
Sau ~1 phút GitHub Pages tự build lại, web cập nhật.

## ▶️ Dùng offline (không cần mạng, không cài gì)
Nhấp đúp vào **`index.html`** — mở bằng trình duyệt là chạy được. Tiến độ tự lưu trong trình duyệt (localStorage), tắt/mở lại vẫn còn.

## ✨ Tính năng
- **Chia 300 câu thành 5 đề cố định × 60 câu** (Đề 1 = câu 1–60, … Đề 5 = 241–300) **+ nút "🎲 Đề ngẫu nhiên"** (bốc 60 câu bất kỳ để luyện tổng hợp).
- **Nút "Kiểm tra" trên từng câu:** chọn đáp án → bấm *Kiểm tra* mới hiện **đúng (xanh) / sai (đỏ) + giải thích** (có khoảng lặng để suy nghĩ, không lộ ngay).
- **Làm xong đề → màn hình kết quả** (vòng tròn % + số đúng/sai) với các lựa chọn:
  - **🔁 Làm lại đề này (tự xáo trộn thứ tự)** — chống học vẹt theo vị trí A/B/C/D.
  - **❌ Chỉ làm lại N câu sai** — cày đúng chỗ mình yếu (nhớ nhanh nhất).
  - **➡️ Sang đề kế / 🎲 Đề ngẫu nhiên mới**.
- **Lưu điểm cao nhất từng đề** + thanh tiến độ, hiện ngay ở màn hình chọn đề.
- **Bảng 60 câu** bên trái tô màu theo trạng thái; **đánh dấu (★)** câu cần xem lại.
- **Phím tắt:** `A`–`D` hoặc `1`–`4` chọn · `Enter` kiểm tra / câu tiếp · `←`/`→` chuyển câu · `F` đánh dấu.
- **Giao diện sáng/tối** (nút 🌙) · **chạy tốt trên điện thoại** · **tự lưu tiến độ** (đóng mở lại vẫn còn).

## 🌐 Deploy miễn phí — chọn 1 trong các cách sau

| Cách | Độ dễ | Cần tài khoản? | Ghi chú |
|------|-------|----------------|---------|
| **Netlify Drop** | ⭐ Dễ nhất | Không (lúc đầu) | Vào https://app.netlify.com/drop → **kéo-thả cả thư mục `quiz-website`** → có link `https://ten-ngau.netlify.app` ngay |
| **Cloudflare Pages** | Dễ | Có (free) | Tạo project → Upload assets → kéo-thả folder |
| **Vercel** | Dễ | Có (free) | `vercel` CLI hoặc kéo-thả trên dashboard |
| **GitHub Pages** | Vừa | Có (GitHub) | Xem bên dưới — hợp với repo cá nhân của bạn |

### Cách nhanh nhất: Netlify Drop (30 giây)
1. Mở https://app.netlify.com/drop
2. Kéo cả thư mục **`quiz-website`** thả vào trang.
3. Xong — bạn nhận được một URL công khai chia sẻ được ngay. (Muốn đổi tên miền đẹp thì đăng ký tài khoản free.)

### GitHub Pages (repo cá nhân)
```bash
cd /Users/MAC/Desktop/quiz-website
git init && git add index.html && git commit -m "Add quiz site"
git branch -M main
git remote add origin https://github.com/NamHT4Devlop/cca-quiz.git   # tạo repo này trước trên GitHub
git push -u origin main
```
Rồi vào **repo → Settings → Pages → Source: `main` / root → Save**.
Sau ~1 phút web sống tại `https://namht4devlop.github.io/cca-quiz/`.

> Chỉ có **1 file `index.html`** là đủ để deploy. `questions.json` và các file `.md` chỉ để bạn tham khảo, không bắt buộc đưa lên.

## ⚠️ Lưu ý về nội dung
Dữ liệu được trích **trung thực 100%** từ PDF của bạn. Có **22 câu mà phần giải thích trong PDF gốc bị mâu thuẫn/nhầm nhãn** (4 câu đáng lưu ý, 18 câu chỉ lỗi diễn đạt nhỏ). Chi tiết xem **`CAN-KIEM-TRA-LAI.md`**.

## 🔧 Cập nhật câu hỏi (nếu cần)
File nguồn: `questions.json`. Sửa xong build lại bằng script `build.py` (mình có thể hỗ trợ). Mỗi câu có dạng:
```json
{ "id": 1, "question": "...", "options": {"A":"...","B":"...","C":"...","D":"..."}, "answer": "A", "explanation": "..." }
```
