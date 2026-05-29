# ROV系统设计的介绍
 此六推进器小型ROV以STM32F407VET6为主控芯片  
驱动部分：直流无刷电机+电子调速器  舵机  
外设部分：预留外设接口  
电源部分：水面岸基高压直流24V供电，两路DCDC降压电路，LDO降压电路  
保护部分：防反接，防短路，防浪涌，防过压设计  
隔离部分：电源，信号隔离
装配部分：全部板件及所需模块放在舱内并进行固定  
需考虑的 **余量设计** 和 **热量管理** ，体现在选型和装配中
 <br><br>

## 一.  驱动部分

###  推进器
 * 需考虑推力，体积，整体协调性等因素。
> **方案：** 参考 6 个 ROVMAKER 24V 水下推进器 正反桨



  <img width="250" height="250" alt="1c96af2e9e1c6dedbf34b07e7f2fcdd1_720" src="https://github.com/user-attachments/assets/8e338260-1bc4-4655-8323-8a36c859c53f" />

  <img width="280" height="250" alt="f84040c7bb4e945844ff14d86c1d2d3b_720" src="https://github.com/user-attachments/assets/f1820e62-1f0a-40a5-aa80-6f9ba28a50ca" />

</div>

###  电子调速器
* 选择独立电调，其相较于内部集成电调，能更稳定持续地输出推力，且成本低。  
* 需考虑输入电压以及尺寸等参数，支持双向。  
* 电调持续电流应根据推进器参数选择，**最好选择持续电流为<1.2 倍推进器峰值电流>的电调**，  
   **又考虑到密封舱内散热受限，则可通过选择更大规格的电调，来降低mos导通热损耗**，且大规格电调在市面上型号更丰富，适配性更好。
> **方案：** 参考 2 个 RuiBet 45A 四合一电调 （余下的两个接口做备用）


  <img src="https://github.com/user-attachments/assets/9a00fff0-6a99-4727-af38-a84e8b1d9a59" width="250" />
</div>

  ###  舵机
* 需考虑扭矩，空载速度，体积，防水等因素。
> **方案：** 参考 斯普特 SPT5425LV-W 防水舵机，摄像头若需要可参考 银燕 EMAX ES08MD II 微型舵机
<img width="250" height="250" alt="38eb3d88d30f48b4222fc036e32bfbdc_720" src="https://github.com/user-attachments/assets/92ac3b77-3532-4b8f-80c6-175fa7b76395" />
<img width="350" height="250" alt="0d015c6e706cfab896a912e346b672c6_720" src="https://github.com/user-attachments/assets/c59d7846-82a7-47a0-b6f0-263bff31387a" />
<img width="250" height="250" alt="02439636d6bc7dec981397c0637d4459_720" src="https://github.com/user-attachments/assets/f7e21334-5cbf-4296-883a-4a9b481ba2b4" />
 <br><br>

## 二. 外设部分  
### 深度传感器   
（供电 1.5~3.6V）


  <img width="300" height="250" alt="96c5af087ffd09066243c27ab55a1dac_720" src="https://github.com/user-attachments/assets/5d13d005-7a79-4af2-aa71-0de550d22f9d" />  
    
### 温湿度传感器  
* 固定：
<img width="260" height="250" alt="000d7bb960bbd8fa7192fdee13440d75_720" src="https://github.com/user-attachments/assets/e3a569dd-29d8-4e2f-ac4a-8f524022f4e9" />
<img width="300" height="250" alt="5341b2844a6c0e580578242b02e429b2_720" src="https://github.com/user-attachments/assets/8f9d0fc6-a4a9-4156-84e1-f7f92fa5699b" />  

### 摄像头  
（供电12V）  


预留探照灯，姿态陀螺仪，串口调试等接口





