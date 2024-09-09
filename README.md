# savelyev_1
## Hướng dẫn vận hành

### *Mục tiêu bài hướng dẫn:*
- Chuyển phương pháp soạn thảo $\text{LaTeX}$ hoàn toàn sang Visual Studio Code, độc lập khỏi Overleaf.
- Cung cấp một số kiến thức về thao tác và chức năng của VSCode.
- Cài đặt trình compile để vận hành với file có nguồn gốc từ Overleaf

### Hướng dẫn VSCode
Đối với một số bạn học sinh / sinh viên mới, VSCode có thể là một công cụ vẫn còn mới. Vì thế, các bạn cần làm quen với công cụ này trước khi có thể hiểu và thực hiện nội dung của bài hướng dẫn.


- Đầu tiên,để cài đặt VS Code.
    - Tải xuống từ [https://code.visualstudio.com/download](https://code.visualstudio.com/download)
    - Sau khi đã tải xuống, chạy file cài đặt (VSCodeUserSetup-{version}.exe). Thời gian cài đặt sẽ từ vài phút cho đến vài tiếng (máy tính thời Tống).
    - Mặc định, VS Code được cài đặt theo đường dẫn `C:\Users\{Username}\AppData\Local\Programs\Microsoft VS Code`.

Một số phím tắt: 
- Để mở một thư mục
    - **File** > **Open Folder** (Ctrl+K Ctrl+O)
- Khởi động trình duyệt File
    - **View** > **Explorer** (Ctrl+Shift+E)
- Tìm kiếm
    - **View** > **Search** (Ctrl+Shift+F)
- Source Control
    - **View** > **Source Control (SCM)** (Ctrl+Shift+G)
- Xem Extensions 
    - **View** > **Extensions** (Ctrl+Shift+X)
- Khởi động Command Palette.
    - **View** > **Command Palette...** (Ctrl+Shift+P)
- Bảng Output
    - **View** > **Output** (Ctrl+Shift+U)
- Bảng sửa lỗi (Problems)
    - **View** > **Problems** (Ctrl+Shift+M)
- Terminal tích hợp
    - **View** > **Terminal** (Ctrl+`)
- Tạo file mới
    - **File** > **New File** (Ctrl+N)
- Lưu file
    - **File** > **Save** (Ctrl+S)
- Bật tự động lưu
    - **File** > **Auto Save**
- Extensions mở rộng cho ngôn ngữ lập trình
    - [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) - IntelliSense, linting, debugging, code formatting, refactoring, and more.
    - [Live Preview](https://marketplace.visualstudio.com/items?itemName=ms-vscode.live-server) - Hosts a local server to preview your webpages.
- Zoom
    - Zoom ra (Ctrl+-)
    - Zoom vào (Ctrl+=)
- Tuỳ biến trình code bằng giao diện ưa thích
    - **File** > **Preferences** > **Theme** > **Color Theme** (Ctrl+K Ctrl+T)

#### Giao diện

Bản chất Visual Studio Code là một trình soạn thảo mã. Giống như nhiều trình soạn thảo mã khác, VS Code áp dụng một giao diện người dùng và bố cục phổ biến với một trình duyệt ở bên trái, hiển thị tất cả các tệp và thư mục mà người dùng có quyền truy cập, và một trình soạn thảo ở bên phải, hiển thị nội dung của các tệp người dùng đã mở.

![UI](https://code.visualstudio.com/assets/docs/getstarted/userinterface/hero.png)

Hướng dẫn cụ thể về các chức năng, các bạn có thể tới đường dẫn [này](https://code.visualstudio.com/docs).

#### Cài đặt Extension

##### Duyệt các tiện ích mở rộng 
Bạn có thể duyệt và cài đặt các tiện ích mở rộng từ trong VS Code. Mở chế độ xem Tiện ích mở rộng bằng cách nhấp vào biểu tượng Tiện ích mở rộng trong Thanh Hoạt động ở bên cạnh của VS Code hoặc lệnh View: Extensions.

![ExtensionsMarketplace](https://code.visualstudio.com/assets/docs/editor/extension-marketplace/extensions-popular.png)

##### Cài đặt một tiện ích mở rộng 

Để cài đặt một tiện ích mở rộng, chọn nút Cài đặt. Khi quá trình cài đặt hoàn tất, nút Cài đặt sẽ chuyển thành nút Quản lý hình bánh răng.

![choose](https://code.visualstudio.com/assets/docs/editor/extension-marketplace/search-for-todo-extension.png)

Click chọn Extension sau đó ấn Install để cài đặt

![install](https://code.visualstudio.com/assets/docs/editor/extension-marketplace/todo-highlight-details.png)

Sau khi cài đặt xong, Extension sẽ có hình bánh răng

![finish](https://code.visualstudio.com/assets/docs/editor/extension-marketplace/manage-button.png)

Sau đó, các lệnh liên quan của Extension sẽ có thể được truy cập bằng cách sử udjng Command Palette (`Ctrl+Shift+P`) 

![Command](https://code.visualstudio.com/assets/docs/editor/extension-marketplace/todo-highlight-commands.png)

Nếu cần phải gỡ cài đặt một Extension, hoặc không cần sử dụng, click vào biểu tượng hình bánh răng và chọn Uninstall

![uninstall](https://code.visualstudio.com/assets/docs/editor/extension-marketplace/todo-highlight-uninstall.png)

### Cài đặt MiKTex (Modern TEX Distribustion)

Bạn tới đường dẫn [MiKTex](https://miktex.org/download) và cài đặt MiKTex.

- Chọn "I accept the MiKTeX copying conditions"
- Tuỳ ý chọn giữa 2 lựa chọn cài đặt, cho người dùng OS hiện tại hoặc cho toàn bộ người dùng
- Chọn đường dẫn cài đặt MiKTeX, mặc định `C:\Program Files\MiKTeX`. Người dùng nên cân nhắc do tổng dung lượng sau khi cài đặt các package là gần 1 GB
- Tiến hành cài đặt

Ấn nút Windows và tìm MiKTeX Console, khởi chạy ứng dụng, tới mục Updates và cài đặt tất cả các package yêu cầu phải có.

Kết thúc, thoát khỏi MiKTeX Console.

### Cài đặt Extension

Vào VSCode, mục Extension, xem hướng dẫn cài đặt [bên trên](#cài-đặt-extension).

Lần lượt cài đặt các Extension sau:
- LaTeX 

![alt text](https://i.imgur.com/qWUnWBe.png)

- LaTeX Workshop (phục vụ debugging)

![alt text](https://i.imgur.com/tBvWSb9.png)

- Overleaf Workshop

![alt text](https://i.imgur.com/pKRgfCW.png)

Sau khi cài đặt, LaTeX Workshop sẽ có dấu chấm than, không cần quan tâm.

### Thiết lập VSCode để compile file từ Overleaf
Bản chất việc compile thành công hay không nằm ở việc công thức (recipe) compile cần ăn khớp với Overleaf. Với 2 quyển sách Savelyev, Overleaf của nhóm dịch đang sử dụng recipe pdfLatex. Tuy nhiên, Latex Workshop không có recipe này mà chúng ta cần cài đặt thêm

- Sau khi đã cài đặt LaTeX Workshop, dí chuột vào biểu tượng bánh răng và ấn Extension Settings

![ExtenSet](https://i.imgur.com/qHbMVYu.png)

- Gõ vào thanh tìm kiếm cài đặt `@ext:James-Yu.latex-workshop recipe` và Enter (tức là gõ thêm từ `recipe` và Enter)

![recipe](https://i.imgur.com/QImQS3y.png)

- Quan tâm đến cài đặt thứ nhất, cài đặt này sẽ để là `lastUsed` cho đỡ khó chịu khi sử dụng

![lastUsed](https://i.imgur.com/noFWbuk.png)

- Tiếp theo, để bổ sung recipe pdfLatex vào LaTeX Workshop, hướng tới cài đặt bên dưới

![1option](https://i.imgur.com/noFWbuk.png)

- Sau đó, click vào `Edit in settings.json`, kéo xuống dưới cùng, bạn sẽ thấy đoạn code

```json
//bên trên có gì đấy
        {
            "name": "tectonic",
            "command": "tectonic",
            "args": [
                "--synctex",
                "--keep-logs",
                "%DOC%.tex"
            ],
            "env": {}
        }
    ]
}
```

Sửa nó thành

```json
//bên trên có gì đấy
        {
            "name": "tectonic",
            "command": "tectonic",
            "args": [
                "--synctex",
                "--keep-logs",
                "%DOC%.tex"
            ],
            "env": {}
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "--shell-escape", // if you want to have the shell-escape flag
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%.tex"
            ]
        }
    ]
}
```

**Lưu ý dấu phẩy ở `},`**, sau đó lưu bằng tổ hợp `Ctrl+S`

- Sau đó, quay ra ngoài và tiếp tục hướng tới cài đặt tiếp theo 

![2option](https://i.imgur.com/3lQNHkC.png)

Cũng click vào `Edit in settings.json`, kéo xuống dưới cùng, bạn sẽ thấy đoạn code

```json
//bên trên có gì đấy
        {
            "name": "tectonic",
            "command": "tectonic",
            "args": [
                "--synctex",
                "--keep-logs",
                "%DOC%.tex"
            ],
            "env": {}
        }
    ]
}
```

Sửa thành 

```json
//bên trên có gì đấy
        {
            "name": "tectonic",
            "command": "tectonic",
            "args": [
                "--synctex",
                "--keep-logs",
                "%DOC%.tex"
            ],
            "env": {}
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "--shell-escape", // if you want to have the shell-escape flag
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%.tex"
            ]
        }
    ]
}
```
**Lưu ý dấu phẩy ở `},`**, sau đó lưu bằng tổ hợp `Ctrl+S`.

Tới đây đã hoàn thành setup VSCode

## Làm việc với repository

### Clone repository

Để bắt đầu làm việc với repo, người dùng cần tải một phiên bản của nó về máy bằng clone. Clone về cơ bản là một hành động để tạo một bản copy của repository trên máy tính cá nhân của người dùng. 

Hiện nay người dùng có thể clone repository bằng Git CLI hoặc Github CLI, tuy người dùng có thể "clone" bằng cách tải repository về thông qua trình duyệt, nhưng dùng phương pháp này không đảm bảo người dùng có thể đóng góp cho dự án về sau do dù sao nếu thiếu các CLI thì cũng không thể làm việc với repo git được.

Bắt đầu với việc đi đến đường dẫn mà người dùng muốn lưu repository tại đó và khởi chạy Command Prompt hoặc khởi chạy Command Prompt rồi `cd` tới đường dẫn.

Clone repository chỉ cần sử dụng 1 dòng lệnh cơ bản

Với Git CLI, lệnh clone repository là 
```cmd
git clone https://github.com/Duy247/savelyev_1
```
Với Github CLI, lệnh clone có khác biệt
```cmd
gh repo clone Duy247/savelyev_1
```
Sau khi repository đã được clone hoàn chỉnh, sử dụng một trình IDE, có thể là Visual Studio Code và mở cả tệp của repository.

### Tạo branch cá nhân

Đầu tiên, để việc người dùng thực hiện thay đổi lên phiên bản clone repository có ý nghĩa, người dùng cần tạo một branch riêng cho bản thân để thực hiện các thay đổi.

```cmd
git checkout -b <branch_name> 
```

Ví dụ, thành viên Log muốn dịch phần Appendix của cuốn sách, Log sẽ làm
```cmd
git checkout -b <log_appendix> 
```

Khi thực hiện các thay đổi trên repository đã clone về, người dùng không thực hiện thay đổi trực tiếp lên repository mà chỉ đang thay đổi các tệp tin được lưu trên máy tính, nói cách khác là lên branch của bản thân. Tại thời điểm này, nếu thực hiện đóng góp nội dung hay sửa đổi, branch của người dùng sẽ cần được *commit*, *push* và *merge* vào repository gốc.

### Source control

Nếu người dùng sử dụng các trình IDE có tính năng **Source Control** thì có thể dễ dàng theo dõi và quản lý các thay đổi này, ví dụ như với Visual Studio Code 

![VSC](https://i.imgur.com/VzmhZ9B.png)

Đối với Git và Github CLI, người dùng phải thêm các thay đổi một cách thủ công, sau đó mới có thể theo dõi thay đổi mình đã thực hiện (so sánh với branch gốc `master` trên repository)

Ví dụ, bổ sung một tệp tin `test.txt` vào thư mục chính của repository, người dùng cần thực hiện việc đẩy thay đổi vào **staging area**
```cmd
git add test.txt
```
Sau đó, để có thể xem thay đổi mà mình đã thực hiện
```cmd
git diff master
```

Kết quả của ví dụ trên sẽ nhìn thế này, trên một repository có tên physx-cnh
```
D:\physx-cnh>git diff master
diff --git a/test.txt b/test.txt
new file mode 100644
index 0000000..e69de29
```

Nếu người dùng muốn huỷ bỏ thay đổi, tức là đưa tệp tin `test.txt` ra khỏi staging area
```cmd
git reset HEAD test.txt
```

Nếu sử dụng IDE có Source Control, các bước trên sẽ hoàn toàn được làm tự động.

Sau khi đã thực hiện các thay đổi, để thực hiện việc commit dễ dàng nhất, khuyến cáo người dùng nên sử dụng lệnh stage

```cmd
git add -p
```

Lệnh stage này sẽ chỉ đưa các thay đổi mà người dùng thực hiện vào staging area thay vì đưa vào toàn bộ repository.

Sau đó người dùng sẽ được review các thay đổi mình đã thực hiện, `y` để đồng ý stage thay đổi 

Ví dụ với thay đổi lên tệp `lessons.txt`
```
D:\physx-cnh>git add -p
diff --git a/physics/lessons.txt b/physics/lessons.txt
index 52c0184..6c9adb6 100644
--- a/physics/lessons.txt
+++ b/physics/lessons.txt
@@ -8,4 +8,5 @@ Luyện tập<br>23/08/24| |/lessons/train_230824.pdf|
 Luyện tập<br>29/08/24| |/lessons/train_290824.pdf|
 Luyện tập<br>30/08/24| |/lessons/train_300824.pdf|
 Giải bài hạt mưa| |/lessons/exercise_raindrop.pdf|
