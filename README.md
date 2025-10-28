# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.

<img width="1920" height="1200" alt="Screenshot (46)" src="https://github.com/user-attachments/assets/359383db-703c-47d5-88dd-c14bf575224f" />


2. Click **File → New STM32 Project**.
  <img width="1920" height="1200" alt="Screenshot (56)" src="https://github.com/user-attachments/assets/fb3f67a9-ac6c-4475-830a-10253d4a3a85" />


3. Select the **target microcontroller** or board and click **Next**.
  <img width="1920" height="1200" alt="Screenshot (48)" src="https://github.com/user-attachments/assets/70cc359e-6ec8-47ed-870f-922ae30f1ab6" />




4. Name the project.

   <img width="533" height="588" alt="image" src="https://github.com/user-attachments/assets/63de2bab-69d4-4cb9-8db6-1b57adff9878" />

5. The corresponding `.ioc` file will be generated automatically.
 
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/7478d1b9-3d23-4cc2-b9d1-cf16632e57e6" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
 <img width="1920" height="1200" alt="Screenshot (50)" src="https://github.com/user-attachments/assets/8cf20008-c767-4137-8501-2f3a84e39e4e" />
<img width="1920" height="1200" alt="Screenshot (51)" src="https://github.com/user-attachments/assets/81918a2e-11f4-4384-ba26-86be2a30d8cc" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1920" height="1200" alt="Screenshot (52)" src="https://github.com/user-attachments/assets/167ed638-d826-417f-837d-6090435215f0" />

 
8. Edit the generated main program as required.
   <img width="1920" height="1200" alt="Screenshot (53)" src="https://github.com/user-attachments/assets/3ff4d86c-c9c4-48ae-9ad4-608dce4edb38" />
   <img width="1920" height="1200" alt="Screenshot (47)" src="https://github.com/user-attachments/assets/6fd02a06-3615-4cda-941b-ce42f364594a" />



9. Click **Project → Build All**.
    <img width="1920" height="1200" alt="Screenshot (54)" src="https://github.com/user-attachments/assets/1d46b91c-19a3-4e1f-ad0f-040cff37ce72" />


10. Link the **HEX file** using the post-build process.
    <img width="946" height="253" alt="Screenshot 2025-10-28 191858" src="https://github.com/user-attachments/assets/166d40e6-437c-408e-b62e-6a75e2a029bf" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1920" height="1200" alt="Screenshot (54)" src="https://github.com/user-attachments/assets/89d72e13-eb39-4ecd-8c12-7cc276eea4d8" />


12. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

![WhatsApp Image 2025-10-28 at 21 36 56_4d0b9340](https://github.com/user-attachments/assets/62fe7df4-1161-496a-ad41-ba64dfb62b9b)


CASE 2: LED OFF

![WhatsApp Image 2025-10-28 at 21 36 56_e63f908b](https://github.com/user-attachments/assets/03b0fdb4-3559-436a-be54-4e1d465aa0dd)


---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
