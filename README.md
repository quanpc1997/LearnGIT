# Hướng dẫn Git cơ bản trên Linux

Việc trao đổi, xây dựng code Project trong một team là hết sức quan trọng. Cách đóng gói rồi gửi code qua một kênh trung gian rồi các thành viên khác phải tải về chỉnh sửa theo cách truyền thống đem lại nhiều bất tiện về mặt thời gian cũng như rối rắm trong quá trình quản lý. Git ra đời để giải quyết bài toán này.


# . Mở đầu

## Git là gì? Github là gì?

**Git** là một hệ thống kiểm soát các phiên bản để theo dõi các thay đổi trong các tệp máy tính và phối hợp công việc trên các tệp đó giữa nhiều người. Nó chủ yếu được sử dụng để quản lý mã nguồn trong phát triển phần mềm và theo dõi các thay đổi của các tập tin.

**GitHub** là một dịch vụ cung cấp kho lưu trữ mã nguồn Git dựa trên nền web cho các dự án phát triển phần mềm. GitHub cung cấp cả phiên bản trả tiền lẫn miễn phí cho các tài khoản. Các dự án mã nguồn mở sẽ được cung cấp kho lưu trữ miễn phí.

Ngoài ra, Github còn được goi là mạng xã hội của giới IT khi mà bạn có thể lên đây và học hỏi nhiều kĩ năng từ những bài viết từ nhiều thành viên của cộng đồng. Cũng như hỏi đáp những thắc mắc, vấn đề trong việc fix code.

## Tại sao phải sử dụng Git và Github
- Dễ sử dụng, an toàn và nhanh chóng.
- Giúp quy trình quản lý, update, rollback mã nguồn một cách hiệu quả và đồng bộ.
- Tính di động làm việc ở bất cứ đâu chỉ với việc clone mã nguồn. 
- ....

