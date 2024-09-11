# Mục tiêu

- Phổ cập kiến thức về git
- Cung cấp ví dụ trực quan liên quan đến quá trình làm việc với dự án mở git
# Git là gì ?

Git là một hệ thống quản lý phiên bản theo dõi thay đổi được thực hiện lên một nhóm các tệp tin (files). Mục tiêu chính của Git là lưu lại lịch sử của nhóm các tệp tin này trong suốt vòng đời của chúng. 

*Có thể hiểu một cách sai lầm nhưng lại rất hợp lý, rằng Git giống như bản ghi của một vũ trụ trong dòng thời gian, chúng ta có thể quay về quá khứ của vũ trụ này, hoặc nhìn vào quá khứ của một sự vật trong vũ trụ đấy, hay là tạo ra một vũ trụ song song với một số khác biệt rồi lại cho chúng nhập vào nhau.*

Bản chất của Git chính là cách mà nó lưu trữ và xử lý thông tin. Đối với các hệ thống quản lý phiên bản (VCS - Version Control System) khác, việc lưu trữ thông tin được làm dưới dạng một danh sách các thay đổi của files (a list of file-based changes), cách xử lý thông tin của các VCS này là chúng sẽ lưu đối tượng dưới dạng danh sách các files và thay đổi được thực hiện lên từng file theo thời gian. 

Mặt khác, Git không lưu trữ và xử lý thông tin theo cách này, mà gần giống như một chuỗi các bản chụp của hệ thống file. Với Git, mỗi khi người dùng lưu lại trạng thái của project, Git lưu lại một bản chụp của tất cả các files tại thời điểm đấy và cả các tham chiếu tới các bản chụp này. Và để trở nên hiệu quả, nếu một hay nhiều files không có thay đổi, Git không lưu lại files này trong các bản chụp về sau mà chỉ là một liên kết về phiên bản có thay đổi gần nhất của files đó nằm ở bản chụp trước. Có thể hiểu thông qua ảnh minh hoạ sau:

