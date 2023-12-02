# Mô phỏng mạng ngang hàng BitTorrent
## Chuẩn bị
- Máy ảo VMware cài hệ điều hành Ubuntu.
- Môi trường chạy java.

# Programming Environment
  Java

# Compile
<b>File owner</b> <br/>
cd Peer1_Owner <br/>
javac FileOwner.java <br/>

<b>Peer2</b> <br/>
cd Peer2 <br/>
javac Peer.java <br/>

<b>Peer3</b> <br/>
cd Peer3 <br/>
javac Peer2.java <br/>

<b>Peer4</b> <br/>
cd Peer4 <br/>
javac Peer.java <br/>

<b>Peer5</b> <br/>
cd Peer5 <br/>
javac Peer5.java <br/>

<b>Peer6</b> <br/>
cd Peer6 <br/>
javac Peer6.java 

- Kết quả chuẩn bị:
<img src="https://ttnguyen.net/wp-content/uploads/2023/11/chuan-bi-chay-chuong-trinh-mo-phong-bittorrent.jpg" width="1000" height="750">
 
# Phân tích hoạt động
– Tạo 2 chương trình:

Phân tích hoạt động:

1. Khởi động Peer1 Owner, cung cấp một cổng.
2. Khởi động 5 máy ngang hàng: Peer 2, Peer 3, Peer 4, Peer 5, Peer 6. Mỗi ngang hàng có 3 cổng: cổng máy chủ, cổng chính nó, cổng ngang hàng khác.
3. Mỗi ngang hàng kết nối với chủ sở hữu tệp. 1 cổng sẽ tải lên các mảnh cho ngang hàng, trong khi cổng còn lại sẽ lắng nghe các ngang hàng mới.
4. Sau khi nhận được các mảnh từ chủ sở hữu tệp. Ngang hàng sẽ lưu chúng dưới dạng các tệp riêng biệt, liệt kê ID các mảnh mà nó có.
5. Sau đó, ngang hàng tiến hành với hai luồng mới, với một luồng lắng nghe hàng xóm tải lên của nó và luồng còn lại kết nối với hàng xóm tải xuống của nó.
6. Ngang hàng yêu cầu danh sách ID các mảnh từ hàng xóm tải xuống, so sánh với danh sách của riêng nó để tìm các phân đoạn còn thiếu và yêu cầu ngẫu nhiên một mảnh còn thiếu từ hàng xóm.
7. Trong khi đó, nó sẽ gửi danh sách ID phân đoạn của riêng mình cho hàng xóm tải lên của mình và khi được yêu cầu sẽ tải lên các phân đoạn lên hàng xóm.
8. Sau khi một ngang hàng có tất cả các phân đoạn tệp, nó sẽ kết hợp chúng thành một tệp duy nhất.
9. Các mạng ngang hàng kết nối với nhau và trao đổi danh sách ID các mảnh. Sau đó, chúng yêu cầu và gửi các mảnh cho nhau cho đến khi tất cả các mạng ngang hàng đều có tất cả các mảnh và có thể kết hợp chúng thành một tệp duy nhất.

# Kết quả chạy thử
<img src="https://ttnguyen.net/wp-content/uploads/2023/11/ket-qua-chay-chuong-trinh-mo-phong-bittorrent.jpg" width="1000" height="750">

Chi tiết: [Mô phỏng mạng BitTorrent](https://ttnguyen.net/bittorrent-la-gi/)
     



