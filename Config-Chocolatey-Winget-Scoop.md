# Config path install app on Windows for Chocolatey-Winget-Scoop
Dưới đây là hướng dẫn chi tiết cách cài đặt và chỉ đường dẫn (thiết lập vị trí cài đặt) cho các trình quản lý gói phổ biến trên Windows: Winget, Chocolatey, và Scoop.

## 1. Winget (Windows Package Manager)
Winget thường được tích hợp sẵn trong Windows 10/11 (App Installer).
- Cách cài đặt/Cập nhật:

    Mở Microsoft Store và tìm "App Installer" để cập nhật.

- Chỉ đường dẫn cài đặt ứng dụng (không phải winget):

    Winget mặc định cài vào các vị trí tiêu chuẩn. Để thay đổi vị trí cài đặt cho một phần mềm cụ thể, bạn có thể sử dụng tham số `--location`.
    ```powershell
    winget install --id <Package.ID> --location "D:\Apps"
    ```
- Hãy thận trọng khi sử dụng mã.Thiết lập mặc định: Bạn có thể chỉnh sửa file cài đặt của winget (`wingetsettings.json`) để thiết lập vị trí mặc định cho các ứng dụng hỗ trợ.

## 2. Chocolatey
Chocolatey cần quyền Administrator để cài đặt.
- Cách cài đặt:

    Mở PowerShell với quyền Administrator và chạy câu lệnh:

    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org'))
    ```

- Chỉ đường dẫn cài đặt (Thay đổi thư mục Choco):

    Mặc định, Choco cài vào `C:\ProgramData\chocolatey`. Để thay đổi thư mục chứa các gói đã cài, bạn cần thay đổi biến môi trường `ChocolateyInstall`.
    - Mở Environment Variables (Biến môi trường) trên Windows.
    - Tạo biến mới: `ChocolateyInstall` = `D:\Path\To\NewFolder`.
    - Chạy lại script cài đặt.

## 3. Scoop
Scoop cài đặt ứng dụng vào thư mục người dùng, không cần quyền admin, rất thuận tiện để chuyển hướng.
- Cách cài đặt:Mở PowerShell và chạy:

    ```powershell
    Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
    irm get.scoop.sh | iex
    ```

- Chỉ đường dẫn cài đặt (Thay đổi thư mục Scoop):

    Mặc định, Scoop cài vào `C:\Users\<User>\scoop`.

    - Tạo thư mục mới, ví dụ: `D:\Applications\Scoop`.
    - Thiết lập biến môi trường `SCOOP` trỏ đến thư mục này trước khi cài đặt:
    ```powershell
    $env:SCOOP='D:\Applications\Scoop'
    [Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')
    ```
- Sau đó chạy lệnh cài đặt Scoop.

## Bảng tóm tắt

| Công cụ | Mặc định | Cách chỉ đường dẫn |
| --- | --- | --- |
| Winget | `C:\Program Files...` | Dùng tham số `--location "Đường\Dẫn"` |
| Choco | `C:\ProgramData\chocolatey` | Đổi biến môi trường `ChocolateyInstall` |
| Scoop | `C:\Users\<User>\scoop` | Đổi biến môi trường `SCOOP` |

> **Lưu ý**: Sau khi thay đổi biến môi trường, hãy khởi động lại PowerShell hoặc Command Prompt.