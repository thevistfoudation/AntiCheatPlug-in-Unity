# AntiCheatPlug-in-Unity
AntiCheatPlug-in
!!! Chú ý:
+ Vào nhánh main nếu bạn là người thích mầy mò và sáng tạo.
+ Vào nhánh Develop nếu bạn là người thích ăn sẵn lấy về và sử dụng.

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
+ Tool này giúp chúng ta tạo ra các giá trị Prefs được lưu trữ và mã hóa và có thể sử dụng thoải mái mà ko lo cheater tìm đc giá trị
+ Ngoài ra để phát hiện cheat chúng ta còn có thể tích hợp thêm tool scripts này:
  + Cách 1: GameObject > Create Other > Code Stage > Anti-Cheat Toolkit > Injection Detector
  + Cách 2: tạo ra game object rồi add thêm component mới Component > Code Stage > Anti-Cheat Toolkit
  ![image](https://user-images.githubusercontent.com/47918431/170865789-0e94db28-9c6d-4562-bc10-d46a11baae7f.png)
+ `Auto Start`: Cho phép việc dò cheater sau khi Scene Load. Hoặc có thể sử dụng thư viện và gọi hàm bắt đầu dò
+ ![image](https://user-images.githubusercontent.com/47918431/170866028-1a3243e7-e1e3-432e-b665-bfe0cb82d9cc.png)
+ `AutoDispose` : Cho phép tự động loại bỏ chính mình sau khi dò ra được Cheater.
+ `Keep Alive`: Cho phép dò ở Scene Load mới(load sang scene khác hiểu đơn giản là chuyển scene).
<a name="SpeedHack"></a>
### SpeedHackDetector
+ https://www.youtube.com/watch?v=I5EUjVbLaNY&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=5
+ Nôm na là cách Cheat mà tất cả chúng ta khi chơi game đều có thể làm được là cheat tốc độ của nhân vật ví dụ: tốc độ đánh , tốc độ di chuyển , tốc độ.
+ Và Plugin này ra đời cũng để phát hiện và chặn User có thể can thiệp vào luồng dữ liệu(tốc độ) trong game.
+ ![image](https://user-images.githubusercontent.com/47918431/171194223-c48bf7d6-de2c-4122-ac4a-605586449a7b.png)
  + `Interval`: là khoảng thời gian tính bằng giây(nên để 1 giây để tiết kiệm hiệu năng)
  + `Threshold`: là hệ số tốc độ tối đa và tối thiểu trong Game cho phép với `Min là 0.2` và `Max là 5`
  + `Max False Positives`: Là độ sai số tối đa được cho phép trong Game(lỗi đồng hồ hoặc BUG T_T). Ví dụ khi xảy ra vấn đề thì tính năng này giúp bỏ qua kết quả sai đó và không coi đó là 1 hành động Hack. Ví dụ thời gian sẽ scale trong khoảng từ 1 -5 giây thì có thể bộ hack sẽ quét được và coi như đó là 1 trường hợp hack còn khi tích hợp và chỉnh độ sai số thì bộ quét sẽ bỏ qua và check tiếp các case khác.
  + `Cool Down`: Cho phép đặt lại bộ đếm dưới luồng code để phòng trường hợp(xảy ra 1 số bug hoạt động sai đếm liên tục dẫn đến bộ đếm sai giá trị và Tool sẽ quét và phát hiện hack tốc độ sai) thì lập tức set giá trị về 0 và tắt tính năng cooldown đi
  + ![image](https://user-images.githubusercontent.com/47918431/171207010-e3a302c0-bf50-4c82-a13f-eac6d1683ddc.png)

<a name="WallHackDetector"></a>
### WallHackDetector
+ https://www.youtube.com/watch?v=xSZkQv7TAgU&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=6
<a name="InjectionDetector"></a>
### InjectionDetector
+ https://www.youtube.com/watch?v=xrJbzvG7WJo&list=PLbTYvIYxIXSj5p9qn3lcsoUc1R9KnSOIb&index=7

<a name="When"></a>
## III.Tổng Kết

