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
  ![WhatsApp Image 2025-11-08 at 09 16 45_21b2dbfc](https://github.com/user-attachments/assets/279bd9bd-ba77-4bc3-a443-8555f02ad6c8)


2. Click **File → New STM32 Project**.
  ![WhatsApp Image 2025-11-08 at 09 17 27_4988239b](https://github.com/user-attachments/assets/3382610a-fdf7-41fb-a02c-e03dbec71ca8)
![WhatsApp Image 2025-11-08 at 09 22 58_4b54eace](https://github.com/user-attachments/assets/b318be6b-4294-417e-b741-19872e68cc81)


3. Select the **target microcontroller** or board and click **Next**.
  ![WhatsApp Image 2025-11-08 at 20 23 19_73577344](https://github.com/user-attachments/assets/a699ee50-4999-4924-b5bd-11d6cf5437c2)


4. Name the project.

![WhatsApp Image 2025-11-08 at 20 24 26_b19b5120](https://github.com/user-attachments/assets/869ebc61-0f0a-481b-9183-ce4cf5ca5b65)

5. The corresponding `.ioc` file will be generated automatically.
 <img width="1919" height="1198" alt="image" src="https://github.com/user-attachments/assets/d059be5b-d153-4504-8a11-d330a0b21ef4" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  ![WhatsApp Image 2025-11-08 at 20 31 08_1b8fb7b8](https://github.com/user-attachments/assets/e67ca35a-da02-42d9-94b9-824d2fbb152c)

![WhatsApp Image 2025-11-08 at 20 32 03_f63f026c](https://github.com/user-attachments/assets/7862a871-1420-4268-86d3-ac53125686de)


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   
 <img width="1919" height="1113" alt="image" src="https://github.com/user-attachments/assets/d3b1bd03-8785-4aa0-a5f0-2e080b85e2b0" />

8. Edit the generated main program as required.
  <img width="1919" height="1149" alt="image" src="https://github.com/user-attachments/assets/966dbbf8-a8eb-40a2-ba64-c1ca411116db" />

<img width="1919" height="1110" alt="image" src="https://github.com/user-attachments/assets/f4062c98-59c4-4487-87dc-fdc4eafa0768" />

9. Click **Project → Build All**.
    <img width="1914" height="1106" alt="image" src="https://github.com/user-attachments/assets/11aeae78-41b5-415f-9f58-5607798a38d9" />


10. Link the **HEX file** using the post-build process.
    <img width="1919" height="1090" alt="image" src="https://github.com/user-attachments/assets/cbb53cf2-0aa6-4daf-8b91-a2a49db172ed" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1919" height="1141" alt="image" src="https://github.com/user-attachments/assets/b4edec7a-92a5-4171-9e40-50c8758f47c5" />


13. Click **Run** to execute the program.
    
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

![WhatsApp Image 2025-10-28 at 07 28 14_4189c939](https://github.com/user-attachments/assets/ae274fb7-f911-4c8d-b170-12680d40fe06)


CASE 2: LED OFF
![WhatsApp Image 2025-10-28 at 07 28 13_884e9cda](https://github.com/user-attachments/assets/2b707ede-f1c9-40d9-9e5e-b3512639d61c)


---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