![illu1](https://i.imgur.com/lv6lEHy.png)

*Ở bản chụp version 2, với sự thay đổi của file A và C, phiên bản mới được lưu lại là A1 và C1, tuy nhiên ,file B không có thay đổi, thì đối tượng lưu trữ của file B chỉ là một liên kết về phiên bản file B lưu ở bản chụp version 1*

Phần lớn các thao tác của Git sẽ được diễn ra ở mức nội bộ (local) trên chính máy tính của người dùng, chỉ với bước `push` thì git khi này sẽ được đẩy lên máy chủ (ví dụ như Github). 

*Ví dụ, nếu máy tính của bạn tạm thời không có kết nối Internet, các bạn vẫn có thể làm việc bình thường, thực hiện các thay đổi bình thường, cho đến khi có lại kết nối Internet, `push` sẽ đồng bộ git từ máy tính lên máy chủ*

Mọi thứ trong Git đều được tổng kiểm tra (checksummed) trước khi lưu trữ và được tham chiếu tới bằng chính mã kiểm tra (checksum) này. Việc thay đổi nội dung của một tệp tin hay thư mục để mà Git không biết tới là không thể nào. Người dùng sẽ làm quen với việc nhìn thấy các đoạn mã SHA-1 hash - đây chính là cách kiểm tra của Git. Cơ sở dữ liệu của Git cũng không lưu trữ thông tin theo tên mà bằng giá trị hash SHA-1 của thông tin.

Khi thực hiện các thay đổi lên một Git, Git sẽ chỉ *thêm* dữ liệu vào cơ sở dữ liệu, rất khó để có thể huỷ bỏ hay xoá đi hành động đã được GIt ghi lại trong lịch sử của một project.

*Ví dụ, người dùng bổ sung một file Readme.md vào project, bản ghi mới nhất của project sẽ phản ánh hành động thêm file Readme.md và cơ sở dữ liệu của Git sẽ ghi lại hành động này cùng với nội dung của file. Sau đó, người dùng xoá file Readme.md và lưu Git, tới đây, Git không huỷ bỏ hành động từ trước mà sẽ thực hiện một bản ghi mới phản ánh việc xoá file Readme.md (không còn file Readme.md trong project), nhưng bây giờ cơ sở dữ liệu của Git vẫn sẽ ghi lại hành động xoá file và liên kết tới nội dung của file bị xoá (nội dung của file bị xoá này được ghi lại ở bản chụp trước khi xoá file).*

# Ba trạng thái của tệp tin trong git

Mỗi tập tin trong Git sẽ được quản lý dựa trên 3 trạng thái: `committed` , `modified` và `staged` . 

- `committed` - dữ liệu (bao gồm nội dung của file và thay đổi lên nó) đã được lưu trữ an toàn trong cơ sở dữ liệu
- `modified` - Nội dung của file (nếu tạo mới) và thay đổi lên nó chưa được đưa vào cơ sở dữ liệu (chưa được `commit`)
- `staged`- đã đánh dấu commit phiên bản hiện tại của một tập tin đã chỉnh sửa vào lần commit tới

Điều này cũng dẫn đến một dự án git sẽ có 3 phần riêng biệt : thư mục git (git repository), thư mục làm việc (working directory) và khu vực tổ chức (staging area). 

![3stage](https://git-scm.com/book/en/v2/images/areas.png)
Thư mục Git - .git directory - Git repository : Là nơi Git lưu trữ các siêu dữ liệu (metadata - mô tả về dữ liệu, cung cấp thông tin về các thuộc tính, đặc điểm và các phần tử khác của dữ liệu) và cơ sở dữ liệu cho project. Đây là phần được sao lưu (clone) về khi chúng ta tạo bản sao của một repo 

Thư mục làm việc - working directory : Là phiên bản của dự án, được kéo về từ cơ sở dữ liệu được nén lại trong thư mục Git và lưu trên ổ cứng máy tính cho người dùng sử dụng hoặc chỉnh sửa

Khu vực tổ chức là một tập tin đơn giản trong thư mục Git, chứa thông tin về những gì sẽ được commit tiếp theo. Còn được biết tới là index, nhưng staging area là tên chuẩn.

Có thể hiểu workflow cơ bản như sau:
- Người dùng thay đổi các tệp tin của project trong thư mục làm việc
- Người dùng tổ chức tệp tin, tạo mới bản chụp của project và đưa nó vào khu vực tổ chức
- commit, bản chụp của project sẽ được đưa vào thư mục Git, lưu trữ vĩnh viễn trong lịch sử của thư mục Git

Trong quá trình làm việc với project, người dùng cũng có thể tạo một nhánh (branch) của project để phát triển các tính năng mới hoặc các thay đổi được cô lập với nhánh chính của project. Chỉ khi nào các tính năng được hoàn chỉnh và các thay đổi được thống nhất, nhánh tách ra ban đầu này sẽ được nhập (merge) trở lại nhánh chính và các thay đổi hay phát triển được thực hiện ở nhánh tách cũng sẽ được nhập vào project. 

*Project sau khi đã tách nhánh giống như tồn tại trong một vũ trụ song song với dòng thời gian của chính nó*

Khi làm việc với các dự án mã nguồn mở với sự tham gia của nhiều cá nhân, việc phân nhánh khi làm việc là bắt buộc để đảm bảo tổ chức cũng như an ninh cho dự án.
# Làm việc với GitHub

Với sự xuất hiện của GitHub, GitHub được hiểu là một "remote repository" - nó đơn giản là phiên bản project của người dùng được lưu (host) trên mạng Internet (public - open source , hoặc private - open source) hoặc một mạng bảo mật không public. Với workflow như sau:

Người dùng đầu tiên, chủ của repo:

- Triển khai remote repository trên GitHub và cấu hình repository này
- `clone`, tạo sao lưu trên máy tính cá nhân
- Đưa các tập tin đầu tiên của project vào thư mục làm việc
- Tổ chức tệp tin, tạo bản chụp đầu tiên của project và đưa vào khu vực tổ chức
- `commit`, bản chụp của project sẽ được đưa vào thư mục git
- `push`, đồng bộ thay đổi lên remote repository 

Giờ remote repository sẽ tồn tại và có thể được truy cập trên GitHub qua một đường dẫn url, bây giờ, một cá nhân tham gia vào project sẽ cần làm những việc sau:

- Fork repo ra một phiên bản của bản thân
- `clone`, tạo sao lưu trên máy tính cá nhân
- `branch` và `checkout` ,tạo một nhánh git riêng của bản thân để thực hiện các thay đổi
- Thay đổi, chỉnh sửa các tệp tin
- Tổ chức tệp tin, tạo bản chụp đầu tiên của nhánh project và đưa vào khu vực tổ chức
- `commit`, bản chụp của nhánh sẽ được đưa vào thư mục git
- `push`, đồng bộ nhánh tách lên remote repository
- Tạo pull request - yêu cầu chủ repo xem xét và đánh giá công việc được thực hiện trên nhánh tách

Bây giờ, chủ repo có thể làm:

- Xem pull request, đánh giá công việc của người tham gia vào project
- Nếu thoả mãn, chủ repo sẽ merge nhánh riêng của người tham gia vào nhánh chính của project, nếu không, từ chối merge 

Nếu tồn tại một người tham gia vào project khác, nhưng người tham gia này ngủ trong lúc pull request trên được đánh giá và merge, người này cần:

- `pull` , kéo về những thay đổi được thực hiện lên nhánh chính của project và merge vào nhánh riêng
- Thay đổi, chỉnh sửa các tệp tin
- Tổ chức tệp tin, tạo bản chụp đầu tiên của nhánh project và đưa vào khu vực tổ chức
- `commit`, bản chụp của nhánh sẽ được đưa vào thư mục git
- `push`, đồng bộ nhánh tách lên remote repository
- Tạo pull request - yêu cầu chủ repo xem xét và đánh giá công việc được thực hiện trên nhánh tách

Trong trường hợp trên hai nhánh của project xuất hiện thay đổi lên cùng một tệp tin, đây là khi "merge conflict" xảy ra, và người dùng cần giải quyết mâu thuẫn trước khi có thể merge , hoặc từ nhánh chính vào nhánh riêng đối với người tham gia, hoặc từ nhánh riêng vào nhánh chính đối với chủ repo.

Đây là khi tồn tại một người tham gia vào project khác, cũng đang hoạt động và chỉnh sửa cùng một file, cả hai cùng thực hiện pull request,  bây giờ sẽ có merge conflict giữa hai người tham gia project, nó có thể được xử lý bởi cả chủ repo, hoặc người tham gia. Với một project được phân chia công việc rõ ràng với một workflow hoàn chỉnh, merge conflict sẽ khó xảy ra, hoặc nếu xảy ra sẽ dễ xử lý.
# Triển khai một Git 

Từ bây giờ, quá trình hướng dẫn sẽ được nhập vai, nêu lại toàn bộ workflow của một project dưới các góc nhìn khác nhau của chủ repo và các cá nhân tham gia. Và ví dụ nhập vai sẽ liên quan tới dự án dịch thuật mã nguồn mở.

Cá nhân `A` - chủ repo muốn bắt đầu thực hiện project. 
`A` lên trang web của nền tảng GitHub và tạo một repository tên `xpho-project`. `A` cài đặt để nhánh chính của repository tên là `main`, tên này có thể đặt tuỳ ý, nhưng `A` quyết định đặt theo gợi ý mặc định.

*Repository này sẽ đóng vai trò là một remote repository, bản chất khác nhau ở một remote repository và repository trên máy tính của người dùng là remote repository sẽ không để thực hiện các thay đổi. Nó sẽ là điểm kết nối chung cho những người tham gia project, một repository chung phản ánh trực tiếp tiến độ của project*

![git1](https://i.imgur.com/CBM43lF.png)

Bây giờ `Ver 1` sẽ chưa có bất kỳ dữ liệu gì, nó là một repository trống, hoặc nếu như `A` đã tích vào lựa chọn tạo file README.md thì bây giờ trong repository sẽ chỉ có README.md

```cmd
// github.com: Ver 1
xpho-project
	README.md
```

`A` muốn triển khai git này bằng việc đưa lên một số file đầu tiên của dự án, `A` quyết định đưa lên một file $\text{TeX}$ `xpho.tex` . `A` có thể : 
- Hoặc sử dụng tính năng upload file của GitHub và đưa lên remote repository - chức năng này tương ứng với việc clone repo về máy tính, thêm file vào rồi commit, sau đó push lên remote repository. Nhưng cách làm này phản khoa học, do trước sau gì `A` cũng cần clone repo về để làm việc.
- `A` chọn sao lưu repository về máy tính cá nhân , thực hiện thay đổi lên project trong working directory, tạo một bản chụp của trạng thái này rồi đồng bộ trở lại remote repository. Bằng cách này, `A` có thể tiếp tục làm việc với project về sau bằng phương pháp này. `A` thực hiện như sau:

`A` cài đặt [git CLI](https://git-scm.com/downloads) (không khuyến cáo) hoặc [GitHub CLI](https://cli.github.com/) , chỉ cần cài đặt một trong hai. 

Trước tiên, `A` cài đặt tên người dùng và email cho git, bật Command Prompt và gõ

```cmd
git config --global user.email "A@gmail.com"

git config --global user.name "A"
```

`A` đi tới một thư mục trong máy tính, `A` tự tin thư mục này dễ tiếp cận và phân vùng ổ cứng chứa thư mục này có đủ dung lượng. `A` cảm thấy thoải mái với việc clone vào ổ `D:`  .`A` sử dụng command prompt, trỏ về ổ D với 
```cmd
Microsoft Windows [Version 10.0.19045.4780]
(c) Microsoft Corporation. All rights reserved.

C:\Users\A> d:
D:\> 
```
Sau đó, `A` trở lại Github và lấy đường dẫn của remote repository, sau đó điền lệnh vào command prompt
- Nếu `A` đã tải git CLI, `A` có thể sử dụng:
```cmd
D:\> git clone https://github.com/A/xpho-project.git 
```
- Nhưng `A` đã tải  GitHub CLI (khuyến cáo), vì thế `A` sử dụng:
```cmd
D:\> gh repo clone A/xpho-project
Cloning into 'xpho-project'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done.
```

*Ở đây người dùng có thể dính lỗi `'git' is not recognized as an internal or external command, operable program or batch file.`. Phương án xử lý, có thể hỏi riêng mình hoặc xem tại đây [Error "'git' is not recognized as an internal or external command" - Stack Overflow](https://stackoverflow.com/questions/4492979/error-git-is-not-recognized-as-an-internal-or-external-command)*

Sau đó, `A` đăng nhập GitHub của mình với GitHub CLI. `A` làm theo prompt, chọn đăng nhập vào GitHub.com, chọn protocol cho các hoạt động Git là `HTTPS`, `Y` với sử dụng GitHub credentials và `Login with a web browser`
```cmd
D:\>gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations on this host? HTTPS
? Authenticate Git with your GitHub credentials? Yes
? How would you like to authenticate GitHub CLI? Login with a web browser

! First copy your one-time code: F0D5-1F94
Press Enter to open github.com in your browser...
✓ Authentication complete.
- gh config set -h github.com git_protocol https
✓ Configured git protocol
✓ Logged in as A
```

Bây giờ tiếp tục với repo, trong ổ D sẽ xuất hiện một thư mục tên `xpho-project`, khi truy cập thì `A` có thể thấy thư mục này có một thư mục tên `.git` và `README.md` được thêm từ đầu

```cmd
// Máy tính cá nhân: Ver 1
xpho-project
	.git
	README.md
```

Tới đây, `A` copy file cần đẩy lên GitHub vào thư mục `xpho-project` bằng cách kéo thả hoặc copy paste (`Ctrl + C // Ctrl +V`) file `xpho.tex` , bây giờ, thư mục sẽ như sau

```cmd
// Máy tính cá nhân: Ver 1
xpho-project
	.git
	README.md
	xpho.tex
```

Với kiến thức về git, `A` thêm thay đổi vào khu vực tổ chức - staging area với lệnh `git add .` , lệnh trên sẽ đưa toàn bộ các thay đổi vào staging area. Sau đó `A` commit nó vào git với lệnh `git commit -m "Commit số một, thêm xpho.tex"` , trong đó flag `-m "..."` quyết định mô tả ngắn gọn của commit. 
Trước tiên cần phải trỏ vào thư mục git đã được clone về với `cd xpho-project`

```cmd
D:\>cd xpho-project
D:\xpho-project> git add .
D:\xpho-project>git commit -m "Commit số một, thêm xpho.tex"
[main 888b058] Commit số một, thêm xpho.tex
 1 file changed, 245 insertions(+)
 create mode 100644 xpho.tex
```

`A` thắc mắc, tại sao trên GitHub vẫn chưa có file `xpho.tex`? 

![img1](https://i.imgur.com/0VzXZ6v.png)

Đấy là bởi vì thay đổi chỉ mới được thực hiện trên thư mục làm việc - working directory trên máy tính của `A` rồi được commit lên thư mục git trên máy tính chứ chưa được đồng bộ lên remote repository, `A` thực hiện thêm bước `git push`, với `origin main` để đặc biệt chỉ ra chúng ta đang push lên tên của remote repository, `origin` là tên gọi mặc định và `main` là tên nhánh chính mà chúng ta cài đặt khi tạo remote repository trên GitHub.
```cmd
D:\xpho-project>git push origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 3.73 KiB | 3.73 MiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/Duy247/xpho-project.git
   b2b04ca..888b058  main -> main
```

Tới đây, có thể thấy file đã được đưa lên GitHub

![img2](https://i.imgur.com/jVHC0sH.png)

Và thư mục `xpho-project` chính thức là bản chụp commit số 2
```cmd
// Máy tính cá nhân: Ver 2
xpho-project
	.git
	README.md
	xpho.tex
```

![git2](https://i.imgur.com/0IW9xDq.png)

Tới đây `A` nghĩ ra, chỉ bản thân mình được phép push thẳng lên nhánh chính `main`, còn người khác phải thông qua `A` mới làm được điều này, `A` quyết định cấu hình thêm các bộ luật cho remote repository trên GitHub để làm điều này. 

`A` tiến vào cài đặt của remote repo trên GitHub và vào cài đặt cho nhánh `Branches`
![img3](https://i.imgur.com/HqBuNQQ.png)

`A` chọn `Add branch ruleset`

`A` đặt ruleset như nhau

![img4](https://i.imgur.com/gcqMK9y.png)

Organization admin và Repository admin ở đây hiểu chính là chủ tài khoản GitHub, do git lưu trên GitHub về bản chất cũng là một thư mục git lưu trên máy tính, với người dùng chủ là tài khoản GitHub đã tạo ra repo này. Vì thế, chỉ có `A`, khi đăng nhập GitHub có quyền bỏ qua bộ luật và thực hiện tuỳ thích các tác động lên remote repository trên GitHub.

Branch target sẽ là default branch

![img5](https://i.imgur.com/gcBMsWD.png)

Bộ luật cho Branch 
![img6](https://i.imgur.com/DBlKfRa.png)

![img7](https://i.imgur.com/yKfyz2F.png)

Với bộ luật này, quyền quyết định thay đổi lên repo lưu trên GitHub nằm toàn bộ ở `A` . Khi một người tham gia dự án muốn được đóng góp, họ buộc phải tạo ra branch riêng của bản thân, thực hiện thay đổi rồi lập một pull request, các thay đổi này cần phải được xem xét bởi `A` và có sự đồng ý thì mới được merge vào branch chính `main` . 

Tới đây là xong, `A` công bố đường dẫn git của remote repository `xpho-project` tới cộng đồng và chờ những người tham gia vào dự án.

# Tham gia đóng góp một git 
Người dùng `B`, được kêu gọi bởi `A` tham gia vào dự án `xpho-project`. Người dùng `B` mới tải [GitHub CLI](https://cli.github.com/) về , đăng nhập GitHub với GitHub CLI của bản thân 
```cmd
D:\>gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations on this host? HTTPS
? Authenticate Git with your GitHub credentials? Yes
? How would you like to authenticate GitHub CLI? Login with a web browser

! First copy your one-time code: 3BC3-F0DH
Press Enter to open github.com in your browser...
✓ Authentication complete.
- gh config set -h github.com git_protocol https
✓ Configured git protocol
✓ Logged in as B
```

và clone repo về máy tính cá nhân với
```cmd
D:\> gh repo clone A/xpho-project
Cloning into 'xpho-project'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done.
```
Người dùng `B` do thiếu kinh nghiệm và kiến thức sử dụng Git và GitHub, đã thực hiện thay đổi ngay lập tức lên các file rồi muốn commit và push

```cmd
D:\xpho-project> git add .
D:\xpho-project>git commit -m "Push without pull request"
[test fdf9784] Push without pull request 
1 file changed, 0 insertions(+), 0 deletions(-) 
create mode 100644 test.txt
```

Ngay khi push lên `main`, người dùng `B` dính lỗi

```cmd
D:\xpho-project>git push origin main
remote: Permission to A/xpho-project.git denied to B.
fatal: unable to access 'https://github.com/A/xpho-project.git/': The requested URL returned error: 403
```

Lý do ở đây là vì `B` vốn không có quyền tác động lên repo `A/xpho-project.git` , kể cả quyền tạo branch `B` cũng không có, việc `B` cần làm là fork `xpho-project` ra một phiên bản của mình, tạo branch rồi thực hiện các thay đổi lên branch này. 

Đầu tiên, `B` cần fork dự án `xpho-project` bằng cách vào đường dẫn `https://github.com/A/xpho-project.git/fork` (tức là thêm `/folk` ở cuối URL repo) , sau khi đã fork một phiên bản của bản thân, `B` lúc này mới clone phiên bản này về

```cmd
D:\> gh repo clone B/xpho-project
Cloning into 'xpho-project'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done.
```

Bây giờ, `B` cần tạo một branch riêng của mình để thực hiện các thay đổi. `B` được `A` đưa cho một nhiệm vụ, là thử tính năng tạo pull request, vậy nên `B` tạo thêm một file `test.txt` trong thư mục `xpho-project` và commit thay đổi này.

Trước tiên, `B` tạo branch có tên `test`

```cmd
D:\xpho-project>git checkout -b test
Switched to a new branch 'test'
```

Sau đó, `B` bổ sung một file `test.txt` vào thư mục
```cmd
// Máy tính cá nhân của B: Ver 2
xpho-project
	.git
	README.md
	xpho.tex
	test.txt
```

Sau đó, `B` thực hiện stage các thay đổi và commit
```
D:\xpho-project>git add .
D:\xpho-project>git commit -m "commit to test"
[test 06a1038] commit to test
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test.txt
```
Bây giờ, thư mục git của `B` là bản chụp Ver 3
```cmd
// Máy tính cá nhân của B: Ver 3
xpho-project
	.git
	README.md
	xpho.tex
	test.txt
```

Nhưng nó tồn tại ở nhánh branch test, chứ không phải ở nhánh chính do `A` quản lý.  `B` lúc này push thay đổi lên remote repository mà đã được tạo do fork repo ban đầu

```
D:\xpho-project>git push origin test
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 308 bytes | 308.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote:
remote: Create a pull request for 'test' on GitHub by visiting:
remote:      https://github.com/QHung247/xpho-project/pull/new/test
remote:
To https://github.com/QHung247/xpho-project.git
 * [new branch]      test -> test
```

Sơ đồ Git có dạng bây giờ là

![git3](https://i.imgur.com/D4lxind.png)

Người dùng `B` có thể thấy trên GitHub phiên bản của project `xpho-project` được fork có một nhánh mới là `test`.
![test](https://i.imgur.com/eow15ik.png)

Đồng thời xuất hiện một thông báo rằng nhánh `test` đã được push lên, người dùng `B` bấy giờ chọn tạo một pull request, click vào `Compare & pull request`, người dùng `B` thực hiện các bước điền thông tin và giải thích các thay đổi của mình thực hiện và gửi đi pull request
![pullreq](https://i.imgur.com/bOCcjwv.png)

Việc của người dùng `B` đã xong, giờ pull request sẽ được xem bởi chủ repo là `A`, review và thông qua thay đổi, merge vào nhánh chính

# Đánh giá pull request
Người dùng `A` bật máy tính và kiểm tra Inbox, phát hiện có một pull request được gửi đến từ `B`. Người dùng `A` đánh giá nội dung của pull request
![review](https://i.imgur.com/uVtRsKZ.png)

Nhận thấy yêu cầu pull request thoả mãn, người dùng `A` chọn Merge pull request và Confirm merge. Pull request chuyển trạng thái

![merged](https://i.imgur.com/JWpMVxh.png)

Thay đổi do `B` đóng góp chính thức được thông qua và đưa vào nhánh chính của project `xpho-project`

![git4](https://i.imgur.com/D4802Ud.png)

![done](https://i.imgur.com/GCr6XR3.png)

# Cập nhật thay đổi mới

Nếu project được phân công cẩn thận, các thay đổi của người dùng này sẽ không ảnh hưởng đến người dùng kia. `B` đưa lên một file `test.txt` vốn không ảnh hưởng gì đến người dùng `C` đã được `A` phân công sửa file `xpho.tex`, vì thế `C` không cần quan tâm `B` đã làm gì mà tiếp tục làm việc, commit và push, rồi tạo pull request.

Tuy nhiên, khi `C` cần cập nhật thay đổi của `B`, giả sử như `C` cần đọc file `test.txt`, `C` thực hiện lệnh
```cmd
git pull 
```
Các thay đổi `B` thực hiện và đã merge vào nhánh chính sẽ được cập nhật về thư mục git trên máy tính cá nhân của `C`

`C` tiếp tục làm việc bình thường, khi hoàn thành công việc, lại push lên branch riêng của mình rồi mở pull request.