## Cần làm gì để sử dụng Git và Github
Truy cập vào trang chủ [Github](https://github.com/) và tạo một tài khoản.

# B. Nội dung chi tiết.
## I. Cài đặt Git và thiết lập ban đầu.
Tùy vào phiên bản Linux thì sẽ có cách cài đặt khác nhau: 

**Debian/Ubuntu/Linux mint:**
```sh
sudo apt-get install git 
```
**RedHat/CentOS/Fedora:**
```sh
sudo yum install git
```
## II. Thiết lập chứng thực
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

## III. Cách tạo một repository
Repository là một kho chứa các mã nguồn của bạn. Có 2 loại kho chứ đó là Local Repository(Kho chứa trên máy tính cá nhân) và Remote Repository(Kho chứa trên máy tính từ xa). Ở bài này Remote Repository tôi áp dụng trên Github.

### 1. Local Repository
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

### 2. Remote Repository
Đăng nhập vào trang [Github](https://github.com/) và click vào dấu **+** chọn **New Repository**:

Các tùy chọn còn lại bạn có thể chọn hoặc không. Click vào **Create repository** nếu như thiết lập xong.

**Gán tên cho remote:**
```sh
$ git remote add ten_remote url_repository
```
Từ nay trên máy của bạn, bạn có thể dùng tên này thay cho url của repository.

**Kiểm tra tên remote:**
```sh
$ git remote -v
example	https://github.com/skybyte0297/LeanGIT.git (fetch)
example	https://github.com/skybyte0297/LeanGIT.git (push)
```

**Đổi tên remote:**
```sh
$ git remote rename ten_hien_tai ten_muon_thay_doi
```

## IV. Branch - Kĩ thuật phân nhánh.
Một teamwork cùng làm một project với mỗi thành viên làm những chức năng khác nhau. Việc các thành viên phải clone từ reposirory về chỉnh sửa rồi đẩy lên repository gây mất thời gian mà laị khó có thể đồng bộ hóa. Phân nhánh(branch) trong Git giải quyết triệt để bài toán trên.

Khi bắt đầu tạo một repository thì tự động chúng là đang ở nhánh _master_. Đây là branch chính chứa toàn bộ mã nguồn trong repository. Ở nhánh phụ ta có thể thay đổi tùy thích mà không ảnh hưởng đến các nhánh khác.

[Image]

#### Tạo mới một Branch
```sh
$ git branch ten_nhanh
```

#### Chuyển sang một Branch khác
```sh
$ git checkout ten_nhanh
```

Bây giờ chúng ta thử tạo mới 1 tập tin docs.txt ở nhánh _master_ rồi sau đó tạo một nhánh mới là _mybranch_ và sửa tập tin mới trên nhánh đó và xem liệu rằng có sự thay đổi nào xảy ra không khi tệp tin trên nhánh _mybranch_ bị thay đổi.

```sh
$ echo "Nhanh Master" > docs.txt
$ git add docs.txt
$ git commit -m "Nhanh Master"
[master (root-commit) 42d294c] Nhanh Master
 1 file changed, 1 insertion(+)
 create mode 100644 docs.txt
$ git branch mybranch
$ git checkout mybranch
Switched to branch 'mybranch'
$ git add docs.txt
$ echo "Nhanh MyBranch" >> docs.txt
$ git add docs.txt
$ git commit -m "Nhanh MyBranch"
[mybranch 7746ff8] Nhanh MyBranch
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Và bạn chuyển về nhánh _master_ để xem kết qủa. Việc chỉnh sửa trên nhánh phụ không ảnh hưởng gì đến nhánh chính

### Gộp nhánh
Trở lại bài toán teamwork lúc đầu, sau khi mọi người hoàn thành nhiệm vụ của mình. Giờ là lúc đồng bộ hóa code. Bằng cách gộp nhánh, code từ các nhánh sẽ được hợp lại ở nhánh master.

Đầu tiên bạn cần trở về nhánh _master_:
```sh
$ git checkout master 
```
Tiếp theo gộp nhánh vào nhánh _master_(ở đây là nhánh mybranch):
```sh
$ git merge mybranch
```
Bạn kiểm tra lại thì nội dung của file docs.txt đã bị thay đổi theo đúng nhánh mybranch.

#### Xóa một Branch
```sh
$ git branch -d ten_nhanh
```
**Lưu ý**: Để xóa được một nhánh thì chúng ta cần gộp với nhánh khác trước sau đó mới xóa được. 


## V. Vòng đời trạng thái của tập tin

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

## VI. Một số hoạt động thường sử dụng.

### 1. Commit
- Commit được hiểu đơn giản là một hành động lưu lại một bản chụp(snapshot) của một sự thay đổi nào đó trong tập tin được đăng kí với Git.
- Mỗi lần commit lịch sử chỉnh sửa sẽ được ghi lại cùng với mã nguồn tại thời điểm đó. Việc này rất thuận tiện nếu chúng ta muốn sử dụng lại một phiên bản cũ nào đó. 
- **Để** có thể **commit** được một tập tin nào đó chúng ta **cần đưa tập tin đó về trạng thái Staged**.

Câu lệnh dưới đây dùng để commit một file:
```sh
$ git commit -m "lời nhắn".
```

**Để xóa commit trước và commit lại** ta thêm tham số *--amend*:
```sh
$ git commit --amend -m "Lời nhắn"
```

### 2. Xem log.
- Để xem lại lịch sử các lần commit trước ta sử dụng lệnh:
```sh
$ git log
```
- Để tối ưu việc đọc log bạn có thể thêm một vài tham số sau:
	* *-p*			: Hiển thị thêm thông tin chi tiết của từng log.
	* *--since, --after*	: Xem các lần commit kể từ ngày nhất định.
	* *--until*		: Xem các lần commit trước từ ngày nhất định.
	* *--author*		: Xem các lần commit của một người nào đó.
	* *--grep*		: Lọc các chuỗi trong log và in ra.
	
	* **_--pretty_**	: Lọc theo _%tag_
	
		Danh sách các _%tag_:
			%H –  Commit hash
			%h – Abbreviated commit hash
			%T – Tree hash
			%t – Abbreviated tree hash
			%P – Parent hashes
			%p – Abbreviated parent hashes
			%an – Author name
			%ae – Author e-mail
			%ad – Author date (format respects the –date=option)
			%ar – Author date, relative
			%cn – Committer name
			%ce – Committer email
			%cd – Committer date
			%cr – Committer date, relative
			%s – Subject


### 3. Tag
- Commit quá nhiều khiến quá trình quản lí trở lên khó khăn. Đặt tag cho commit sẽ giải quyết được vấn đề này. Sử dụng tag giúp cho việc diff một cách dễ dàng mà không cần nhớ mã checksum. Ngoài ra nó còn tốt cho việc phân nhánh sau này. 
- Để hiển thị Tag đã gắn vào commit:
```sh
$ git show ten_tag
```

- Trong Git có hai kiểu tag chính đó là:
	* **Lightweight Tag**	: Các tag này chỉ đơn thuần là đánh dấu snapshot của commit.
	* **Annotated Tag**	: Với tag này, bạn có thể đặt tiêu đề cho tag, và khi xem nó sẽ có thông tin về người tag, ngày tag,….

#### Lightweigh Tag:
- Để tạo ra **Lightweigh Tag** ta sử dụng câu lệnh sau **_git tag ten_Tag_**. Ví dụ _ten_tag_ là V1:
```sh
$ git tag V1
$ git tag
V1
```
- **_Lưu ý_**:Tag V1 sẽ được tự động gắn vào commit gần nhất.
```sh
$ git show V1
 git show V1
commit 52cfc8f2dabd262bc96c39a190220c1cb2532a64 (HEAD -> master, tag: V1)
Author: unknown <skybyte0297@gmail.com>
Date:   Wed Dec 5 10:17:49 2018 +0700

    BTL Media

diff --git a/01.png b/01.png
new file mode 100644
index 0000000..95baed8

```

#### Annotated Tag
- Để tạo ra **Annotated Tag** ta sử dụng lệnh **_git tag -a ten_Tag -m "Loi_nhan"_**. 

Ví dụ:
```sh
$ git tag -a Ver01 -m "Su dung Grubcut"
$ git show Ver01
tag Ver01
Tagger: unknown <skybyte0297@gmail.com>
Date:   Wed Dec 5 10:26:12 2018 +0700

Su dung Grubcut

commit 52cfc8f2dabd262bc96c39a190220c1cb2532a64 (HEAD -> master, tag: Ver01, tag: V1)

```

#### Thêm Tag cho commit cũ
Đầu tiên ta cần phải biết mã checksum của từng commit. Sử dụng **_git log_** với tham số **_--pretty_** với giá trị **_oneline_**.
```sh
$ git log --pretty=oneline
d5a599e3385a8fc7a65958ed50bc8b54666b45ad Commit for Annotated Tag
05193375f7a7c1295fd26c6388d81e188f405b0b Added a new tag
435f642f951fbab1037fc2feef239ab26d6e6115 Added faq.html
6904d5232bf90821068279311e205e3e1ff929f1 Initial commit
```

Và bây giờ mình có thể đặt tag cho commit Initial commit thì sẽ khai báo một đoạn mã checksum của nó vào lệnh **_git tag -a ten_tag ma_checksume -m "Lời nhắn"_**  như sau. 
```sh
$ git tag -a v0.0 6904d -m "Tag for inintial commit"
$ git tag
v0.0
v1.0
v1.0-an 
```
#### Xóa Tag
Sử dụng **_git tag -d ten_Tag_**:
```sh
$ git tag -d V1
```
### 4. Clone
Khi muốn chép toàn bộ dữ liệu từ nhánh master trên repository về máy của bạn:
```sh
$ git clone url_repository/ten_da_gan_cho_repository
```
Lệnh này tự động tạo một nhánh master trên _local repository_ của bạn.

**Để clone một nhánh không phải _master_ ta làm như sau:**
```sh
$ git clone --single-branch -b ten_branch url_repository/ten_da_gan_cho_repository
```
Ví dụ ở đây tôi muốn clone nhánh mygit tử repository của tôi:
```sh
$ git clone --single-branch -b mygit https://github.com/skybyte0297/LeanGIT.git
Cloning into 'LeanGIT'...
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 7 (delta 0), reused 7 (delta 0), pack-reused 0
Unpacking objects: 100% (7/7), done.
```

### 5. Pull
Muốn update một phiên bản mới gộp vào nhánh bạn đang làm việc mà không phải tản lại hẳn cả phiên bản mới về, ta gùng lệnh _git pull_
```sh
$ git pull url_repository/ten_da_gan_cho_repository
```

### 6. Push
Muốn đẩy một tệp/thư mục từ local repository lên github thì ta dùng lệnh _git push_
```sh
$ git push url_repository/ten_da_gan_cho_repository ten_branch_muon_push
```


To be continue ...!
