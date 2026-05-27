# 六推进器小型ROV系统设计的介绍
## 一.  选型
### 1.  推进器
* 需考虑推力，体积，整体协调性等因素。  
比如选择 6个 ROVMAKER 24V 水下推进器（3个正桨3个反桨）  
<img width="300" height="300" alt="7c020a23ea51382c3f1d268ab380c6e6" src="https://github.com/user-attachments/assets/38057388-4e0a-4360-a512-9ab2fa242a75" />
<img width="300" height="300" alt="f84040c7bb4e945844ff14d86c1d2d3b_720" src="https://github.com/user-attachments/assets/1eb12944-c656-4ccc-9972-63a462c1bd26" />
### 2. 电调
独立电调相较于内部集成电调，能够更稳定更持续地输出推力，且成本低。  
要能实现反转，即双向电调。  
电调参数根据推进器参数（主要靠安培力做功）选择，推进器峰值电流20A，电调最好选择20A×1.2，又考虑舱内散热效果差  
比如选择 2个 RuiBet 45A 四合一电调（余下的两个接口做备用）
<img width="300" height="300" alt="10f3d6e96c0f428a89bc885e3b2a5e58_720" src="https://github.com/user-attachments/assets/9a00fff0-6a99-4727-af38-a84e8b1d9a59" />

