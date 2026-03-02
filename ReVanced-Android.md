MicroG là môi trường thay thế cho dịch vụ google play, giúp các ứng dụng google như youtube, google photo... hoạt động bình thường trên các rom thuần AOSP không có dịch vụ google play.

> ❗Cài đặt Micro-RE về (**Bắt buộc cho cả 2 cách**): [link](https://github.com/MorpheApp/MicroG-RE/releases)

## Cách 1: Dùng morphe manager
Morphe manager là công cụ giúp cài các ứng dụng google đã được mod lại để hoạt động với microG.

Morphe manager: [Link](https://github.com/MorpheApp/morphe-manager/releases)

Và cài thêm apk gốc của youtube: Trên morphe sẽ có gợi ý phiên bản cần tải và cho sẵn link apk mirror.

_Các bước thực hiện:_

1. Cài xong Morphe → mở lên
2. Chọn **Youtube Morphe**
3. Tải APK mà nó gợi ý (tự động chuyển sang APKMirror để tải YouTube gốc)
4. Vào lại app Morphe → chọn APK gốc đã tải
5. Ấn **Patch** → đợi
6. Bấm **Install** → XONG


Còn [google photo](https://github.com/VVispy/revanced-builder/releases/download/55/google-photos-revanced-v7.63.0.869312946-arm64-v8a.apk) không giới hạn thì cài file apk này về và chạy apk là xong.

### Lựu chọn thêm cho morphe manager:
Reddit: Thêm patch vào morphe manager
- `https://raw.githubusercontent.com/wchill/patcheddit/refs/heads/main/patches-bundle.json`

RVX Morphed Patches: 
- `https://raw.githubusercontent.com/wchill/rvx-morphed/refs/heads/main/patches-bundle.json`

RVX Patches Anddea:
- `https://raw.githubusercontent.com/Jman-Github/ReVanced-Patch-Bundles/bundles/patch-bundles/anddea-patch-bundles/anddea-latest-patches-bundle.json`

Piko Twitter/X:
- `https://raw.githubusercontent.com/Jman-Github/ReVanced-Patch-Bundles/bundles/patch-bundles/piko-patch-bundles/piko-latest-patches-bundle.json`






## Cách 2: Dùng Obtainium cài về lụm luôn và tự động update

### Morphe - Config One

YouTube, YouTube Music

### ReVanced - Config Two (Additional)

YouTube, YouTube Music, Google Photos, Facebook, Instagram (distraction free), Messenger, Proton Mail, Proton VPN, Reddit, SoundCloud, TikTok, Twitch

_Các bước thực hiện:_

1. Cài đặt Obtainium
2. Tải file JSON configuration:
   - [Config One](https://gitlab.com/-/snippets/4883030/raw/main/obtainium-config.json?inline=false) / [Config Two (Additional)](https://gitlab.com/-/snippets/4926053/raw/main/extra-obtainium-config.json?inline=false) 
3. Mở Obtainium, vào **Import/Export** (tab ở dưới), chọn **Obtainium Import**, và chọn file JSON đã tải
4. Quay lại tab **Apps** - các ứng dụng sẽ xuất hiện
5. Obtainium sẽ tự động kiểm tra và thông báo khi có phiên bản mới của các ứng dụng.