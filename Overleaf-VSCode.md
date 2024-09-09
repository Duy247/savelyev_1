# Hướng dẫn kết nối Overleaf với VSCode

## *Mục tiêu bài hướng dẫn:*
- Chuyển phương pháp soạn thảo $\text{LaTeX}$ sang Visual Studio Code, từ bỏ giao diện Overleaf cùi bắp.
- Củng cố kiến thức vận hành $\text{LaTeX}$ trong VSCode trước khi (nếu có thể) rời toàn bộ dự án sang VSCode và duy trì trên Github.
- Cung cấp một số kiến thức về thao tác và chức năng của VSCode.

## Hướng dẫn VSCode
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

### Giao diện

Bản chất Visual Studio Code là một trình soạn thảo mã. Giống như nhiều trình soạn thảo mã khác, VS Code áp dụng một giao diện người dùng và bố cục phổ biến với một trình duyệt ở bên trái, hiển thị tất cả các tệp và thư mục mà người dùng có quyền truy cập, và một trình soạn thảo ở bên phải, hiển thị nội dung của các tệp người dùng đã mở.

![UI](https://code.visualstudio.com/assets/docs/getstarted/userinterface/hero.png)

Hướng dẫn cụ thể về các chức năng, các bạn có thể tới đường dẫn [này](https://code.visualstudio.com/docs).

### Cài đặt Extension

#### Duyệt các tiện ích mở rộng 
Bạn có thể duyệt và cài đặt các tiện ích mở rộng từ trong VS Code. Mở chế độ xem Tiện ích mở rộng bằng cách nhấp vào biểu tượng Tiện ích mở rộng trong Thanh Hoạt động ở bên cạnh của VS Code hoặc lệnh View: Extensions.

![ExtensionsMarketplace](https://code.visualstudio.com/assets/docs/editor/extension-marketplace/extensions-popular.png)

#### Cài đặt một tiện ích mở rộng 

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

## Kết nối Overleaf với VSCode

Đầu tiên, sau khi đã cài đặt VSCode, để có thể làm việc với các file $\text{LaTeX}$ hoặc $\text{TeX}$, người dùng cần cài đặt một bộ công cụ để máy tính có thể sử dụng.

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

### Kết nối Overleaf và VSCode

#### Đăng nhập Overleaf trên trình duyệt 

Có thể sử dụng các trình duyệt Microsoft Edge, Google Chrome,Mozilla Firefox, Safari,etc... Sau đó tham gia vào các project cần tham gia, nếu cần tự thao tác chỉnh sửa, tải xuống mã nguồn của các project và upload lại lên Overleaf.

Tải mã nguồn bằng cách chọn Menu bên trái giao diện

![download](https://i.imgur.com/B1xMaIK.png)

Upload lại ở trang chủ 

![upload](https://i.imgur.com/0pTgBe0.png)

Quay trở lại trang chủ của Overleaf, ấn F12 hoặc chuột phải Inspect

Sau khi bật trình debug console, giao diện như sau:

![uidebug](https://i.imgur.com/j4ueNQq.png)

Chúng ta quan tâm tới phần Network, tại đây chúng ta sẽ lấy cookie để đăng nhập vào Overleaf trên VSCode, refresh lại trang để làm mới mục Network

![network](https://i.imgur.com/wTk4Ugu.png)

Tại mục Network, kéo lên đầu và chọn giao tiếp "project", ở tab bên phải kéo xuống và tìm Cookie

![cookie](https://i.imgur.com/mKMivum.png)

Copy cookie này, `Ctrl+C`

#### Đăng nhập Overleaf trên VSCode

Quay trở lại VSCode, tại cột trái màn hình, ấn vào biểu tượng Overleaf

![overleafvscode](https://i.imgur.com/QMLjETc.png)

Ấn vào biểu tượng login bên phải

![login](https://i.imgur.com/yggnrs5.png)

Chú ý thanh tìm kiếm trên cùng giao diện, nay xuất hiện mục Login with Cookies

![loginw](https://i.imgur.com/i6hkcHu.png)

Paste đoạn mã Cookie vừa copy từ bên Network của Overleaf,`Ctrl+V`

![cookiepaste](https://i.imgur.com/maBzk7d.png)

Enter, sau khi đã đăng nhập, bên trái phần overleaf, chúng ta có thể thấy toàn bộ các project mình đang tham gia

![project](https://i.imgur.com/K04wAtN.png)

Ấn chọn mũi tên bên phải để mở Project mình muốn

![openpro](https://i.imgur.com/ziKtkzI.png)

Tới đây, các bạn có thể bắt đầu Edit các file $\text{LaTeX}$, thay đổi được lưu sẽ đẩy lên Overleaf. Giao diện như sau

![editor](https://i.imgur.com/8F2BDDE.png)

Để thực hiện Compile file LaTeX thành PDF, gõ tổ hợp phím `Ctrl+Alt+B`, biểu tượng pdfLatex dưới giao diện sẽ xoay, 

![compile](https://i.imgur.com/z6JK9sP.png)

Sau khi xoay xong gõ tổ hợp `Ctrl+Alt+V` để xem file PDF

![view](https://i.imgur.com/QOUsPFf.png)


## Kết

Tới đây, các bạn đã có thể bắt đầu xem và chỉnh sửa các file LaTeX ngay trên VSCode, các thay đổi nếu được lưu cũng sẽ được lưu trực tiếp trên Overleaf. 

Các cảnh báo xuất hiện ở phần debug, nếu không phải đỏ, đa phần có thể được bỏ qua, miễn là file PDF vẫn compile thành công

![warn](https://i.imgur.com/FFdRDmE.png)

### Đánh giá:
- Tốc độ làm việc trên VSCode nhanh hơn trên Overleaf
- Vẫn cần kết nối Internet nếu muốn đồng bộ lên Overleaf
- Đây sẽ là bước đệm để chuyển rời từ Overleaf sang LaTeX không phụ thuộc trên Github
- Nếu compile file LaTeX sử dụng LaTeX Workshop sẽ không thành công, do thiếu đi các module và package của Overleaf, chỉ có thể compile thành PDF dựa vào Overleaf extension.

## Chúc các bạn thành công



