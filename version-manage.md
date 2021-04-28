
## Version control



## use this rule for applications:
```
x.y.z
```
Where:

-   x = main version number, 1-~.
-   y = feature number, 0-9. Increase this number if the change contains new features with or without bug fixes.
-   z = hotfix number, 0-~. Increase this number if the change only contains bug fixes.

Example:

-   For new application, the version number starts with 1.0.0.
-   If the new version contains only bug fixes, increase the hotfix number so the version number will be 1.0.1.
-   If the new version contains new features with or without bug fixes, increase the feature number and reset the hotfix number to zero so the version number will be 1.1.0. If the feature number reaches 9, increase the main version number and reset the feature and hotfix number to zero (2.0.0 etc)ber


## Yêu cầu đảm bảo tương thích

```
x.y.z
``` 
Trong đó:

-   _**x – MAJOR**_  **_version:_**  tăng khi bạn thực hiện các thay đổi dẫn đến  **KHÔNG** tương thích ngược.
-   _**y – MINOR**_  **_version:_** tăng khi bạn thêm tính năng và vẫn đảm bảo tương thích ngược (backwards-compatible).
-   _**z – PATCH**_  **_version:_** tăng khi bạn thực hiện fix lỗi xử lý bên trong và vẫn đảm bảo tương thích ngược (backwards-compatible)

END.

## Yêu cầu đảm bảo giao diện

-   Software mà sử dụng Semantic Versioning thì  **PHẢI** cung cấp và mô tả một danh sách public API. API này có thể được mô tả ngay trong chính mã nguồn hoặc trong tài liệu đi kèm. Các API cần phải được mô tả chính xác và đầy đủ.
-   Một phiên bản bình thường  **PHẢI** có dạng  _x.y.z_  (như đã nói ở trên) trong đó  _x, y_ và _z_  là các số nguyên không âm,  **KHÔNG ĐƯỢC**  chứa số 0 đằng trước và phải đánh tăng dần sau mỗi lần release. Ví dụ:  _1.9.0 → 1.10.0 → 1.11.0_
-   Khi một phiên bản mới đã được phát hành thì nội dung của phiên bản đó  **KHÔNG ĐƯỢC**  sửa đổi. Mọi sửa đổi xảy ra sau đó  **PHẢI** được phát hành dưới phiên bản mới ( X ).
-   Major version X sẽ bằng 0  _(0.y.z)_  với những phiên bản phát triển ban đầu. Đó là thời điểm mà bất cứ điều gì có thể thay đổi bất cứ lúc nào. Public API của software khi đó là chưa đẩy đủ và không ổn định.
-   Version 1.0.0 là phiên bản mà public API của nó đã khá đầy đủ (ổn định hay không thì chưa biết). Mọi sự thay đổi từ đó về sau sẽ phụ thuộc vào sự thay đổi được thực hiện đối với public API này.
-   Patch version Z (x.y.Z | x > 0)  **PHẢI** được tăng nếu phiên bản mới chỉ fix các lỗi hoạt động bên trong của API và vẫn đảm bảo tương thích ngược (interface của public API không thay đổi)

### hungnt1 @ SA - CXVIEW
