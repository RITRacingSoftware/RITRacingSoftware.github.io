# MCU

**The Microcontroller Unit** (MCU) is the core of our embedded system, managing sensors, actuators, and communication. For the racecar, the MCU handles real-time control and data processing under challenging automotive conditions.

---

## STM32G473RET6

We use the STM32G473RET6 from STMicroelectronics — a powerful ARM Cortex-M4 MCU with floating-point support, ideal for control and signal processing tasks.

Some documentation on this MCU:

* [Datasheet](https://www.st.com/resource/en/datasheet/stm32g473cb.pdf)

* [Reference Manual for STM32G4 series MCUs](https://www.st.com/resource/en/reference_manual/rm0440-stm32g4-series-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

* [Link to part on DigiKey](https://www.digikey.com/en/products/detail/stmicroelectronics/STM32G473RET6/10326721)

## HAL

The **Hardware Abstraction Layer** (HAL) is a software library provided by STMicroelectronics for STM32 microcontrollers. It offers a high-level, standardized interface to the MCU’s hardware peripherals—such as timers, ADCs, communication interfaces (SPI, I2C, UART), and GPIO—abstracting away the low-level register manipulations.

The team's firmware extensively uses the custom Core library, which is largely built on the HAL.

HAL Documentation:

* [HAL Documentation for STM32G4 series MCUs](https://www.st.com/resource/en/user_manual/um2570-description-of-stm32g4-hal-and-lowlayer-drivers--stmicroelectronics.pdf)