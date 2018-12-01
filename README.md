# Hướng dẫn Git cơ bản trên Linux

Việc trao đổi, xây dựng code Project trong một team là hết sức quan trọng. Cách đóng gói rồi gửi code qua một kênh trung gian rồi các thành viên khác phải tải về chỉnh sửa theo cách truyền thống đem lại nhiều bất tiện về mặt thời gian cũng như rối rắm trong quá trình quản lý. Git ra đời để giải quyết bài toán này.


## I. Mở đầu

### Git là gì? Github là gì?

**Git** là một hệ thống kiểm soát các phiên bản để theo dõi các thay đổi trong các tệp máy tính và phối hợp công việc trên các tệp đó giữa nhiều người. Nó chủ yếu được sử dụng để quản lý mã nguồn trong phát triển phần mềm và theo dõi các thay đổi của các tập tin.

**GitHub** là một dịch vụ cung cấp kho lưu trữ mã nguồn Git dựa trên nền web cho các dự án phát triển phần mềm. GitHub cung cấp cả phiên bản trả tiền lẫn miễn phí cho các tài khoản. Các dự án mã nguồn mở sẽ được cung cấp kho lưu trữ miễn phí.

Ngoài ra, Github còn được goi là mạng xã hội của giới IT khi mà bạn có thể lên đây và học hỏi nhiều kĩ năng từ những bài viết từ nhiều thành viên của cộng đồng. Cũng như hỏi đáp những thắc mắc, vấn đề trong việc fix code.

### Tại sao phải sử dụng Git và Github
- Dễ sử dụng, an toàn và nhanh chóng.
- Giúp quy trình quản lý, update, rollback mã nguồn một cách hiệu quả và đồng bộ.
- Tính di động làm việc ở bất cứ đâu chỉ với việc clone mã nguồn. 
- ....

### Cần làm gì để sử dụng Git và Github
Truy cập vào trang chủ [Github](https://github.com/) và tạo một tài khoản.

## II. Nội dung chi tiết.
### 1. Cài đặt Git và thiết lập ban đầu.
Tùy vào phiên bản Linux thì sẽ có cách cài đặt khác nhau: 

**Debian/Ubuntu/Linux mint:**
```sh
sudo apt-get install git 
```
**RedHat/CentOS/Fedora:**
```sh
sudo yum install git
```
### Thiết lập chứng thực
Ngay sau khi cài đặt Git thành công, việc đầu tiên chúng ta cần làm là khai báo tên và địa chỉ email trong file cấu hình. Sử dụng lệnh sau để khai báo:

```sh
$ git config --global user.name "Your name"
$ git config --global user.email "Your email"
```
Để kiểm tra việc thiết lập đã được chấp nhận hay chưa ta làm như sau: 
```sh
$ cat ~/.gitconfig
[user]
   name = Your name
   email = Your email
```

### 2. Cách tạo một repository
Repository là một kho chứa các mã nguồn của bạn. Có 2 loại kho chứ đó là Local Repository(Kho chứa trên máy tính cá nhân) và Remote Repository(Kho chứa trên máy tính từ xa). Ở bài này Remote Repository tôi áp dụng trên Github.

#### Local Repository
Bạn cần truy cập đến thư mục chứa mã nguồn bằng lệnh:
```sh
$ cd duong_dan_den_thu_muc
```
Sau đó sử dụng lệnh sau để tạo repository trên thư mục đó:
```sh
$ git init ten_thu_muc
Initialized empty Git repository in /..Đường dẫn đến thư mục của bạn../.git/
```
Thư mục .git chứa những thông tin của khó chứa. Chúng ta không cần quan tâm đến thư mục này.

#### Remote Repository
Đăng nhập vào trang [Github](https://github.com/) và click vào dấu **+** chọn **New Repository**:

Các tùy chọn còn lại bạn có thể chọn hoặc không. Click vào **Create repository** nếu như thiết lập xong.


### 3. Vòng đời trạng thái của tập tin

[Image]

**Untracked**: Là trạng thái mà các tập tin chưa được đăng kí làm việc với Git. 

**Tracked**: Là trạng thái mà các tập tin đã đăng kí với  Git. Git sẽ tự động phát hiện thay đổi khi có bất kì tác động nào vào file đó. 

Các trạng thái **Unmodified**(chưa chỉnh sửa), **Modified**(đã chỉnh sửa) và **Staged**(Đã sẵn sàng để Commit) là trạng thái phụ của **Tracked**.

**_Làm sao để đăng kí một tập tin với Git?_**
Khi có bất kì một tập tin được thêm mới vào trong thư mục làm việc của bạn thì nó sẽ ở trạng thái Untracked. Bây giờ ta thử tạo một tập tin mới tên là index.html. Sau đó sử dụng lệnh sau để xem trạng thái của Git trong thư mục làm việc.

```sh
$ touch index.html
$ git status 
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	index.html
nothing added to commit but untracked files present (use "git add" to track)
```
Từ kết quả cho thấy file index.html đang ở trạng thái Untracked. Để đưa nó về Tracked bạn phải sử dụng lệnh git add ten_file. Sau đó dùng kiểm tra trạng thái của file:
```sh
$ git add index.html
$ git status
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   index.html
```
Kết quả hiển thị như trên chính tỏ file đã chuyển sang trạng thái Tracked thành công. 

**Lưu ý**: với file lần đầu tiên đăng kí với Git thì đồng nghĩa với việc nó được chuyển thẳng về trạng thái **Staged**.

### 4. Một số hoạt động trên Git thường sử dụng.

To be continue ...!
