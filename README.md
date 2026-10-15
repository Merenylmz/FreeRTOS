# FreeRTOS

🌍 **Dil / Language:** [Türkçe](#-proje-amacı) | [English](#-project-purpose)

---

## 🎯 Proje Amacı
Bu proje, STM32 mikrodenetleyici mimarisi üzerinde FreeRTOS (Gerçek Zamanlı İşletim Sistemi) çekirdeği ve STM32 HAL (Hardware Abstraction Layer) kütüphaneleri kullanılarak geliştirilmiş gömülü yazılım pratiklerini içermektedir. Projenin temel amacı, kısıtlı donanım kaynaklarına sahip gömülü sistemlerde çoklu görev (multitasking), görev önceliklendirme ve zamanlama mekanizmalarını somut donanım birimleri üzerinde gerçek zamanlı olarak çalıştırmaktır.

Depo içerisinde, GPIO tabanlı donanım kontrol mekanizmalarını (buton okuma ve LED anahtarlama) ve seri haberleşme protokollerini (UART üzerinden veri iletimi) FreeRTOS görevleri (tasks) ile asenkron ve kararlı bir biçimde yöneten modüler alt projeler yer almaktadır.

## 🛠️ Kullanılan Teknolojiler
* **C / Gömülü C (Embedded C)**
* **FreeRTOS** (Real-Time Operating System Kernel)
* **STM32 HAL** (Hardware Abstraction Layer)
* **ARM Cortex-M** Mikrodenetleyici Mimarisi
* **STM32CubeIDE / Keil MDK** (Geliştirme Ortamı)

## 🚀 Kurulum ve Çalıştırma

Projeyi yerel ortamınıza klonlamak ve hedef kart üzerinde çalıştırmak için aşağıdaki adımları takip edin:

```bash
# 1. Depoyu yerel makinenize klonlayın
git clone https://github.com/Merenylmz/FreeRTOS.git

# 2. Proje dizinine geçiş yapın
cd FreeRTOS
```

### Derleme ve Yükleme:
1. **STM32CubeIDE** veya tercih ettiğiniz IDE'yi açın.
2. `File` > `Import` > `Existing Projects into Workspace` adımlarını izleyerek çalıştırmak istediğiniz alt projeyi (`HAL_FreeRTOS_Button_LED_Control` veya `HAL_UART_SendingMessage_WithFreeRTOS`) içe aktarın.
3. Hedef STM32 geliştirme kartınızı (ör. Nucleo, Discovery) ST-Link / J-Link aracılığıyla bilgisayarınıza bağlayın.
4. Projeyi derleyin (`Build Project` - `Ctrl+B`).
5. Kodu hedef mikrodenetleyiciye yükleyin (`Run` / `Debug` - `F11`).

## 📌 Ek Bilgiler ve Özellikler
* **HAL_FreeRTOS_Button_LED_Control:** Buton girdilerini kesme (interrupt) veya tarama (polling) yöntemiyle algılayıp, görevler arası bildirim veya durum kontrolü ile LED durumlarını deterministik biçimde yöneten RTOS görev yapısını içerir.
* **HAL_UART_SendingMessage_WithFreeRTOS:** UART çevre birimi üzerinden mesaj gönderimini engellemeyen (non-blocking) bir FreeRTOS görevi altında yürüterek diğer sistem görevlerinin kesintiye uğramadan çalışmasını sağlar.
* **Modüler Mimari:** Her alt proje, kendi FreeRTOS konfigürasyonunu (`FreeRTOSConfig.h`) ve HAL başlatma kodlarını barındıran bağımsız bir yapıya sahiptir.

---

# FreeRTOS (English)

## 🎯 Project Purpose
This repository contains embedded software implementations based on the FreeRTOS (Real-Time Operating System) kernel and STM32 HAL (Hardware Abstraction Layer) on STM32 microcontrollers. The main goal of this project is to demonstrate real-time multitasking, task scheduling, and resource management on resource-constrained embedded hardware using deterministic task architectures.

The repository includes modular sub-projects focusing on GPIO hardware management (button inputs and LED toggling) and serial communication protocols (transmitting data via UART) asynchronously and reliably through FreeRTOS tasks.

## 🛠️ Technologies Used
* **C / Embedded C**
* **FreeRTOS** (Real-Time Operating System Kernel)
* **STM32 HAL** (Hardware Abstraction Layer)
* **ARM Cortex-M** Microcontroller Architecture
* **STM32CubeIDE / Keil MDK** (Development Toolchains)

## 🚀 Installation and Usage

Follow the steps below to clone the repository and deploy the firmware to your target hardware:

```bash
# 1. Clone the repository
git clone https://github.com/Merenylmz/FreeRTOS.git

# 2. Navigate to the project directory
cd FreeRTOS
```

### Build & Flash:
1. Open **STM32CubeIDE** or your preferred ARM IDE.
2. Select `File` > `Import` > `Existing Projects into Workspace` and choose the relevant sub-directory (`HAL_FreeRTOS_Button_LED_Control` or `HAL_UART_SendingMessage_WithFreeRTOS`).
3. Connect your STM32 development board (e.g., Nucleo, Discovery) to your workstation via ST-Link / J-Link debugger.
4. Build the project (`Build Project` - `Ctrl+B`).
5. Flash the binary to the microcontroller (`Run` / `Debug` - `F11`).

## 📌 Additional Information & Features
* **HAL_FreeRTOS_Button_LED_Control:** Demonstrates deterministic GPIO handling where button input state changes trigger LED toggles via isolated RTOS tasks without blocking the processor.
* **HAL_UART_SendingMessage_WithFreeRTOS:** Implements serial communication under a dedicated FreeRTOS task, ensuring non-blocking message transmission over UART.
* **Modular Codebase:** Each directory operates as a standalone project with dedicated hardware configurations and `FreeRTOSConfig.h` settings.