-Giải bài căng dây - vòng 2 TP| |/lessons/exercise_tensionstring.pdf|
\ No newline at end of file
+Giải bài căng dây - vòng 2 TP| |/lessons/exercise_tensionstring.pdf|
+ádasdasd
\ No newline at end of file
(1/1) Stage this hunk [y,n,q,a,d,e,p,?]?
```

Sau khi đã xem lại toàn bộ thay đổi và stage những thay đổi, người dùng sẽ commit thay đổi này lên branch riêng của bản thân
```cmd
git commit -m "Change"
```

Và push thay đổi này lên hệ thống của Github
```cmd
git push
```
### Tạo pull request 

Cuối cùng ,các bạn quay lại nền tảng Github, tới branch của bạn vừa push và tạo pull request, chọn branch của bạn là nguồn (source) và branch master của tôi là target. Thực hiện yêu cầu pull request rồi Submit. 

Ví dụ dưới là giao diện của một pull request

![Example](https://docs.github.com/assets/cb-87213/mw-1440/images/help/pull_requests/pull-request-review-edit-branch.webp)

Người dùng khi đóng góp nội dung cần nêu rõ mình thay đổi những gì. Sau khi thực hiện Submit pull request, cá nhân chủ repo sẽ review thay đổi mà người dùng đã thực hiện, nếu đạt yêu cầu, branch của người dùng sẽ được merge vào branch chính.

### Chỉnh sửa file TeX và Compile

Trước khi có thể push và merge vào repo chính của nhóm dịch, trước tiên bạn sẽ cần thực hiện các thay đổi, ví dụ như dịch một đoạn ngắn, thay đổi file ảnh,v.v...

Trong số đó, việc chỉnh sửa file TeX tải từ Overleaf về sẽ được thực hiện với sự hỗ trợ của bước phía [trên](#cài-đặt-extension) trở xuống

- Mở file thư mục chứa toàn bộ file TeX, ở đây, tôi ví dụ cuốn sách số 1 chứa các file TeX từng chương và file TeX chính chứa các code cơ bản để thiết lập file đầu ra. 

![mainscreen](https://i.imgur.com/trZDS6k.png)

Nhìn về phía trái màn hình, click vào biểu tượng $\text{TeX}$ , mở rộng phần `Build LaTeX project`, kéo xuống chọn recipe pdflatex mà chúng ta thêm ở [trên](#cài-đặt-extension).

![pdflatex](https://i.imgur.com/XYihFpa.png)

Click vào dấu chạy màu xanh, sau đó tag pdflatex sẽ có hiệu ứng xoay tròn

![spin](https://i.imgur.com/ZzO7yNB.png)

Sau khi hoàn thành

![done](https://i.imgur.com/Kp8ls1i.png)

Đến đây chúng ta sẽ tìm thấy một file pdf ở trong thư mục chứa các file TeX, đây chính là file PDF được compile

![pdf](https://i.imgur.com/CAkqDcu.png)

Sẽ có những phần báo lỗi ở dưới, tuy nhiên không cần quá quan tâm, miễn là compile ra được file PDF.


Mỗi khi thay đổi file, chỉ cần ấn tổ hợp phím `Ctrl+Alt+B` lại một lần nữa để Compile lại file PDF.


