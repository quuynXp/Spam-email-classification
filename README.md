# Spam-email-classification
spam email classification

Chúng tôi muốn kiểm tra xem email có phải là thư rác hay không thông qua phân loại văn bản trong WEKA.

<h2>Giới thiệu</h2>
Mỗi ngày, người dùng E-mail nhận được hàng trăm thư rác với nội dung mới, từ các địa chỉ mới được phần mềm rô-bốt tự động tạo ra. Việc lọc thư rác bằng các phương pháp truyền thống như danh sách đen trắng (tên miền, địa chỉ IP, địa chỉ gửi thư) gần như là không thể. Việc áp dụng các phương pháp khai thác văn bản vào E-mail có thể nâng cao hiệu quả lọc thư rác. Ngoài ra, việc phân loại thư rác cũng có thể thiết lập sự phụ thuộc theo chủ đề từ địa lý.

<h2>TẬP DỮ LIỆU</h2>
Chúng tôi có 5180 email dưới dạng tập dữ liệu trong ba thư mục norm cho bình thường, ham cho tác hại và spam cho Thư rác. Các tính năng của tập dữ liệu như sau.
1. Một từ hoặc ký tự cụ thể thường xuyên xuất hiện trong e-mail.
2. Các thuộc tính độ dài chạy (55-57) đo độ dài của các chuỗi chữ in hoa liên tiếp.

<h2>Triển khai</h2>
<h3>Thuật toán C4.5(J48)</h3>
Chúng tôi đang sử dụng thuật toán C4.5 được gọi là thuật toán j48 trong WEKA. C4.5 là thuật toán được sử dụng để tạo cây quyết định do Ross Quinlan phát triển. C4.5 là phần mở rộng của thuật toán ID3 trước đó của Quinlan. Cây quyết định do C4.5 tạo ra có thể được sử dụng để phân loại và vì lý do này, C4.5 thường được gọi là bộ phân loại thống kê.
Thuật toán này trở nên khá phổ biến sau khi xếp hạng #1 trong 10 thuật toán hàng đầu trong khai thác dữ liệu.<br>

Cây quyết định là đồ thị sử dụng phương pháp phân nhánh để minh họa mọi kết quả có thể xảy ra của một quyết định. Về mặt lập trình, chúng có thể được sử dụng để gán giá trị tiền tệ/thời gian hoặc các giá trị khác cho các kết quả có thể xảy ra để các quyết định có thể được tự động hóa.

Sau đây là ví dụ về cây quyết định.
<img src="https://github.com/quuynXp/Spam-email-classification/images/24_vi_du_cay_quyet_dinh.JPG">
<h3>Triển khai thuật toán Naive Bayes</h3>
Chúng tôi cũng đang so sánh các kết quả với các kết quả thu được từ Naive Bayes. Đây là một kỹ thuật phân loại dựa trên Định lý Bayes với giả định về sự độc lập giữa các yếu tố dự đoán. Nói một cách đơn giản, một bộ phân loại Naive Bayes giả định rằng sự hiện diện của một tính năng cụ thể trong một lớp không liên quan đến sự hiện diện của bất kỳ tính năng nào khác.
<img src="https://github.com/quuynXp/Spam-email-classification/images/23_thuat_toan_NaiveBayes.png">

<h2>Cách chạy?</h2>
<b>Nguồn: </b><a href="http://www.cs.waikato.ac.nz/ml/weka/downloading.html">Tải xuống và cài đặt Weka</a>
<h3>1. Chuẩn hóa dữ liệu</h3>
Bộ dữ liệu chúng tôi nhận được nằm trong 5180 tệp văn bản như được hiển thị trong ảnh chụp màn hình sau.
<img src="https://github.com/quuynXp/Spam-email-classification/images/1_so_do_thu_muc.png">
(3 thư mục trong một thư mục)
<img src="https://github.com/quuynXp/Spam-email-classification/images/2_noi_dung_file_data.csv.png">
(file csv)
<img src="https://github.com/quuynXp/Spam-email-classification/images/3_chuyen_file_csv_thanh_arff.png">
(Sau khi chuyển thành tệp arff)<br>

<h3>Triển khai thuật toán C4.5(J48)</h3>
Bây giờ chúng ta sẽ chọn và áp dụng bộ phân loại của mình như sau.
<img src="https://github.com/quuynXp/Spam-email-classification/images/8_chon_thuat_toan_j48.png">

