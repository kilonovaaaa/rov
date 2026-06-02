# ROV系统设计的介绍
此六推进器小型ROV以STM32F407VET6为主控芯片，采用水面岸基⾼压直流24V供电，  
为了实现摄像头的功能，选择以太网通信方案，通过脐带缆将动力与以太网信号输送至水下密封舱中。  
电路板分为四个模块:   
1.电调驱动模块  
2.多级DCDC降压电源模块  
3.主控和外设接口模块，LDO降压电路  
4.微型百兆交换机板，建立通信（供电5V~12V)  （预留485通讯）
<img width="120" height="120" alt="df9ab95c752fe5d95a556db47fde8d25_720" src="https://github.com/user-attachments/assets/79116558-786c-41f8-812d-2544eb9bb9a6" />

  
本介绍将从驱动和外设选型，电源设计，电路保护和隔离，以及装配几个部分进行说明，  
需要考虑的余量设计和热量管理则体现在选型，板子设计和装配中。
 <br><br><br>

## 一.  驱动部分

###  1. 推进器
 * 需考虑推力、体积、整体协调性等因素。
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
* 需考虑扭矩、空载速度、体积、防水等因素。
> **方案：**  夹爪 NANGU 35KG 潜水舵机（堵转电流2~3A) ， 摄像头若添加云台可参考 银燕 EMAX ES08MD II 微型舵机（堵转电流1A左右）

<img width="220" height="250" alt="1af7928793e2a3ad60a34a430e5b665c_720" src="https://github.com/user-attachments/assets/ae6b0d1a-611a-4802-856a-0085be94acd1" />
<img width="280" height="250" alt="c5d734da20287fc41ad8aad1bb2f76d4_720" src="https://github.com/user-attachments/assets/65ed4d40-ab5d-436c-9b63-f2e80216f096" />
<img width="250" height="250" alt="02439636d6bc7dec981397c0637d4459_720" src="https://github.com/user-attachments/assets/f7e21334-5cbf-4296-883a-4a9b481ba2b4" />
 <br><br><br>

## 二. 外设部分  
### 1. 深度传感器   
  
> **参考：**  实际需要5V供电 （端子 MX1.25）


  <img width="260" height="200" alt="96c5af087ffd09066243c27ab55a1dac_720" src="https://github.com/user-attachments/assets/5d13d005-7a79-4af2-aa71-0de550d22f9d" />  
  
    
### 2. 温湿度传感器    
 

  > **参考：**  （端子 XH2.54)
<img width="260" height="250" alt="000d7bb960bbd8fa7192fdee13440d75_720" src="https://github.com/user-attachments/assets/e3a569dd-29d8-4e2f-ac4a-8f524022f4e9" />
<img width="300" height="250" alt="5341b2844a6c0e580578242b02e429b2_720" src="https://github.com/user-attachments/assets/8f9d0fc6-a4a9-4156-84e1-f7f92fa5699b" />  

### 3. 摄像头  
> **参考：**  IMX307 网络摄像头模组 DC12V供电  （端子 MX1.25） 
<img width="240" height="220" alt="bc92b56fc3557287788037797812d187_720" src="https://github.com/user-attachments/assets/861a218f-03ed-496b-b5bd-0f49adb683c1" />
<img width="220" height="220" alt="daeab980037aac4d4e9659abc597383d_720" src="https://github.com/user-attachments/assets/9c4b4a97-f6f2-406b-bf91-e50c76e9180b" />
<br>  
  
  ### 4. 预留
  
  >  探照灯（供电12V，电源线1平，信号线0.15平)，姿态陀螺仪等接口，以及串口调试，I2C接口等
<img width="200" height="200" alt="d96eb445224d210bc213a4def4e1f523" src="https://github.com/user-attachments/assets/02df0760-9463-41e6-9d21-50819d186084" />
<img width="180" height="200" alt="6e7d976220f9b6ba8651b4d6ee719a09_720" src="https://github.com/user-attachments/assets/2994ccb4-0a5e-437f-aa86-aa1432ca1434" />
<img width="240" height="200" alt="3b54dc04182e4079ab0fd0604c82c331_720" src="https://github.com/user-attachments/assets/251ff13b-6d29-4ff1-b064-900c392122fe" />
<img width="220" height="200" alt="5210e7315d6d1ff7aa8be2cdc708c282_720" src="https://github.com/user-attachments/assets/44ef85ac-2344-4cce-b77b-97defd593d93" />


 <br><br><br>  
 ## 三. 电源部分  
 考虑上述驱动和外设部分的选型，并预留后续外设可能消耗的功率，又由于脐带缆存在线损，  
 选择 **明纬RSP-1600-24**（1600W，输出电压可调：23.5V~30V）岸基高压供电。
 
 ### DCDC降压  
#### 芯洲科技SCT2650 (+24V转+12V)
输入电压: 4.5V~60V  
输出电压: 12V  
输出电流: 最大5A  
**输出电流满足后续负载要求，且留有余量**；60V宽电压输入，一定程度上耐受电调带来的电压尖峰，保护后级电路；  
异步整流，抵御高压浪涌，防止直通短路。  
#### 芯洲科技SCT2450 (+12V转+6V)   
输入电压：3.8V~36V  
输出电压：6V  
输出电流：最大5A  
**输出电流满足后续负载要求，且留有余量**；**同步整流，相对减少发热**；宽电压输入。  
#### 金升阳 URB2412YMD 10WR3 隔离电源 (+24V转+12V)  
输入电压：9V-36V  
输出电压： 12V  
输出电流: 833mA  
**输出电流满足后续负载要求，且留有余量**；具有欠压保护，过流保护等功能；宽电压输入。
#### 芯洲科技SCT2430 (+12V转+5V)  
输入电压：3.8V~36V  
输出电压：5V  
输出电流：最大3.5A  
**输出电流满足后续负载要求，且留有余量**；**同步整流，相对减少发热**；宽电压输入。  
### LDO降压  
#### TPS73733 (+5V转+3V3)  
输入电压: 2.2V~5.5V  
输出电压: 固定3.3V  
输出电流: 最大1A  
**输出电流满足后续负载要求，且留有余量**；**超低压差可以减少自身发热**，低静态电流可以减少功耗；  
**又由选择SOT-223封装，可以使得芯片在密封舱中温升更小**。
* 供电部分分为功率部分和信号部分,两部分在隔离电源处用0欧电阻单点相连  
功率部分：SCT2650-SCT2450，给探照灯，舵机等大功率负载供电。  
信号部分：隔离DCDC-SCT2430-LDO，给摄像头，传感器，通讯模块，以及主控供电。
* 所选择的SCT系列具有欠压锁定（选择用）、过温保护等功能，且**底部均设计了散热焊盘**，可以有效保护芯片，  
又芯片手册介绍详细，有利于选型，进而实现芯片性能，且SCT系列成本相对较低。
<br><br><br>
## 四. 电路保护和隔离  
### 保护  
1. 在主控，舵机电源输入处放置合适参数的自恢复保险丝，保护主控及系统。
2. 在24V和5V输入处，都设计了相关的保护电路。
3. 485隔离通讯接口处，设计了专用的差模浪涌防护。

  ### 隔离  
  #### 电源隔离  
  1.隔离电源的采用，地的分割，用0欧电阻相连  
  2.SCT数字地模拟地的分离，在芯片引脚处进行单点相连
  #### 信号隔离  
  1.选取隔离型485芯片，  
  2.微型百兆交换机中的网络变压器，  
  <br><br><br>  
  ## 五. 装配  
  

       





