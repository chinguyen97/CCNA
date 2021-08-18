### Địa chỉ IPv4
https://cuongquach.com/tu-hoc-ccna-dia-chi-ip-la-gi.html
#### 1. Giới thiệu

#### 2. Các loai địa chỉ IPv4
- Địa chỉ host: Là địa chỉ để định danh duy nhất cho mỗi máy tính trong 1 vùng mạng
VD: 192.168.1.2
- SubnetMask: Là giá trị để xác định phần host và phần mạng của 1 địa chỉ IPv4 để từ đó kết hợp với địa chỉ host sẽ tìm ra địa chỉ mạng của IPv4 VD: 255.255.255.0
- Địa chỉ mạng: Là tất cả các bit phần host bằng 0
VD: 192.168.1.0/24
- Địa chỉ Broadcast : Là địa chỉ quảng bá, tất cả các host của nó bằng 1. 
VD: 192.168.1.255.
Khi 1 gói tin được gửi đến địa chỉ broadcast thì tất cả các máy tính trong mạng LAN sẽ nhận được. 

#### 3. Chia địa chỉ IP
Có hai cách chia địa chỉ IP: Classfull và LVSM 
##### 3.1. Classfull - Chia đều
B1: Xác định số mang con cần phải chia
B2: Xác định số bit cần phải mượn từ trái qua phải sao cho thỏa mãn điều kiện: 

2^n >=số mạng con  (n số bít mượn)

m = 32-n-SubnetMask Hiện tại

Bước nhảy: 2^m

B3: Các subnet ID bao gồm: 

- SubnetID đầu tiên = 0 
- SubnetID kế tiếp = Subnet hiện tại + bước nhảy

B4: Trong SubnetID
- Host đầu: SubnetID +1
- Host cuối: SunetID + Bước nhảy -2
- Địa chỉ Broadcast: Host cuối +1

Ví dụ: 10.1.1.0/24  Chia thành 8 mạng con 

Phân tích: 2^n >=8 => n =3

m= 32-3-24= 5  => Bước nhẩy: 2^5=32

| |Ví dụ 1| Ví dụ 2|Ví dụ 3|
|--- |:-------:|:-------:|:-------:|
|---|101.1.1.0/24|172.16.4.0/22|10.1.8.0/21|
|Số mạng con|8|9|8|
|Số bit mượn n|3|4|3|
|m=32-n-SM hiện tại|5|6|8|
|Bước nhảy 2^5| 32| 64|256|
|Kết quả|101.1.1.0/27 101.1.1.32/27 101.1.1.64/27 101.1.1.96/27 101.1.1.128/27  101.1.1.160/27 101.1.1.192/27 101.1.1.224/27| 172.16.4.0/26 172.16.4.64/26 172.16.4.128/26 172.16.4.192/26 172.16.5.0/26 172.16.5.64/26 172.16.5.128/26 172.16.5.192/26 172.16.6.0/26|10.1.8.0/24 10.1.9.0/24 10.1.10.0/24 10.1.11.0/24 10.1.12.0/24 10.1.13.0/24 10.1.14.0/24 10.1.15.0/24  

##### 3.2. Chia không đều ( VLSM)
B1: Sắp xếp các mạng cần phải chia theo thứ tự giảm dần số host

B2: xác định số bit làm phần host cho mỗi mạng con. Thỏa mãn điều kiện : 

2^n -2 >= số host ( n: số bit cần mượn) Vì phải trừ đi địa chỉ NetID và Broadcast 

B3: Chia 



