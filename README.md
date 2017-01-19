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
  
 

