# Lab 07 Seven segment Component develope.

## 1. เพิ่ม functions ในคลาส sevent segment

จากใบงานที่ 6 ให้เพิ่ม  functions ในคลาส SevenSegment ดังต่อไปนี้

```mermaid
classDiagram
class SevenSegment {
    common_pin : int 

+ SevenSegment(int pin)
+ DisplayBlank() void 
+ DisplayNumber(number : int)
+ DisplayNum0()  void
+ DisplayNum1()  void
+ DisplayNum2()  void
+ DisplayNum3()  void
+ DisplayNum4()  void
+ DisplayNum5()  void
+ DisplayNum6()  void
+ DisplayNum7()  void
+ DisplayNum8()  void
+ DisplayNum9()  void
}
```
แต่ละ function มีหน้าที่ต่อไปนี้

|Function|Description|
|--------|-----------|
|SevenSegment(int pin)| Constructor ทำหน้าที่รับหลายเลข pin เข้ามาตอนสร้าง object และกำหนดทิศทางเป็น output|
| void DisplayNumber(number : int) | แสดงตัวเลขที่ป้อนทางพารามิเตอร์บน seven segment | 
| void DisplayNum0()   | แสดงเลข 0 บน seven segment |  
| void DisplayNum1()   | แสดงเลข 1 บน seven segment|
| void DisplayNum2()   | แสดงเลข 2 บน seven segment |
| void DisplayNum3()   | แสดงเลข 3 บน seven segment |
| void DisplayNum4()   | แสดงเลข 4 บน seven segment |
| void DisplayNum5()   | แสดงเลข 5 บน seven segment |
| void DisplayNum6()   | แสดงเลข 6 บน seven segment |
| void DisplayNum7()   | แสดงเลข 7 บน seven segment |
| void DisplayNum8()   | แสดงเลข 8 บน seven segment | 
| void DisplayNum9()   | แสดงเลข 9 บน seven segment |

### 1.1 แก้ไขไฟล์  sevensegment.h

![alt text](image.png)

### 1.2 แก้ไขไฟล์  sevensegment.cpp ดังต่อไปนี้

#### 1.2.1  ฟังก์ชัน `HardwareTest()`

![alt text](image-1.png)

#### 1.2.2  ฟังก์ชัน `DisplayBlank()`

![alt text](image-2.png)

#### 1.2.3  เพิ่มฟังก์ชัน `DisplayNumber(int number)`
![alt text](image-3.png)

#### 1.2.4  เพิ่มฟังก์ชัน `DisplayNum0()`
![alt text](image-4.png)

#### 1.2.5  เพิ่มฟังก์ชัน `DisplayNum1()` ถึง `DisplayNum9()` 
ใช้ตารางนี้ [(ตารางความจริง seven segment)](https://github.com/Special-Topic-2567/ESP32-Lab06-LED-7Segment-Component?tab=readme-ov-file#%E0%B8%95%E0%B8%B2%E0%B8%A3%E0%B8%B2%E0%B8%87%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B8%88%E0%B8%A3%E0%B8%B4%E0%B8%87%E0%B8%AA%E0%B8%B3%E0%B8%AB%E0%B8%A3%E0%B8%B1%E0%B8%9A%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%AA%E0%B8%94%E0%B8%87%E0%B8%9C%E0%B8%A5%E0%B8%95%E0%B8%B1%E0%B8%A7%E0%B9%80%E0%B8%A5%E0%B8%82-7-%E0%B8%AA%E0%B9%88%E0%B8%A7%E0%B8%99) ในการเพิ่มฟังก์ชันแสดงเลข 1 ถึง 9 (ถ้ามีที่ผิด แก้ให้สามารถแสดงผลได้ถูกต้องด้วย)

ตัวอย่าง code แสดงเลข 1
![alt text](image-5.png)


ตัวอย่าง code แสดงเลข 9
![alt text](image-6.png)

จาก code สำหรับแสดงผลเลข 0 ถึง 9 นั้น เพื่อไม่ให้ LED ของ segment กระพริบและนำไปสู่การแสดงผลแบบแปลก ๆ ในขณะที่กำลัง ปิดและเปิดแต่ละ segment เราต้องปิดการแสดงผลด้วยคำสั่ง `common.OFF();` เมื่อเปลี่ยนแปลงแต่ละ segment ครบแล้ว ให้เปิด seven segment ด้วยคำสั่ง `common.ON();`

#### 1.2.6  แก้ไขไฟล์ main.cpp เพื่อทดสอบการทำงานของ seven segment

```cpp
#include <stdio.h>
#include "SevenSegment.h"

SevenSegment s1(0) ;
SevenSegment s2(4) ;

extern "C" void app_main(void)
{
    while(1)
    {
        s1.DisplayNum0();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayNum1();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayNum2();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayNum3();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayNum4();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayNum5();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayNum6();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayNum7();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayNum8();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayNum9();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s1.DisplayBlank();

        s2.DisplayNum0();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayNum1();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayNum2();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayNum3();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayNum4();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayNum5();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayNum6();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayNum7();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayNum8();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayNum9();
        vTaskDelay(500/portTICK_PERIOD_MS);
        s2.DisplayBlank();
    } 
}
```

build, flash และ run โปรแกรม 

บันทึกวิดิโอของ LED seven segment และแนบ link วิดีโอในไฟล์นี้

ผลลัพน์ คือ LED seven segment ติดทั้งสองอัน และติดเป็นตัวเลข 0-9 ทั้งสองอัน


รูปภาพ

![image](https://github.com/user-attachments/assets/9ebc7d9d-6d9c-4b39-bf69-df13f256a2c4)
![image](https://github.com/user-attachments/assets/d0cbfc8f-59ec-4d02-bae4-f768a77c2f7b)

![image](https://github.com/user-attachments/assets/2f047bed-f046-4433-b3d2-a05d6bb2d1fd)

![image](https://github.com/user-attachments/assets/47d395f9-1d5f-4fb2-9ff7-308a2295ae8d)
![image](https://github.com/user-attachments/assets/6d28c523-1e63-416d-998e-367f34e7bf17)
![image](https://github.com/user-attachments/assets/e35ffb5a-ccf9-4708-aedf-95fa1d3b76c9)

![image](https://github.com/user-attachments/assets/2a0a91e0-17e9-4f9b-993c-53c8cab2849e)

![image](https://github.com/user-attachments/assets/4203407b-6eb9-4590-badc-9c081e937d02)


วิดิโอ

https://vt.tiktok.com/ZS2FCjy4j/

![image](https://github.com/user-attachments/assets/0e26ad78-5c3b-4b54-9ee1-f554dafbb44e)


ลิงค์งาน GIT HUB

https://github.com/AnchisaPhetnoi/Lab-07-Seven-segment-Component-develope.git

![image](https://github.com/user-attachments/assets/05d86934-0f7c-43bd-be59-d6970d60ce46)








