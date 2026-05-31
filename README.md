# ROV系统设计的介绍
此六推进器小型ROV以STM32F407VET6为主控芯片，采用水面岸基⾼压直流24V供电，  
为了实现摄像头的功能，选择以太网通信方案，通过复合脐带缆将动力与以太网信号输送至水下驱动部分。  
电路板分为四个模块:   
1.电调驱动模块  
2.多级DCDC降压电源模块  
3.主控和外设接口模块，LDO降压电路  
4.微型百兆交换机板，建立通信  
  <img width="120" height="120" alt="df9ab95c752fe5d95a556db47fde8d25_720" src="https://github.com/user-attachments/assets/79116558-786c-41f8-812d-2544eb9bb9a6" />

  
本介绍将从驱动和外设选型，电源设计，电路保护和隔离，以及装配几个部分进行说明，  
需要考虑的余量设计和热量管理则体现在选型，板子设计和装配中。
 <br><br><br>

## 一.  驱动部分

###  1. 推进器
 * 需考虑推力，体积，整体协调性等因素。
 * 选择直流无刷电机。
> **方案：**  6 个 ROVMAKER 24V 水下推进器 正反桨



  <img width="250" height="250" alt="1c96af2e9e1c6dedbf34b07e7f2fcdd1_720" src="https://github.com/user-attachments/assets/8e338260-1bc4-4655-8323-8a36c859c53f" />

  <img width="280" height="250" alt="f84040c7bb4e945844ff14d86c1d2d3b_720" src="https://github.com/user-attachments/assets/f1820e62-1f0a-40a5-aa80-6f9ba28a50ca" />

</div>

###  2. 电子调速器
* 选择独立电调，其相较于内部集成电调，能更稳定持续地输出推力，且成本低。  
* 需考虑输入电压以及尺寸等参数，支持双向。  
* 电调持续电流应根据推进器参数选择，**最好选择持续电流为<1.2 倍推进器峰值电流>的电调**，  
   **又考虑到密封舱内散热受限，则可通过选择更大规格的电调，来降低mos导通热损耗**，且大规格电调在市面上型号更丰富，适配性更好。
> **方案：**  2 个 RuiBet 45A 四合一电调 （余下的两个接口做备用）


  <img src="https://github.com/user-attachments/assets/9a00fff0-6a99-4727-af38-a84e8b1d9a59" width="200" />
<img width="320" height="200" alt="42acd2ad6ac0a1f1876194c1bc5a01f1_720" src="https://github.com/user-attachments/assets/286d5e2b-ba2a-4920-b492-f99b5e91473d" />


  ###  3. 舵机
* 需考虑扭矩，空载速度，体积，防水等因素。
> **方案：**  夹爪 斯普特 SPT5425LV-W 防水舵机 ， 摄像头若添加云台可参考 银燕 EMAX ES08MD II 微型舵机

<img width="350" height="250" alt="0d015c6e706cfab896a912e346b672c6_720" src="https://github.com/user-attachments/assets/c59d7846-82a7-47a0-b6f0-263bff31387a" />
<img width="250" height="250" alt="02439636d6bc7dec981397c0637d4459_720" src="https://github.com/user-attachments/assets/f7e21334-5cbf-4296-883a-4a9b481ba2b4" />
 <br><br><br>

## 二. 外设部分  
### 1. 深度传感器   
  
> **参考：** （端子 MX1.25）


  <img width="260" height="200" alt="96c5af087ffd09066243c27ab55a1dac_720" src="https://github.com/user-attachments/assets/5d13d005-7a79-4af2-aa71-0de550d22f9d" />  
    
### 2. 温湿度传感器    
 

  > **参考：**  
<img width="260" height="250" alt="000d7bb960bbd8fa7192fdee13440d75_720" src="https://github.com/user-attachments/assets/e3a569dd-29d8-4e2f-ac4a-8f524022f4e9" />
<img width="300" height="250" alt="5341b2844a6c0e580578242b02e429b2_720" src="https://github.com/user-attachments/assets/8f9d0fc6-a4a9-4156-84e1-f7f92fa5699b" />  

### 3. 摄像头  
> **参考：**  IMX307 网络摄像头模组 DC12V供电   
<img width="240" height="220" alt="bc92b56fc3557287788037797812d187_720" src="https://github.com/user-attachments/assets/861a218f-03ed-496b-b5bd-0f49adb683c1" />
<img width="220" height="220" alt="daeab980037aac4d4e9659abc597383d_720" src="https://github.com/user-attachments/assets/9c4b4a97-f6f2-406b-bf91-e50c76e9180b" />
<br>  
  
  ### 4. 预留
  
  >  探照灯（供电12V)，姿态陀螺仪等接口，以及串口调试，GPIO接口等
<img width="200" height="200" alt="d96eb445224d210bc213a4def4e1f523" src="https://github.com/user-attachments/assets/02df0760-9463-41e6-9d21-50819d186084" />
<img width="180" height="200" alt="6e7d976220f9b6ba8651b4d6ee719a09_720" src="https://github.com/user-attachments/assets/2994ccb4-0a5e-437f-aa86-aa1432ca1434" />
<img width="240" height="200" alt="3b54dc04182e4079ab0fd0604c82c331_720" src="https://github.com/user-attachments/assets/251ff13b-6d29-4ff1-b064-900c392122fe" />
<img width="220" height="200" alt="5210e7315d6d1ff7aa8be2cdc708c282_720" src="https://github.com/user-attachments/assets/44ef85ac-2344-4cce-b77b-97defd593d93" />


 <br><br><br>  
 ## 三. 电源部分
 
### LDO降压  
#### TPS73733 （+5V转+3V3)  
输入电压:2.2V~5.5V  
输出电压:固定3.3V  
输出电流: 最大1A 
TPS73733的超低压差可以减少自身发热，低静态电流可以减少功耗，且具有反向电流保护等功能  
又由选择SOT-223封装，可以使得芯片在密封舱中温升更小




