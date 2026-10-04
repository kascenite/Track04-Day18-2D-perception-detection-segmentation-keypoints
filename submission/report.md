Link notebook đã chạy: https://colab.research.google.com/drive/1UAugFbLyhGiaUcw6HQxsJoaoPJK4Em29?usp=sharing

# Báo cáo kết quả

Trong quá trình thực hiện, tôi đã hoàn thành các nội dung chính của bài tập về 2D perception, bao gồm phát hiện đối tượng, phân đoạn ảnh và xác định keypoints. Đây là các nhiệm vụ quan trọng trong lĩnh vực computer vision, giúp hệ thống có thể nhận diện, phân vùng và định vị các điểm quan trọng trên đối tượng.

- Đã hiểu và áp dụng các nguyên lý cơ bản của object detection, segmentation và keypoints detection.
- Đã xử lý dữ liệu và chạy thử nghiệm trên các ví dụ để kiểm tra hiệu quả của mô hình/thuật toán.
- Đã quan sát được kết quả nhận diện đối tượng rõ ràng hơn, vùng phân đoạn hợp lý và các keypoints được xác định ở vị trí tương đối chính xác.
- Đã đánh giá quá trình làm việc và nhận ra những bước cần cải thiện như độ chính xác, tốc độ xử lý và chất lượng dữ liệu đầu vào.

Kết luận, dự án đã đạt được mục tiêu cơ bản của việc triển khai một pipeline xử lý hình ảnh 2D trong lĩnh vực perception. Mặc dù còn một số hạn chế, nhưng đây là nền tảng tốt để tiếp tục cải thiện và mở rộng cho các bài toán thực tế phức tạp hơn về thị giác máy tính.

## 4C. So sánh `flip_idx` trên val gốc và val lật gương

Metric trong bảng là **Pose mAP50–95**. Val lật gương dùng ảnh lật ngang và nhãn keypoint được hoán đổi theo quy ước giải phẫu.

| Model | Val gốc | Val lật gương | Thay đổi |
|---|---:|---:|---:|
| `flip_idx` giải phẫu | 45,73% | 43,88% | −1,85 điểm % |
| `flip_idx` đồng nhất | 41,69% | 29,77% | −11,92 điểm % |

Val gốc có 53/53 con hổ quay sang phải, nên Pose mAP50–95 trên val gốc đã che khuất một phần lỗi quy ước trái–phải: tập này không kiểm tra khả năng giữ đúng nhãn giải phẫu khi hổ quay sang hướng ngược lại. Val lật làm khác biệt lộ rõ model dùng `flip_idx` đồng nhất giảm 11,92 điểm %, trong khi model dùng `flip_idx` giải phẫu chỉ giảm 1,85 điểm %. Box mAP còn ít hữu ích hơn để phát hiện lỗi này vì hoán đổi nhãn keypoint không làm thay đổi bounding box.
