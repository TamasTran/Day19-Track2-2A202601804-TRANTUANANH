# Reflection — Lab 19

**Tên:** _Trần Tuấn Anh_
**Cohort:** _A20-K3B
**Path đã chạy:** _lite_

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

- **Exact**: Keyword (BM25) thắng vì truy vấn chứa các từ khóa xuất hiện nguyên văn trong văn bản.
- **Paraphrase**: Semantic (Vector) thắng vì người dùng dùng từ đồng nghĩa hoặc diễn đạt lại; BM25 sẽ bị trượt từ vựng (vocabulary mismatch) còn Vector nắm bắt được ý nghĩa.
- **Mixed**: Hybrid thắng do dung hòa được cả hai ưu điểm thông qua RRF.

**Khi nào KHÔNG dùng Hybrid:**
1. **Dùng pure BM25 khi:** Tìm kiếm các mã định danh chính xác (SKU, ID, Error Code), tên riêng khó, hoặc khi hệ thống có tài nguyên tính toán yếu/đòi hỏi độ trễ cực thấp (P99 < 10ms).
2. **Dùng pure Vector khi:** Tìm kiếm đa ngôn ngữ (cross-lingual), tìm kiếm khái niệm trừu tượng không có từ khóa cụ thể.

---

## Điều ngạc nhiên nhất khi làm lab này

Em biết được rằng hiện tượng "Cold Start" có thể khiến P99 Latency bị dội lên cực cao (hơn 500ms) ở những truy vấn đầu do mô hình nạp vào RAM. Giải pháp giảm RRF depth (từ 50 xuống 15) và thêm bước "warm-up" đã xử lý triệt để vấn đề này. Nhưng do máy em khá yếu nên không thể chạy chính xác NB3 cụ thể là Hybrid latency dưới 50ms do CPU hạn chế.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