Đầu tiên, chúng tôi đào tạo dữ liệu như sau bằng cách chọn tùy chọn đào tạo tập dữ liệu và chúng tôi nhận được kết quả sau.
<img src="https://github.com/quuynXp/Spam-email-classification/images/9_ket_qua_training_1.png">
<img src="https://github.com/quuynXp/Spam-email-classification/images/9_ket_qua_training_2.png">
<img src="https://github.com/quuynXp/Spam-email-classification/images/9_ket_qua_training_3.png">
Ở đây chúng ta có độ chính xác 98%. Sau đó, chúng ta tiếp tục đào tạo nó trên các phần trăm phân chia khác nhau và có được kết quả sau.
<img src="https://github.com/quuynXp/Spam-email-classification/images/12_ket_qua_training_66%.png">
Ở phần trăm phân chia 66%, chúng ta có độ chính xác 93%.
<img src="https://github.com/quuynXp/Spam-email-classification/images/13_ket_qua_training_80%.png">
Với tỷ lệ phần trăm chia tách 80%, chúng ta có được độ chính xác 94%.
<img src="https://github.com/quuynXp/Spam-email-classification/images/14_ket_qua_training_90%.png">
Với tỷ lệ phần trăm chia 90%, chúng ta có độ chính xác 89%.<br>
Bây giờ chúng ta quyết định thử nghiệm mô hình của mình, vì vậy chúng ta tạo tập dữ liệu thử nghiệm từ ID email của riêng mình như được hiển thị trong ảnh chụp màn hình sau.
<img src="https://github.com/quuynXp/Spam-email-classification/images/15_file_test.png">
Bây giờ chúng ta đưa tập dữ liệu thử nghiệm này cho mô hình đã được đào tạo của mình và chúng ta có được các dự đoán sau về tập dữ liệu này.
<img src="https://github.com/quuynXp/Spam-email-classification/images/16_kiem_thu_bang_file_test.png">
Mô hình của chúng ta đưa ra dự đoán như được hiển thị trong ảnh chụp màn hình ở trên.

<h3>Triển khai thuật toán Naive Bayes</h3>
Tôi lặp lại quy trình tương tự với Naive Bayes được hiển thị trong các ảnh chụp màn hình sau.
<img src="https://github.com/quuynXp/Spam-email-classification/images/17_ket_qua_thuat_toan_NaiveBayesMultinomailText_1.png">
<img src="https://github.com/quuynXp/Spam-email-classification/images/18_ket_qua_thuat_toan_NaiveBayesMultinomailText_2.png">
<img src="https://github.com/quuynXp/Spam-email-classification/images/19_ket_qua_thuat_toan_NaiveBayesMultinomailText_66%.png">
<img src="https://github.com/quuynXp/Spam-email-classification/images/20_ket_qua_thuat_toan_NaiveBayesMultinomailText_80%.png">
<img src="https://github.com/quuynXp/Spam-email-classification/images/21_ket_qua_thuat_toan_NaiveBayesMultinomailText_90%.png">


<h2>Kết luận</h2>
Gửi thư rác qua email là một kỹ thuật phổ biến nhưng có thể gây tổn hại nghiêm trọng đến quyền riêng tư của người dùng. Hiện nay, có nhiều công cụ chống thư rác có thể chống lại thư rác. Nhưng phân loại văn bản là một trong những cách tốt nhất để phát hiện thư rác. Chúng ta có thể cải thiện độ chính xác của nó bằng tập dữ liệu rất lớn và hạn chế các thuật toán của mình để bỏ qua các từ trong từ điển thông thường và phân loại các từ thư rác thường dùng.

<h2>Tài liệu tham khảo</h2>
[1] A. Anderson, M. Corney, O. de Vel, and G. Mohay."Identifying the 
Authors of Suspect E-mail". Communications of the ACM, 2001.<br> 
[2] Shlomo Hershkop, Ke Wang, Weijen Lee, Olivier Nimeskern, German 
Creamer, and Ryan Rowe, "Email Mining Toolkit Technical Manual". 
(June 2006) Department of Computer Science Columbia University. <br> 
[3] Bron, C. and J. Kerbosch. "Algorithm 457: Finding all cliques of an 
undirected graph." (1973). <br> 
[4] Ding Zhou et al and Ya Zhang, "Towards Discovering Organizational 
Structure from Email Corpus". (2005) Fourth International Conference on 
Machine Learning and Application. <br> 
[5]  Giuseppe Carenini, Raymond T. Ng and Xiaodong Zhou , "Scalable 
Discovery of Hidden Emails from Large Folders". Department of 
Computer Science, University of British Columbia, Canada. <br> 
[6] Hung-Ching Chen el al, "Discover The Power of Social and Hidden 
Curriculum to Decision Making: Experiments with Enron Email and 
Movie Newsgroups". Sixth International Conference on Machine 
Learning and Applications. <br> 