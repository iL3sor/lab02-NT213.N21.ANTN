# Lab 2 

### Challenge 1:

Kiểm tra source HTML của trang web ta thấy có thông tin được leak ra như sau:

>![](https://i.imgur.com/s5oKxOk.png)

- Thử đăng nhập với tài khoản trên, ta có kết quả là đăng nhập thành công, tuy nhiên, role của ta vẫn là `support`

>![](https://i.imgur.com/MhqFuGs.png)


- Kiểm tra cookie thấy có 1 trường `role` với giá trị `support`, ta thử đổi nó thành `admin` và có thể solve challenge

>![](https://i.imgur.com/3Y9OR7Y.png)


>![](https://i.imgur.com/1nVtGyc.png)

:::success
**Flag**: hiadminyouhavethepower
:::

### Challenge 2:

Kiểm tra mã nguồn public của trang challenge, ta thấy đoạn script như sau

>![](https://i.imgur.com/SdttAsD.png)

Decode byte sang text, ta có bản rõ như sau:

>![](https://i.imgur.com/Ft6lklX.png)

Theo đó, nếu username và password cùng bằng `Cyber-Talent` thì là đúng, do đó ta solve được challenge

>![](https://i.imgur.com/sZDl2A1.png)

:::success
**Flag:** J4V4_Scr1Pt_1S_Aw3s0me
:::

### Challenge 3

Tương tự 2 challenge trên, kiểm tra source web ta thấy có đoạn javascript đã được encode dưới dạng jsfuck như sau:

>![](https://i.imgur.com/37VWN8f.png)

Deobfuscator ta thu được kết quả

```javascript!
String.fromCharCode(102, 117, 110, 99, 116, 105, 111, 110, 32, 99, 104, 101, 99, 107, 40, 41, 123, 10, 10, 118, 97, 114, 32, 117, 115, 101, 114, 32, 61, 32, 100, 111, 99, 117, 109, 101, 110, 116, 91, 34, 103, 101, 116, 69, 108, 101, 109, 101, 110, 116, 66, 121, 73, 100, 34, 93, 40, 34, 117, 115, 101, 114, 34, 41, 91, 34, 118, 97, 108, 117, 101, 34, 93, 59, 10, 118, 97, 114, 32, 112, 97, 115, 115, 32, 61, 32, 100, 111, 99, 117, 109, 101, 110, 116, 91, 34, 103, 101, 116, 69, 108, 101, 109, 101, 110, 116, 66, 121, 73, 100, 34, 93, 40, 34, 112, 97, 115, 115, 34, 41, 91, 34, 118, 97, 108, 117, 101, 34, 93, 59, 10, 10, 105, 102, 40, 117, 115, 101, 114, 61, 61, 34, 67, 121, 98, 101, 114, 34, 32, 38, 38, 32, 112, 97, 115, 115, 61, 61, 32, 34, 84, 97, 108, 101, 110, 116, 34, 41, 123, 97, 108, 101, 114, 116, 40, 34, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 32, 67, 111, 110, 103, 114, 97, 116, 122, 32, 92, 110, 32, 70, 108, 97, 103, 58, 32, 123, 74, 52, 86, 52, 95, 83, 99, 114, 49, 80, 116, 95, 49, 83, 95, 83, 48, 95, 68, 52, 77, 78, 95, 70, 85, 78, 125, 34, 41, 59, 125, 32, 10, 101, 108, 115, 101, 32, 123, 97, 108, 101, 114, 116, 40, 34, 119, 114, 111, 110, 103, 32, 80, 97, 115, 115, 119, 111, 114, 100, 34, 41, 59, 125, 125)
```

Tương đương với code sau

```javascript!
function check(){\n\nvar user = document["getElementById"]("user")["value"];\nvar pass = document["getElementById"]("pass")["value"];\n\nif(user=="Cyber" && pass== "Talent"){alert("                      Congratz \\n Flag: {J4V4_Scr1Pt_1S_S0_D4MN_FUN}");} \nelse {alert("wrong Password");}}
```

Có username và mật khẩu, và cả flag, ta solve được challenge

:::success
**Flag:** FLAG{J4V4_Scr1Pt_1S_S0_D4MN_FUN}
:::


### Challenge 4:

Trang web có chức năng nhập tên, sau đó nó sẽ trả về cho chúng ta tên được viết dưới dạng cong cong như hình sau:

>![](https://i.imgur.com/KY5EvcN.png)

Thử payload XSS thì thấy nó đã bị filter:

>![](https://i.imgur.com/AwsFybf.png)

Thử lại payload khác là `<img src=x onerror=alert(1)>` thì thấy trả về flag

>![](https://i.imgur.com/QItp4TQ.png)

Thậm chí vào console gõ `alert(1)` cũng ra flag.
:::success
**Flag:** ciyypjz
:::


### Challenge 5:

Kiểm tra source ta thấy đường dẫn đáng ngờ như sau:

>![](https://i.imgur.com/YLW6oBO.png)

Dựa vào đó ta tìm được 1 trang admin

>![](https://i.imgur.com/4yMKuMy.png)

Tiếp tục view-page source ta thấy đường dẫn đáng nghi khác nằm trong 1 thẻ input

>![](https://i.imgur.com/iu5PqPx.png)

Truy cập vào đó ta có được flag (đã bị md5 hash)

>![](https://i.imgur.com/Lu7EjQR.png)

:::success
**Flag:** badboy
:::

### Challenge 6:

Trang web có một ô input cho phép nhập vào email, thử 1 payload bình thường theo đúng yêu cầu của input, ta thấy kết quả trả ra như sau:

>![](https://i.imgur.com/TmDPSzG.png)

Các payload bất thường vẫn hoạt động, chỉ cần ta loại bỏ type=email trong input, trang web sẽ không kiểm tra gì thêm (chỉ cần payload có @ và . là được)

Vì thấy có hành vi insert data, ta thử khai thác SQL injection, nhưng không thành công.

Đọc lại gợi ý, ta đoán có thể khai thác Command injection

>![](https://i.imgur.com/ASDIQFT.png)

Thử với payload sau ta thấy thành công và nhận được flag.

```
`ls` ; @.
```

:::success
**Flag:** hgdr64.backup.tar.gz
:::

### Challenge 6:

Kiểm tra source trang web ta thấy

>![](https://i.imgur.com/Qkkj0MA.png)

Đăng nhập theo tài khoản trên ta nhận được thông báo như sau:

>![](https://i.imgur.com/1w9UUlr.png)

Kiểm tra cookie ta thấy có 1 trường `Authentication` có giá trị là 1 mã base64 encode

Decode ra ta được giá trị `login=Guest`

Sửa lại thành `login=admin` và encode lại sau đó nhét vào cookie là ta có flag

>![](https://i.imgur.com/5KRhqD9.png)


:::success
**Flag:** FLag{B@D_4uTh1Nt1C4Ti0n}
:::


### Challenge 7

Theo hướng dẫn của đề, ta đăng nhập với tài khoản `demo/demo`

Đăng nhập vào, khi truy cập đường dẫn `profile` ta thấy nó nhận tham số từ URL như sau: `/profile.php?user=demo`

Thử thay bằng `admin` thì thấy thông báo access denied

Kiểm tra cookie ta thấy có trường user đang giữ giá trị `demo`, ta thay nó thành `admin` và thành công khai thác xác thực -> có được flag.

>![](https://i.imgur.com/6R8Me4T.png)

:::success
**Flag:** 15716a249064f7e9684a816dcdb05282
:::


### Challenge 8:

Tìm trong đường dẫn `/robots.txt` ta thấy có thông tin sau

>![](https://i.imgur.com/mXLIwbU.png)

Dựa theo trên ta tìm được source của trang web

>![](https://i.imgur.com/99O2jrr.png)


Theo đó `user`=Cyber-Talent và `pass`=Cyber-Talent

Kết quả:

>![](https://i.imgur.com/KMmB7G1.png)

Decode mã morse trên ta có 

>![](https://i.imgur.com/7LAGc6w.png)


:::success
**Flag:** FLAG(I-KN0W-Y0U-AR3-M0RS3)
:::

### Challenge 9

Vào trang web ta thấy nó đang gặp 1 lỗi và hiện ra như sau:

>![](https://i.imgur.com/kC86gUz.png)


Thử thêm tham số `welcome` vào URL, ta thấy nó hiện ra lỗi tiếp theo

>![](https://i.imgur.com/mlsSukN.png)

Tiếp tục như trên ta được flag

>![](https://i.imgur.com/q3GnD0m.png)

:::success
**Flag:** FLAG{k33p_c4lm_st4rt_c0d!ng}
:::


### Challenge 10

:::danger
Không load được challenge
:::

### Challenge 11

:::danger
Không load được challenge
:::

### Challenge 12

Dùng `dirsearch` để scan, ta thấy các thư mục con của git được public

>![](https://i.imgur.com/0qo8sh1.png)

Dùng git-dumper để dump repository về máy, ta có các file sau.

>![](https://i.imgur.com/1l1UO3s.png)

Xem thử nội dung flag.php

>![](https://i.imgur.com/ork0Yvn.png)


Dùng secretkey trên submit thì solve đc bài lab

:::success
**Flag:** be607453caada6a05d00c0ea0057f733
:::

### Challenge 13

Truy cập trang web, ta thấy có chức năng đăng nhập, tìm trong mã nguồn có tài khoảng `bob/password` nhưng sau khi đăng nhập không có thông tin gì thêm.

>![](https://i.imgur.com/t1YSyH5.png)


Thử payload SQLinjection thì thấy dễ dàng bypass và đăng nhập thành công


Payload:
```
admin' or 1=1 -- 
```

>![](https://i.imgur.com/iUkrt5N.png)

:::success
**Flag:** flag{!njection_3v3ry_wh3r3}
:::

### Challenge 14

Kiểm tra ta thấy có comment như sau:

>![](https://i.imgur.com/duT1gZ2.png)

Dùng burpsuite để truy cập trang web và thay đổi user-agent trong http header thành `givittome`, ta truy cập được sâu hơn.

>![](https://i.imgur.com/t0pp6Ss.png)

- Kiểm tra lại response, ta thấy flag nằm trong 1 header như sau

>![](https://i.imgur.com/QUSuxxv.png)


:::success
**Flag:** W3lcome_Ag3nt8
:::

### Challenge 15

Dùng dirsearch kiểm tra các đường dẫn trên trang web, ta thấy các thư mục .git được public

>![](https://i.imgur.com/7U4FG7a.png)

Dùng git-dumper để dump các tệp về máy, ta được 3 file là `api.php`, `index.php` và `contact_process.php`

Xem file `api.php` ta thấy

>![](https://i.imgur.com/JyzIaAa.png)

Vậy ta cần tìm `$apikey` sau đó thiết lập 1 cookie có giá trị bằng với apikey này là có được flag.

Tìm trong 2 file còn lại, ta thấy trong file `contact_process.php` có secret như sau:

>![](https://i.imgur.com/kI1Dmtd.png)

Thử lấy giá trị đó ra 

>![](https://i.imgur.com/b59Llf6.png)

Tạo 1 cookie có name=`api_key` và value `746869735f69735f746f705f736563726574` sau đó reload lại trang web ta lấy được flag như hình.

>![](https://i.imgur.com/HGFhUAz.png)

:::success
**Flag:** Flag{g!7_!5_4w350m3_XD!!}
:::

### Challenge 16

Khi nhập vào input, ta thấy payload được reflected ở trong html

>![](https://i.imgur.com/jkwsX81.png)

Thử lại với Payload có thể trigger XSS

```
?name=abc%27%20onload=alert(1)
```


:::success
**Flag:** Flag{X55_D4mn_G00D}
:::


### Challenge 17

Mục tiêu của bài này là trigger được XSS trong trang web.

Để ý ta thấy có chức năng nhập tên và hiển thị tên lên màn hình, thử `<script>alert(1)</script>` ta thấy bị filter và lọc bỏ.

>![](https://i.imgur.com/ubwXLka.png)

Thử lại `<img scr=x onerror=alert(1)>` thì thấy có flag

>![](https://i.imgur.com/s9ZRvy9.png)


:::success
**Flag:** Flag{N!c3_Y0u_G07_My_X55}
:::

### Challenge 18

Dùng `dirsearch` tìm kiếm, ta tìm được trang `signup.php` cho phép tạo tài khoản mới.

Đăng kí tài khoản và đăng nhập, ta thấy có chức năng thay đổi password

>![](https://i.imgur.com/fixDVpc.png)

Thử quan sát request của nó, ta thấy có đính kèm `userid` trong tham số, ta thay nó bằng 1 để đổi mật khẩu admin (lưu ý đổi cả `userid` trong cookie sang 1)

>![](https://i.imgur.com/OdoKSIX.png)

>![](https://i.imgur.com/sGQrkSm.png)


Kết quả đăng nhập bằng tài khoản admin và lấy flag

>![](https://i.imgur.com/JobC7sH.png)

:::success
**Flag:** FLAG{Y0U_F0UND_MY_ID0R!!}
:::


### Challenge 19

Dùng `dirsearch` ta quét được 2 đường dẫn sau:

>![](https://i.imgur.com/6tdVV9X.png)


Truy cập vào `/files` ta có 1 list các file như sau

>![](https://i.imgur.com/JFej8nH.png)

Tìm kiếm trong các thư mục trên không có kết quả, ta thử các payload path traversal, khi thử với `/files../` ta thành công (nginx)

>![](https://i.imgur.com/sApcuDF.png)

Trong thư mục `/home` có file flag.txt

>![](https://i.imgur.com/eHdlvx3.png)


:::success
**Flag:** FLAG{Nginx_nOt_aLWays_sEcUre_bY_The_waY}
:::

### Challenge 20

Khi nhập đại 1 input vào ô tìm kiếm, ta nhận được các hint như sau:

>![](https://i.imgur.com/7pT7CpZ.png)


>![](https://i.imgur.com/osw5c7n.png)

Quay lại tìm kiếm với từ khóa `Momen` ta được kết quả như sau

>![](https://i.imgur.com/GwYqHOf.png)

Vào `hint.php` có thêm 1 yêu cầu tham số nữa, có vẻ là tham số `show` với giá trị `True` hoặc `False`

Ta được mã nguồn trang web như sau:

>![](https://i.imgur.com/K7fBwn0.png)


Thêm trường `Referer: http://cyberguy` vào header ta có flag1 = `0xL4ugh{H3r0_`

>![](https://i.imgur.com/6mxozBQ.png)

Tìm 2 chuỗi khác nhau có MD5 hash giống nhau hoặc bắt đầu với `0e` ta lấy được flag2 (s1: `240610708` và s2: `QNKCDZO`)

>![](https://i.imgur.com/WlVLXp5.png)

Cuối cùng, sử dụng hint `robots.txt` đề lấy flag cuối của challenge

>![](https://i.imgur.com/ZCNaxxe.png)

tuy nhiên khi truy cập `/robots.txt.php` thì bị 403, thử đổi Method thành PUT và đính kém cookie cùng trường `Referer` trong request thì ta nhận được kết quả như hình

>![](https://i.imgur.com/5n8qZyD.png)

Dùng user-agent = `G3t_My_Fl@g_N0w()` để gửi request tới `/user_check.php` ta có được flag

>![](https://i.imgur.com/yq5vRFn.png)


:::success
**Flag:** G3t_My_Fl@g_N0w()
:::

### Challenge 21

Truy cập trang web ta thấy:

>![](https://i.imgur.com/4RtZBde.png)

Kiểm tra header của request, thấy `Accept-Language` đang để tiếng Anh `en-US,en;q=0.9` - ta đổi lại thành tiếng Đức với mã là `de`

>![](https://i.imgur.com/kB9OVhn.png)

Kết quả:

>![](https://i.imgur.com/ZgyzfY5.png)


:::success
**Flag:** FLAG{HE4DERS_M4G1C}
:::


### Challenge 22

Quét các thư mục ta tìm được /.git/ vẫn để public

>![](https://i.imgur.com/HQQWrNg.png)

Dump nó về và kiểm tra thư tệp index.php, ta thấy để có được flag thì thỏa các điều kiện sau:

>![](https://i.imgur.com/jazCUWh.png)

Tóm tắt:
- Tạo 1 request post
- Giá trị của tham số Q = giá trị của session['flooog'] = base64decode(cookie['secret'])
- Đảm bảo thời gian từ lúc truy cập đến hiện tại < 3s


Để thực hiện công việc đó nhanh chóng, ta dùng code như sau:

```python!
import requests
import base64
from urllib.parse import unquote

url = "http://wcamxwl32pue3e6m5l3n94wbq36o1y3e8d9yhxvm-web.cybertalentslabs.com/index.php"

r = requests.Session()

get1 = r.get(url=url)
s =  unquote(get1.cookies['secret'])
ck = base64.b64decode(s)

post1 = r.post(url=url, data={'Q':ck})

print(post1.text)
```

Kết quả:

>![](https://i.imgur.com/RdUHjTa.png)


:::success
**Flag:** flag{s0n1c_isnt_that_fast_after_all}
:::