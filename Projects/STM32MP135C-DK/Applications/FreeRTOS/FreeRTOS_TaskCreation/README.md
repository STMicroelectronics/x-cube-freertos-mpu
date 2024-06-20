/**
  @page FreeRTOS_ThreadCreation FreeRTOS Thread Creation application
 
  @verbatim
  ******************************************************************************
  * @file    FreeRTOS/FreeRTOS_ThreadCreation/readme.txt
  * @author  MCD Application Team
  * @brief   Description of the FreeRTOS Thread Creation application.
  ******************************************************************************
  * @attention
  *
  * Copyright (c) 2024 STMicroelectronics.
  * All rights reserved.
  *
  * This software is licensed under terms that can be found in the LICENSE file
  * in the root directory of this software component.
  * If no LICENSE file comes with this software, it is provided AS-IS.
  *
  ******************************************************************************
  @endverbatim

@par Application Description

How to implement thread creation using RTOS native API. 

This application creates two threads with the same priority, which execute in 
a periodic cycle of 15 seconds. 

In the first 5 seconds, the thread 1 toggles LED7 each 200 ms and the 
thread 2 toggles LED3 each 500 ms.
In the following 5 seconds, the thread 1 suspends itself and the thread 2
continue toggling LED3.
In the last 5 seconds, the thread 2 resumes execution of thread 1 then 
suspends itself, the thread 1 toggles the LED7 each 500 ms.    

@note Care must be taken when using HAL_Delay(), this function provides accurate
      delay (in milliseconds) based on variable incremented in HAL time base ISR.
      This implies that if HAL_Delay() is called from a peripheral ISR process, then
      the HAL time base interrupt must have higher priority (numerically lower) than
      the peripheral interrupt. Otherwise the caller ISR process will be blocked.
      To change the HAL time base interrupt priority you have to use HAL_NVIC_SetPriority()
      function.
 
@note The application needs to ensure that the HAL time base is always set to 1 millisecond
      to have correct HAL operation.

@note The FreeRTOS heap size configTOTAL_HEAP_SIZE defined in FreeRTOSConfig.h is set accordingly to the 
      OS resources memory requirements of the application with +10% margin and rounded to the upper Kbyte boundary.

For more details about FreeRTOS implementation on STM32Cube, please refer to UM1722 "Developing Applications 
on STM32Cube with RTOS".

@par Keywords

RTOS, FreeRTOS, Threading

@par Directory contents
    - FreeRTOS/FreeRTOS_Semaphore/Src/main.c                         Main program
    - FreeRTOS/FreeRTOS_Semaphore/Src/stm32mp13xx_hal_timebase_tim.c HAL timebase file
    - FreeRTOS/FreeRTOS_Semaphore/Src/stm32mp13xx_it.c               Interrupt handlers
    - FreeRTOS/FreeRTOS_Semaphore/Src/stm32mp13xx_hal_msp.c          MSP Initialization file
    - FreeRTOS/FreeRTOS_Semaphore/Inc/main.h                         Main program header file
    - FreeRTOS/FreeRTOS_Semaphore/Inc/stm32mp13xx_hal_conf.h         HAL Library Configuration file
    - FreeRTOS/FreeRTOS_Semaphore/Inc/stm32mp13xx_it.h               Interrupt handlers header file
    - FreeRTOS/FreeRTOS_Semaphore/Inc/FreeRTOSConfig.h               FreeRTOS Configuration file
    - FreeRTOS/FreeRTOS_Semaphore/Inc/stm32mp13xx_disco_conf.h       BSP configuration file

@par Hardware and Software environment

  - This example runs on STM32MP135xx devices.
  
  - This example has been tested with STMicroelectronics STM32MP135F-DK boards.
    and can be easily tailored to any other supported device and development board.

   
@par How to use it ?

In order to make the program work, you must do the following :

 - Open your preferred toolchain
 - Rebuid and run DDR_Init example to initialize the DDR memory
 - Rebuild all FreeRTOS_TaskCreation application files and load your image into target memory
 - Run the application
  

 */