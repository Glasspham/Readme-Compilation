# Custom Terminal

## Cài đặt các công cụ cần thiết

### 1. Cài đặt Terminal

Bạn hãy kiểm tra trong máy có `Terminal` chưa, nếu chưa thì tải tại [Microsoft Store](https://apps.microsoft.com/home?hl=vi-VN&gl=VN) và tìm kiếm [Terminal](https://apps.microsoft.com/detail/9N0DX20HK701?hl=vi-vn&gl=VN)

Sau khi tải xong, bạn hãy mở `Terminal` lên và gõ lệnh sau:
```bash
wt.exe --version
```
Nếu nó hiện ra phiên bản của `Terminal` thì bạn đã cài đặt thành công.

### 2. Cài đặt PowerShell 7

Bạn vào [Microsoft Store](https://apps.microsoft.com/home?hl=vi-VN&gl=VN) và tìm kiếm [PowerShell](https://apps.microsoft.com/detail/9mz1snwt0n5d?hl=vi-VN&gl=VN).

Hoặc mở `Terminal` lên và gõ lệnh sau:

```bash
winget install --id Microsoft.PowerShell --source winget
```
Nếu nó hiện ra phiên bản của `PowerShell` thì bạn đã cài đặt thành công.

## Cấu hình Terminal

### 1. Cấu hình Terminal

B1. Mở `settings` của `Terminal`

B2. Chọn `PowerShell` làm `default profile`

B3. Chọn `Windows Terminal` làm `default terminal application`

B4. Chọn `Default > Appearance` trong `Profiles`

B5. Cấu hình giao diện!

__Gợi ý__

Color scheme: có thể tham khảo [Dracula Theme](https://draculatheme.com/terminal) [Windows Terminal Themes](https://windowsterminalthemes.dev/) [Color schemes in Windows Terminal](https://learn.microsoft.com/en-us/windows/terminal/customize-settings/color-schemes)

Font: có thể tham khảo [Nerd Fonts](https://www.nerdfonts.com/)

### 2. Cấu hình profile PowerShell theo ChrisTitusTech

Thực thi lệnh sau trong cửa sổ PowerShell với quyền quản trị viên để cài đặt cấu hình PowerShell:

```bash
irm "https://github.com/ChrisTitusTech/powershell-profile/raw/main/setup.ps1" | iex
```

After running the script, you'll have two options for installing a font patched to support icons in PowerShell:

1. Install font `cove.zip`.
2. Install `oh-my-posh`.

[Tham khảo](https://github.com/ChrisTitusTech/powershell-profile)

### 3. Cá nhân hóa khi làm theo cấu hình ChrisTitusTech

Khi bạn cài xong thì toàn bộ `PowerShell` sẽ giống y chang của `ChrisTitusTech`. Để cá nhân hóa theo bản thân thì ta cần nhúng code vào! Hãy chạy đoạn code dưới đây trong `Terminal` để lấy đường dẫn chứa cấu hình:

```bash
$PROFILE.CurrentUserCurrentHost
```

Ví dụ: `C:\Users\Admin\Documents\PowerShell\Microsoft.PowerShell_profile.ps1`

B1. Hãy tạo ra 2 file `profile.ps1` và `CTTcustom.ps1` trong thư mục `C:\Users\Admin\Documents\PowerShell`

__Giải thích__

- `profile.ps1`: File này sẽ được chạy mỗi khi mở `PowerShell`
- `CTTcustom.ps1`: File này sẽ được load theo do trong file `Microsoft.PowerShell_profile.ps1` có lệnh gọi đến file này!

```powershell
if (Test-Path "$PSScriptRoot\CTTcustom.ps1") {
    Invoke-Expression -Command "& `"$PSScriptRoot\CTTcustom.ps1`""
}
```

B2. Vào thư file `CTTcustom.ps1` thêm đoạn code sau:

```powershell
oh-my-posh init pwsh --config https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/1_shell.omp.json | Invoke-Expression
```

`1_shell.omp.json` tên file chứa cấu hình giao diện, bạn có thể thay đổi nó theo ý muốn! Tham khảo thêm tại [Oh My Posh](https://ohmyposh.dev/docs/themes)

### 4. Cấu hình cá nhân hóa từ đầu đến cuối

Bạn có thể tham khảo và làm theo [video này](https://www.youtube.com/watch?v=xDZC5iYg_uU)!

### Giải thích 1 số vấn đề (ChrisTitusTech)

#### Tại sao không sửa theme trực tiếp trong file `Microsoft.PowerShell_profile.ps1`?

Vì trong file có đoạn code cập nhật mới file `Microsoft.PowerShell_profile.ps1` từ github về máy mỗi khi mở `PowerShell` được đóng góp bởi cộng đồng!

Đây là hàm thực hiện update

```powershell
# Check for Profile Updates
function Update-Profile {
    # If function "Update-Profile_Override" is defined in profile.ps1 file
    # then call it instead.
    if (Get-Command -Name "Update-Profile_Override" -ErrorAction SilentlyContinue) {
        Update-Profile_Override
    } else {
        try {
            $url = "$repo_root/powershell-profile/main/Microsoft.PowerShell_profile.ps1"
            $oldhash = Get-FileHash $PROFILE
            Invoke-RestMethod $url -OutFile "$env:temp/Microsoft.PowerShell_profile.ps1"
            $newhash = Get-FileHash "$env:temp/Microsoft.PowerShell_profile.ps1"
            if ($newhash.Hash -ne $oldhash.Hash) {
                Copy-Item -Path "$env:temp/Microsoft.PowerShell_profile.ps1" -Destination $PROFILE -Force
                Write-Host "Profile has been updated. Please restart your shell to reflect changes" -ForegroundColor Magenta
            } else {
                Write-Host "Profile is up to date." -ForegroundColor Green
            }
        } catch {
            Write-Error "Unable to check for `$profile updates: $_"
        } finally {
            Remove-Item "$env:temp/Microsoft.PowerShell_profile.ps1" -ErrorAction SilentlyContinue
        }
    }
}
```

Trong đoạn dưới đây luôn gọi tới hàm `Update-Profile` để cập nhật file `Microsoft.PowerShell_profile.ps1`

```powershell
# Check if not in debug mode AND (updateInterval is -1 OR file doesn't exist OR time difference is greater than the update interval)
if (-not $debug -and `
    ($updateInterval -eq -1 -or `
            -not (Test-Path $timeFilePath) -or `
            $null -eq $lastExec -or `
        ((Get-Date) - $lastExec).TotalDays -gt $updateInterval)) {

    Update-Profile
    $currentTime = Get-Date -Format 'yyyy-MM-dd'
    $currentTime | Out-File -FilePath $timeFilePath

} elseif ($debug) {
    Write-Warning "Skipping profile update check in debug mode"
}
```

Bạn có thể tắt update bằng cách thay đổi giá trị của biến `$updateInterval` thành `-1` hoặc comment đoạn code trên lại rồi chỉnh sửa theme!

#### Sự khác biệt giữa file `profile.ps1` và `CTTcustom.ps1`?

File `profile.ps1` sẽ được chạy mỗi khi mở `PowerShell`, dùng để code thêm các hàm, biến, alias, ... cá nhân của bạn.

File `CTTcustom.ps1` sẽ được load theo do trong file `Microsoft.PowerShell_profile.ps1` có lệnh gọi đến file này. Nên chỉ có thể lưu các cấu hình giao diện, theme, font, và api, ...

Nên khi thêm 1 thứ gì mới hãy thử bỏ vào 1 trong 2 file này để kiểm tra xem nó có hoạt động không nhé!


## Cấu hình Terminal của [harrytien107](https://github.com/harrytien107/powershell-profile)

Update: 2024-06-26
Do gần đây ở christitus bị cắt bớt chức năng nên mình đã tự tạo ra 1 bản cấu hình mới.
Giữ lại các chức năng ngày xưa của ChrisTitusTech và thêm 1 số chức năng mới.
Các chức năng mới:
- Thêm chức năng lựa chọn theme.
- Thêm Tool AVL.
- Bật/tắt chức năng update profile (mặc định là tắt).

Check tại: [powershell-profile-fork](https://github.com/harrytien107/powershell-profile)