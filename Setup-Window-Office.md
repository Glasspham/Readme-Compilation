# Hướng dẫn cài Windows 11 và Office 365

## Mục lục

- [Chuẩn bị usb cứu hộ](./Setup-Window-Office.md#chuẩn-bị-usb-cứu-hộ)

- [Cài Windows 11](./Setup-Window-Office.md#cài-windows-11)

- [Cài Office 365](./Setup-Window-Office.md#cài-đặt-và-active-office-365)

- [Một số vấn đề gặp phải](./Setup-Window-Office.md#một-số-vấn-đề)

## Chuẩn bị usb cứu hộ

Bạn có thể làm theo video hướng dẫn dưới đây [Link video](https://youtu.be/g2tDjh7v-Ok?si=PSa-RFeuJ0qHI6oA)

#### Các USB Boot mà tôi recommend:
- ⭐ Ventoy [hướng dẫn tạo usb boot](https://www.ventoy.net/en/index.html)
- NHV BOOT (có bản free và paid) [hướng dẫn tạo usb boot](https://anhdvboot.com/huong-dan/tao-usb-boot-phan-vung-an-uefi-legacy-voi-1-click-anhdv-boot/)
- Anhdv Boot (có bản free và paid) [hướng dẫn tạo usb boot](https://nhvboot.com/huong-dan-tao-usb-nhv-boot/)
- WinPE

## Cài Windows 11

__Lưu ý:__ Nếu bạn chưa phân vùng ổ cứng hay ổ cứng mới mua thì hãy làm theo dưới đây trước [Step-by-step](./Setup-Window-Office.md#lan-dau-cai-win-tren-mot-o-cung-moi)

Trước tiên bạn phải chuẩn bị một [USB cứu hộ](./Setup-Window-Office.md#chuẩn-bị-usb-cứu-hộ) trước khi cài vì các hướng dẫn sau đây đều liên quan đến đó.

**B1:** Chia ổ đĩa _(ít nhất 2 ổ C và D nếu bạn không có chỗ chứa file `.iso` như trong usb cứu hộ hoặc trong usb khác)_

**B2:** Lên [Microsoft](https://www.microsoft.com/en-us/software-download/windows11) để tải file windows 11 `.iso` _(lưu ý để vào ổ D nếu không có như trên ghi)_

Các chỗ tải iso (recommend):
- ⭐ [Massgrave](https://massgrave.dev/genuine-installation-media)
- ⭐ [OS click](https://os.click/) 
- ⭐ [PITVN](https://docs.google.com/spreadsheets/u/7/d/e/2PACX-1vRlK-vRwPJHDaANT81EjyG4m5ZnLXdKRYfS0eKXyCzGymEfUDmKHRhxvUbtWYTfVn7MJ3E2jk7v3cGi/pubhtml?usp=embed_facebook#gid=0)
- [Adguard](https://files.rg-adguard.net/version/f0bd8307-d897-ef77-dbd6-216fefbe94c5)
- [Hải dớ](https://docs.google.com/spreadsheets/d/1SsEA4SC1RV1_-Dejz4zUVIsXBPBkKMfe11Ik6NUOmMQ/edit?gid=0#gid=0)
- [Zinyan91](https://docs.google.com/spreadsheets/d/e/2PACX-1vTId_2VGY1MeQdeH6OU6Oja27zMe91mHmYUl6aVWsyKlcFBuLwvr2M-9uaBRWDUqxPAi5xE-pqief4d/pubhtml#gid=1662926245)


**B3:** Làm ra file `.xml` _(nếu muốn windows được cài nhẹ, còn không khỏi tạo cũng được)_ tên gọi khác là file `unattended`.

- Cách 1: lên web này tạo [Link](https://schneegans.de/windows/unattend-generator/).

- Cách 2: tải file `.xml` có sẵn trên github [Link](https://github.com/memstechtips/UnattendedWinstall/blob/main/autounattend.xml#L10)
> ❗**Hãy lưu ý trước khi dùng file này để cài win**
>
> File `unattended` của `Winhance` mức độ `debloat` sâu nên sẽ xóa hết các phần mềm của `Microsoft Store` cho dù bạn có tải `Microsoft Store` rồi restart máy sẽ `auto remove Microsoft Store` ra khỏi máy.
>
> **Cách fix:** mở file `unattended` ở notepad rồi tìm dòng `'Microsoft.WindowsStore'` xóa bỏ hoặc comment `#` ở đằng trước.
>
> Ví dụ: `#   'Microsoft.WindowsStore'`
>
> Tương tự cho mấy phần mềm khác.

**B4:** Cắm usb cứu hộ sao đó restart máy, trong lúc đang restart bấm các nút hàng `F1 - F12`, để chọn môi trường trong usb cứu hộ
> **Cách nhanh và lười**: Khi ở desktop máy thì tạo shortcut và nhập `shutdown /r /fw /t 0` next next rồi chạy hoặc mở cmd nhập lệnh chạy rồi máy sẽ tự vào bios.

**B5: (Optional)** Coi theo video cài windows của "Neyako Phạm" [Link](https://vt.tiktok.com/ZS9JhErjobKJd-0MDv3/) hoặc coi [file](./File/Hướng%20dẫn%20cài%20đặt%20Windows%20với%20WinNTSetup%20chuẩn%20UEFI.pdf)
> Đủ ổn để nghe theo để cài win nhưng hãy xem README này để dễ hơn.
>
> Lúc khi window khởi động và cài đặt thông tin cho hệ thống thì bạn có thể vượt không yêu cầu password và đăng nhập microsoft. Lúc chọn khu vực nhấn Shift + F10 hiện ra cửa sổ cmd.
> 
> ```cmd
> oobe\bypassnro
> ```

**B6: (Optional)** Sau khi cài lại win thì hãy chạy `talon` để được performance tốt nhất
> 🐧 Mặc dù file `unattended` đã đủ nhưng `talon` sẽ cho lại result tốt nhất, tất nhiên sẽ là `Optional` thôi vì `unattended` đã đủ cho ngườ dùng cơ bản.

Mở `PowerShell` với quyền admin

**Talon:** Bản full 

```bash
irm https://debloat.win/now | iex
```

**Talon Lite:** Bản cơ bản nếu sợ 😉

```bash
irm https://debloat.win/lite | iex
```

**B7:** Cài lại các phần mềm, sau khi cài lại windows

Mở powershell với quyền admin

```bash
irm christitus.com/win | iex
```

Tải Microsoft Store (Optional): [Link](https://github.com/stdin82/htfx/releases/tag/v0.0.24)
> Chạy `Add-Store.cmd` là được.

_Lưu ý:_ Do 1 số phần mềm cần cài nằm trên Microsoft Store, mà gần đây nó hay bị lỗi.

> Sửa lỗi Microsoft Store khi bị lỗi Code: 0x80244022

Mở PowerShell với quyền Admin

```bash
Get-AppxPackage -AllUsers *WindowsStore* | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

**B8:** Đi kiếm chỗ cài đặt driver bị thiếu (VD: với máy Lenovo thì cài Lenovo Vantage, vô phần system update)
- Snappy Driver
- [Lenovo Tool Kit](https://github.com/LenovoLegionToolkit-Team/LenovoLegionToolkit/releases) (Dành cho máy Lenovo)

**B9:** Cài phần mềm Winhance, để tắt/bật windows update

**B10:** Active windows và Microsoft Office

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