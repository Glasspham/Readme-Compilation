# Hướng dẫn cài Windows 11 và Office 365

## Mục lục

- [Chuẩn bị usb cứu hộ](./Setup-Window-Office.md#chuẩn-bị-usb-cứu-hộ)

- [Cài Windows 11](./Setup-Window-Office.md#cài-windows-11)

- [Cài Office 365](./Setup-Window-Office.md#cài-đặt-và-active-office-365)

- [Một số vấn đề gặp phải](./Setup-Window-Office.md#một-số-vấn-đề)

## Chuẩn bị usb cứu hộ

Bạn có thể làm theo video hướng dẫn dưới đây [Link video](https://youtu.be/g2tDjh7v-Ok?si=PSa-RFeuJ0qHI6oA)

## Cài Windows 11

__Lưu ý:__ Nếu bạn chưa phân vùng ổ cứng hay ổ cứng mới mua thì hãy làm theo dưới đây trước [Step-by-step](./Setup-Window-Office.md#lan-dau-cai-win-tren-mot-o-cung-moi)

Trước tiên bạn phải chuẩn bị một [USB cứu hộ](./Setup-Window-Office.md#chuẩn-bị-usb-cứu-hộ) trước khi cài vì các hướng dẫn sau đây đều liên quan đến đó.

**B1:** Chia ổ đĩa _(ít nhất 2 ổ C và D nếu bạn không có chỗ chứa file `.iso` như trong usb cứu hộ hoặc trong usb khác)_

**B2:** Lên [Microsoft](https://www.microsoft.com/en-us/software-download/windows11) để tải file windows 11 `.iso` _(lưu ý để vào ổ D nếu không có như trên ghi)_

**B3:** Làm ra file `.xml` _(nếu muốn windows được cài nhẹ, còn không khỏi tạo cũng được)_

- Cách 1: lên web này tạo [Link](https://schneegans.de/windows/unattend-generator/).

- Cách 2: tải file `.xml` có sẵn trên github [Link](https://github.com/memstechtips/UnattendedWinstall/blob/main/autounattend.xml#L10).

**B4:** Cắm usb cứu hộ sao đó restart máy, trong lúc đang restart bấm các nút hàng từ `F1 - F12` _(tùy thuộc vào hãng laptop)_, để chọn môi trường trong usb cứu hộ.

**B5:** Coi theo video cài windows của "Neyako Phạm" [Link](https://vt.tiktok.com/ZS9JhErjobKJd-0MDv3/) hoặc đọc file hướng dẫn [File](./File/Hướng%20dẫn%20cài%20đặt%20Windows%20với%20WinNTSetup%20chuẩn%20UEFI.pdf).

> Lưu ý: 

1. Khi trong app `WinNTSetup` khi bạn chọn `file` và `đường dẫn ổ đĩa` đúng theo `video` hoặc file `.pdf đính kèm`, vẫn còn thiếu 1 bước để thêm file `.xml`. Hãy nhìn vào trường `Unattend` và nhấn chọn để thêm file `.xml` của bạn vào!

2. Lúc khi window khởi động và cài đặt thông tin cho hệ thống thì bạn có thể vượt không yêu cầu `password` và đăng nhập `microsoft`. Lúc chọn khu vực nhấn `Shift + F10` hiện ra cửa sổ `cmd`.

    ```cmd
    oobe\bypassnro
    ```

3. Trường `Add drivers` trong file `.pdf` ghi là thiếu sẽ nguy hiểm nhưng thực tế không có vẫn không sao hết!

**B6:** Cài lại các phần mềm, sau khi cài lại windows.

Mở powershell với quyền admin

```bash
irm christitus.com/win | iex
```

_Lưu ý:_ Do 1 số phần mềm cần cài nằm trên Microsoft Store, mà gần đây nó hay bị lỗi.

> Sửa lỗi Microsoft Store khi bị lỗi Code: 0x80244022

Mở PowerShell với quyền Admin

```bash
Get-AppxPackage -AllUsers *WindowsStore* | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

**B7:** Đi kiếm chỗ cài đặt driver bị thiếu (VD: với máy Lenovo thì cài Lenovo Vantage, vô phần system update).

**B8:** Cài phần mềm Winhance, để tắt/bật windows update.

**B9:** Active `Windows` và `Microsoft Office`

Mở `PowerShell` với quyền Admin

```bash
irm https://get.activated.win | iex
```

## Cài đặt và Active Office 365

### Cài đặt

**B1:** Tải và Office Deployment Tool [Link](https://www.microsoft.com/en-us/download/details.aspx?id=49117) được file `officedeploymenttool_[id].exe`.

**B2:** Giải nén file `officedeploymenttool_[id].exe` ra folder tên bất kì ví dụ: `Office 365`. Trong folder này sẽ có file `setup.exe` và `configuration-Office365-[x64].xml`.

**B3:** Xóa file `configuration-Office365-[x64].xml` và vào [Link](https://config.office.com/deploymentsettings) để tạo file .xml riêng. 

> Lưu ý: Bạn đặt file .xml tên gì thì ở dưới phải sửa lại! Hoặc để mặc định như hệ thống gợi ý càng tốt (mặc định là `Configuration.xml`)! Và nhớ down vào thư mục `Office 365` để có thể cài đặt.

**B4:** Mở command prompt với quyền admin đúng thư mục `Office 365`.

Bạn có thể mở bằng cách gõ `cmd` trong Windows Search chọn chạy dưới quyền admin. Sau đó cd vào thư mục `Office 365`.

```bash
cd "path\to\Office 365"
```

Cách tìm đường dẫn đúng là mở `explorer` rồi sao chép đường dẫn của thư mục `Office 365`.

**B5:** Cài đặt Office 365

```bash
setup /configure Configuration.xml
```

[Video hướng dẫn](https://youtu.be/KqKAm97Baeo?si=ig1xETd2GR1MipYM)

### Active Office 365

**B1:** Mở PowerShell với quyền Admin

```bash
irm https://get.activated.win | iex
```

**B2:** Nhấn phím 2 chọn active Office

**B3:** Hoàn thành khi hiện `Office 365 is permanently activated.`

_Gợi ý:_

- HWID (Digital License): Activate vĩnh viễn Windows.
- Ohook: Activate vĩnh viễn Office.
- TSforge: Activate vĩnh viễn Windows, ESU, và Office.
- Online KMS: Activate Windows/Office 180 days (Trọn đời với nhiệm vụ gia hạn).

**B4:** Nhấn phím bất kì thoát ra. Sau đó nhấn phím 5 để kiểm tra active.

Nếu không hiện thời gian còn lại là crack thành công vĩnh viễn.

**Tham khảo thêm tại đây** [Link](https://massgrave.dev/)

## Một số vấn đề

### Lần đầu cài Win trên một ổ cứng mới

Ban đầu ổ cứng mới chưa có phân vùng nên ta cần chia phân vùng ổ đĩa trước. Bạn cần chuẩn bị một box chứa hoặc cấm trực tiếp vào máy để làm!

**B1:** Mở command prompt với quyền admin

**B2:** Gõ lệnh sau:

```bash
diskpart
```

**B3:** Gõ lệnh sau:

```bash
list disk
```

Hiện ra các phân vùng ổ đĩa của bạn, hãy chọn đúng ổ đĩa cần chia (thường là ổ đĩa 1 là ổ cứng mới gắn thêm)

**B4:** Gõ lệnh sau:

```bash
select disk 1
```

**B5:** Gõ lệnh sau:

> Bạn có thể thay đổi dung lượng theo ý thích (300 là 300MB). Và chỉnh label theo ý thích.

```bash
clean
convert gpt
create partition efi size=300
format quick fs=fat32 label="System"
assign letter="S"
create partition msr size=16
create partition primary
format quick fs=ntfs label="Windows"
assign letter="W"
shrink minimum=1024
create partition primary
format quick fs=ntfs label="Recovery"
assign letter="R"
set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
gpt attributes=0x8000000000000001
```
**B6:** Gõ lệnh sau:

Kiểm tra lại phân vùng vừa tạo

```bash
list partition
```
**B7:** Gõ lệnh sau:

```bash
exit
```

### Ẩn các phân vùng vừa tạo khỏi hiện thị ở `This PC`

#### Cách 1:

**B1:** Mở Command Prompt với quyền admin.

**B2:** Gõ lệnh sau:

```bash
diskpart
```

**B3:** Gõ lệnh sau:

```bash
list volume
```

**B4:** Gõ lệnh sau:

```bash
select volume X (thay X bằng số volume bạn muốn ẩn).
```

**B5:** Gõ lệnh sau:

```bash
remove letter=E (thay E bằng ký tự ổ đĩa bạn muốn ẩn). 
```

**B6:** Gõ lệnh sau:

```bash
exit
```

#### Cách 2 (Recommended):

**B1:** Mở Command Prompt với quyền admin.

**B2:** Gõ lệnh sau:

```bash
mountvol I: /d (thay I bằng ký tự ổ đĩa bạn muốn ẩn)
```

### Xóa phân vùng `Healthy (Recovery Partition)`

**B1:** Mở Command Prompt với quyền admin.

**B2:** Gõ lệnh sau:

```bash
diskpart
```

**B3:** Gõ lệnh sau:

```bash
list disk
```

**B4:** Gõ lệnh sau:

```bash
select disk X (thay X bằng số ổ đĩa bạn muốn xóa).
```

**B5:** Gõ lệnh sau:

```bash
list partition
```

**B6:** Gõ lệnh sau:

```bash
select partition X (thay X bằng số volume bạn muốn xóa).
```

**B7:** Gõ lệnh sau:

```bash
delete partition override
```

**B8:** Gõ lệnh sau:

```bash
exit
```