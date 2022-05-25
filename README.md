# AntiCheatPlug-in-Unity
AntiCheatPlug-in
## Mục Lục
- [I.Cách Setup Plugin vào project](#What)
- [II.Cách sử dụng Plugin?](#How)
- [III.Tổng kết  ?](#When)
<a name="What"></a>
## I.Cách Setup Plugin ?
+ Sau khi clone Plugin về sẽ bắt đầu import vào Project bằng cách kích đúp vào package(nếu đã có sẵn hãy loại bỏ package cũ khỏi project)
+ Chọn tab Tool > Code Stage > Anti-Cheat ToolKit > Settings để kiểm tra thông tin về package gồm 
  + Phiên bản Package đang dùng 
  + Các thư viện đang có trong package
  + ![image](https://user-images.githubusercontent.com/47918431/169299750-08d15a75-3760-4ef7-a0cb-2371270f780d.png)
<a name="How"></a>
## II.Cách sử dụng Plugin và Plugin gồm những gì ?
- [`types` Obscured types](#Obscuredtypes)
- [`Prefs` Obscured Prefs ](#ObscuredPrefs)
- [`FileandPrefs` Obscured File &&  Obscured Prefs ](#ObscuredFile)
- [`SpeedHackDetector` SpeedHackDetector](#SpeedHack)
- [`WallHackDetector` WallHackDetector ](#WallHackDetector)
- [`InjectionDetector` InjectionDetector](#InjectionDetector)
<a name="Obscuredtypes"></a>
### Obscured types
+ https://www.youtube.com/watch?v=QiznofE8xD4&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=2
+ Thường đa số các Cheater sẽ dùng tool để xác định các biến trong game như tiền , life point , tài nguyên bằng cách quét các thông số hiển thị trên game và lấy các giá trị đó ra và thay đổi.
+ 1 số Tool Cheat được dùng: Cheat Engine, ArtMoney (PC), Game CIH, Game Guardian (Android).
+ Để hạn chế tình trạng đó thì Package sẽ có bộ thư viện hỗ trợ để ẩn các chỉ số đi 
+ ![image](https://user-images.githubusercontent.com/47918431/169303770-640c80e2-67fc-46be-a7a0-522a039621f1.png)
+ Sau khi thay đổi kiểu giá trị sang dạng `Obscured` Cheater vẫn có thể nhìn thấy những giá trị được hiển thị lên tuy nhiên giá trị gốc đã được bảo vệ và Cheater sẽ ko thể can thiệp và thay đổi thông số trong game.
+ Mặc dù được che giấu đi nhưng trong Game để tăng tính bảo mật sẽ thực hiện thêm 1 số phép tính nhằm thay đổi và che giấu tuyệt đối giá trị trong game
+ ![image](https://user-images.githubusercontent.com/47918431/169311314-b7cd45a2-d69b-4284-808d-8b6c88181e0b.png)

<a name="ObscuredPrefs"></a>
### Obscured Prefs
+ https://www.youtube.com/watch?v=Hf0MOct9rDQ&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=4
+ PlayerPrefs là gì
  + `PlayerPrefs` là 1 lớp lưu trữ các tùy chọn của người chơi giữa các turn, Class này có thể lưu trữ cacsc giá trị như String,Float,Int vào Hệ điều hành của người dùng.
  + Tùy thuộc Hệ điều hành mà class lưu trữ này sẽ được lưu ở tùy từng file phụ thuộc vào nền tảng
    + Windows: HKCU\Software\ExampleCompanyName\ExampleProductName 
    + Linux: ~/.config/unity3d/ExampleCompanyName/ExampleProductName
    + Windows Store Apps : %userprofile%\AppData\Local\Packages\[ProductPackageId]\LocalState\playerprefs.dat
    + Android :  /data/data/pkg-name/shared_prefs/pkg-name.v2.playerprefs.xml
    + macOS: /Library/Preferences/[bundle identifier].plist
  + 1 số Hàm được dùng trong PlayerPref
  + ![image](https://user-images.githubusercontent.com/47918431/169842335-4229b47d-0991-40bf-a291-2deffb446746.png)
 + `Tuy Nhiên UNITY lại ko khuyến người dùng cách này để lưu trữu và sử dụng dữ liệu vì nó đc lưu cục bộ và ko được mã hóa và User có thể dễ dàng can thiệp và sử dụng những dữ liệu`
 + Để thay thế và lưu trữ 1 cách bảo mật hơn:
  + sử dụng thêm thư viện `using CodeStage.AntiCheat.Storage;`
  + Thay vì dùng như này:
    ![image](https://user-images.githubusercontent.com/47918431/170180888-a28cee0c-71fb-46ca-a3b1-38a8c9e65815.png)
  + Có thể dùng như thế này:
    ![image](https://user-images.githubusercontent.com/47918431/170182337-4d96777f-5109-4830-a5d9-c62fc7858e5c.png)
<a name="ObscuredFile"></a>
### Obscured File &&  Obscured Prefs
+ https://www.youtube.com/watch?v=JCNEl1xQ0WE&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=4
+ Anti Cheat Tool Kit được tích hợp cả trong cửa sổ của Unity Editor
+ Để mở cửa sổ của Anti CheatTool Kit có thể bằng cách:
  + Tools > Code Stage > Anti-Cheat Toolkit > Prefs Editor as Tab
  + ![image](https://user-images.githubusercontent.com/47918431/170267352-5123467e-25bb-4ebe-9a0e-bec6760e9f7c.png)
  + "+" được đùng để add thêm mới Pref bằng cách chọn loại biến và kích hoạt mã hóa nó sau đó đặt key và giá trị và bấm `OK`
  + "Refresh" được dùng để quét lại tất các Prefs đã được update vào list
  + "Key Descending" được dùng để sắp xếp , các giá trị có thể khác: Key Ascending, Type, Obscurance
  + Search field - được dùng để nhập vào lọc ra các bản ghi có chứa name đc tìm
  + "X " dùng để xóa bản ghi đó
  + "S" dùng để lưu những thay đổi của bản ghi đó
  + "E"/"D" dùng để mã hóa và giải mã của bản build đó
  + "..." dùng để copy dữ liệu ra bảng

<a name="SpeedHack"></a>
### SpeedHackDetector
+ https://www.youtube.com/watch?v=I5EUjVbLaNY&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=5
<a name="WallHackDetector"></a>
### WallHackDetector
+ https://www.youtube.com/watch?v=xSZkQv7TAgU&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=6
<a name="InjectionDetector"></a>
### InjectionDetector
+ https://www.youtube.com/watch?v=xrJbzvG7WJo&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=7

<a name="When"></a>
## III.Tổng Kết

