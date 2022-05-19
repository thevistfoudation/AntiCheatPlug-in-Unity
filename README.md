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
+ Sau khi thay đổi kiểu giá trị sang dạng `bscured` Cheater vẫn có thể nhìn thấy những giá trị được hiển thị lên tuy nhiên giá trị gốc đã được bảo vệ và Cheater sẽ ko thể can thiệp và thay đổi thông số trong game.
<a name="ObscuredPrefs"></a>
### Obscured Prefs
+ https://www.youtube.com/watch?v=Hf0MOct9rDQ&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=4
<a name="ObscuredFile"></a>
### Obscured File &&  Obscured Prefs
+ https://www.youtube.com/watch?v=JCNEl1xQ0WE&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=4
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

