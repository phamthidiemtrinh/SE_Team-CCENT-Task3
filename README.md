**Địa chỉ IP:** là một loại địa chỉ logic thuộc lớp network trong mô hình OSI , là một loại địa chỉ thông dụng được sử dụng bởi giao thức IP trong chồng giao thức TCP//IP thuộc lớp Internet
- Linh hoạt
- Tiện dụng
- Gọn nhẹ

## 1. Một số phép tính toán thao tác với địa chỉ IP
- chuyển đổi hệ thập phân (Decimal) sang nhị phân (binary)  và ngược lại
- các giá trị lũy thùa 2: 2,4,8,16,32,64,128,256,512,1024,2048,4096...65536 (2^16)
- khi cho n bit nhị phận thì có thể tạo ra 2^n số nhị phân n-bit (khi đổi sang hập phân thì chạy từ 0 đến (2^n)-1)
- các giá trị cần nhớ
`````
                 Nhị phân             |             Thập phân
  ________________________________________________________________________
                 00000000             |                 0
  ________________________________________________________________________
                 10000000             |                128
  ________________________________________________________________________
                 11000000             |                192
  ________________________________________________________________________
                 11100000             |                224
  ________________________________________________________________________
                 11110000             |                240  
  ________________________________________________________________________
                 11111000             |                248
  ________________________________________________________________________
                 11111100             |                252       
  _______________________________________________________________________
                 11111110             |                254
  _______________________________________________________________________
                 11111111             |                255
                 
 ```````````````````````````
 - bảng bước nhảy : gọi n là số bit mượn. Bước nhảy được tính theo công thức 2^(8-n)
 
 ````````````````````````````
 số bit mượn      |    1    |    2    |    3    |    4   |    5    |     6    |    7    |    8   |
__________________________________________________________________________________________________
   Bước nhảy      |   128   |   64    |   32    |    16  |    8    |     4    |    2    |    1    |
   
 ````````````````````````
 
 
 ## 2. IP header
 
![](http://www.yaldex.com/tcp_ip/FILES/04fig03.gif) 
 - trong đó
  - IHl (ip header length): độ dài header
  - service type : bảo đảm chất lượng dịch vụ
  - Identification  , flag , flag offset : phân mảnh gói tin khi gói tin quá lớn
  - Time to live : tránh hiện tượng chạy vòng trong việc định tuyến sai lầm
  - protocol : phần dữ liệu thuộc giao thức nào
  - header checksum : tổng kiểm tra lỗi cho cả gói dữ liệu
  
  ## 3. cấu trúc địa chỉ IP
  - gồm tổng cộng 32 bit, được chia thành 2 phần là mạng (network) và host
  - được viết thành từng cụm 8 bit được gọi là octet
  - mỗi octet được đổi thành số thập phân và ngăn cách nhau bởi dấu chấm
  - lứu ý :
    - các bit phần network không được phép đồng thời bằng không
    - nếu tất cả bit phần host bằng không thì ta có địa chỉ mạng
    - nếu tất cả bit phần host bằng một thì ta có địa chỉ quảng bá ( broadcast ) : đại diện cho tất cả các host có trong mạng
    
  ## 4. các lớp địa chỉ IP

![](https://lh4.ggpht.com/-Lj5iAsyu1Us/V2yB1Dq-nlI/AAAAAAAABP8/NjVY_TeAMCAV46ucVwJ1kGKl8KuQZDshQCLcB/s1600/ipclass.png) 
  
  - trong lớp A : 1 octet đầu là network. quy ước bit đàu tiên địa chỉ lớp A được đưa về 0, phần mạng ược định danh bằng 7bit tiếp theo 
    - địa chỉ mạng sử dụng địa được: 126, chạy từ 1.0.0.0 đến 127.0.0.0
    - số host: 2^14 
    - mạng 127.0.0.0 : loopback network
  - trong lớp B : 2 octet đầu là network, quy ước 2bit đầu tiên trong đạ chỉ lớp B là 1 và 0
    - có 2^14 địa chỉ mạng chạy từ 128.0.0.0 đến 191.255.0.0
    - có 2^16-2 host
  - trong lớp C : 3 octet đầu là network, quy ước 3 bit dầu là 110
    - chạy từ 192.0.0.0 đến 223.255.255.0 có 2^21 mạng
    - 254 host
   - địa chỉ lớp D : 224.0.0.0 đến 239.255.255.255 là địa chỉ multicast (giao thức định tuyến trong công nghệ multicast) dùng để đặt cho từng nhơm thiết bị
   - địa chỉ lớp E: từ 240.0.0.0 trở đi : là lớp dự phòng
   
  ## 5. các loại địa chỉ IP
   - địa chỉ quảng bá
    -  direct : có phần host được quy ước các bit đồng thời bằng 1 : gửi broadcast cho các host ngoại mạng
    -  local : 32 bit nhị phân đồng thời =1 : 255.255.255.255 : khi host muốn gửi broadcast đến tất cả các jost trong cùng mạng
  - Địa chỉ IP private: sử dụng trong mạng LAN , có thể được sử dụng nhiều lần trong các mạng LAN khác nhau, được tự quyền cấp phát
    - lớp A : 10.x.x.x
    - lớp B : 172.16.x.x -> 172.31.x.x
    - lớp C : 192.168.x.x
    - bảo tồn địa chỉ IP public
  - Địa chỉ IP public : là dịa chỉ được dử dụngt trên môi tường internet toàn cầu có tính chất toàn cầu
  
 ## 6. Subnet mask và prefix
 - là dãy nhị phân đài 32bit dùng kèm với địa chỉ IP
 - khi máy xác định địa chỉ mạng thì nó lấy kết quả của phép toán (IP and subnet mask) dưới dạng nhị phân
 - nếu không khai báo subnet mask kèm theo địa chỉ IP thì địa chỉ IP đó được xem là không hợp lệ
 - sử dụng prefix-length để làm ngắn lại cách ghi cả hai địa chỉ : A.B.C.D/n ( trong đó n là só bit mạng)
 
    

