CÁC BƯỚC THỰC HIỆN:
1. Cấu hình Clock:
   - Bật clock cho GPIO, ADC1, USART1 và DMA1
  
  <img width="1204" height="105" alt="image" src="https://github.com/user-attachments/assets/2e5782c9-21fd-451b-b17f-79ad6d8faf02" />

2. Cấu hình GPIO:
   - PA0: Analog input
   - PA9: USART1_TX
   - PA10: USART1_RX
  
<img width="619" height="341" alt="image" src="https://github.com/user-attachments/assets/6e004a02-45be-4941-8e68-71cd3b6822a9" />

3. Cấu hình USART:
   - Baudrate: 9600
   - Word length: 8 bit
   - Stop bit: 1
   - Parity: None
   - Mode: Tx

  <img width="738" height="233" alt="image" src="https://github.com/user-attachments/assets/f97576d6-a50a-4b7c-bcbb-7b2c97e0ce03" />

4. Cấu hình ADC1:
   - Hoạt động độc lập
   - Đọc kênh đơn (Channel 0 - PA0)
   - Chế độ liên tục
   - Kết quả canh phải
   - Cho phép DMA

   <img width="890" height="418" alt="image" src="https://github.com/user-attachments/assets/fdf1c26b-76a2-472c-b638-8534df7f636c" />

5. Cấu hình DMA:
   - Địa chỉ ngoại vi: &ADC1->DR
   - Địa chỉ bộ nhớ: adc_buffer[]
   - Kích thước dữ liệu: 16 bit
   - Chế độ: Circular
   - Cho phép ngắt khi truyền xong

     <img width="686" height="421" alt="image" src="https://github.com/user-attachments/assets/89b89105-9a29-4389-bb00-d4386229b08b" />

6.  Hàm ngắt DMA:
   
   <img width="572" height="123" alt="image" src="https://github.com/user-attachments/assets/bb1f53e9-e857-4fe6-a2db-a21cf46a38fb" />

7. Tạo delay:

   <img width="540" height="127" alt="image" src="https://github.com/user-attachments/assets/c7943309-09cb-40f2-b920-df9640f6094f" />

8. Hàm gửi dữ liệu qua USART:
   - Gửi toàn bộ buffer ADC ra UART1

   <img width="729" height="213" alt="image" src="https://github.com/user-attachments/assets/eb4625d9-4eeb-44a0-a5a7-e75b2a3ba950" />


9. Hàm main:
   

<img width="731" height="318" alt="image" src="https://github.com/user-attachments/assets/ffe5142e-9006-4cbc-b57d-e002c60b119b" />

10. Kết quả:
    - STM32 đọc giá trị ADC (PA0).
    - DMA ghi liên tục vào adc_buffer[16].
    - Mỗi 1 giây STM32 gửi toàn bộ buffer qua UART1 


