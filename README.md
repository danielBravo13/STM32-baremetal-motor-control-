# STM32 Bare-Metal Motor Control
A Bare-metal STM32F401RE dual DC motor controller using TIM2 PWM generation and L298N driver with independent speed and direction control.

## Features
- Bare-metal STM32 development (no HAL)
- TIM2 PWM generation
- Independent motor speed control
- Independent motor direction control
- Dual motor supply
- Register-level peripheral configuration
- Oscilloscope-verified PWM output
- Modular GPIO and timer initialization

## Hardware

### Microcontroller
- STM32 NUCLEO-F401RE (ARM Cortex M4)

### Motor Driver
- L298N Dual H-Bridge Driver

### Test Equipment
- Oscilloscope
- Laboratory DC Power Supply
- Digital Multimeter

## PWM Generation
-TIM2 is configured to generate a 1 kHz PWM signal used to control motor speed.
```c
	TIM2->PSC = (SystemCoreClock / 1000000U) - 1U;
	TIM2->ARR = 1000-1;

	TIM2->CCR1 = 500;
	TIM2->CCR2 = 500;
```

## PWM Verification
Measured:
- Frequency: 1 kHz
- Period: 1ms
- Duty Cycle: 50%
