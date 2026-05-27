# 六推进器小型ROV系统设计的介绍
## 一.  选型

### 1. 推进器
* 需考虑推力，体积，整体协调性等因素。
* 比如选择 6 个 ROVMAKER 24V 水下推进器 （3个正桨，3个反桨）


  <img src="https://github.com/user-attachments/assets/38057388-4e0a-4360-a512-9ab2fa242a75" width="300" />
  <img width="300" height="300" alt="f84040c7bb4e945844ff14d86c1d2d3b_720" src="https://github.com/user-attachments/assets/f1820e62-1f0a-40a5-aa80-6f9ba28a50ca" />

</div>

### 2. 电子调速器
* 选择独立电调，其相较于内部集成电调，能更稳定持续地输出推力，且成本低。
* 要能实现反转，即选择双向电调。
* 注意输入电压，和尺寸等参数需协调整个系统。
* 电调持续电流参数需根据推进器参数选择，最好选择持续电流为（推进器峰值电流×1.2）的电调，
  又考虑到密封舱内散热受限，则可通过选择更大规格的电调，来降低mos导通热损耗，并且大规格电调在市面上型号更丰富，适配性更好。
比如选择 2 个 RuiBet 45A 四合一电调 （余下的两个接口做备用）


  <img src="https://github.com/user-attachments/assets/9a00fff0-6a99-4727-af38-a84e8b1d9a59" width="300" />
</div>
