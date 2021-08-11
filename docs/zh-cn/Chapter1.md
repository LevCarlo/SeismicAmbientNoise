## 1.3 PSDPDF 可视化和应用

地震功率的长期变化（包括：仪器问题、地理位置的差异及昼夜和季节变化）可以通过单一PSDPDF很好的描述。



- 大于20s：仪器的发展可有效压制
- 小于1s：易受人为活动的影响
- 1-20s：地理位置（主要是靠近海岸线的情况）、季节变化



### 1.3.1 关于地震环境噪声的主要震源的综述

#### 短周期环境噪声(<1s)

大体上，短周期环境噪声与人类活动有关，中、长周期的环境噪声主要由海浪产生，但并不总是这样。

- **Cultural noise**

  交通与机械的耦合

  人类活动相关的噪声源一般具有双峰的特征。白天与黑夜，工作日与周末。

  非常尖锐和明显特征周期频带

- **Glacier Calving（冰川崩解）**

- **Wind**

  风与地表的相互作用

#### 中周期环境噪声

- **（海洋）微震**

  Rayleigh波噪声源的相关研究：Webb and Constable (1986); Cessaro (1994); Stehly et al. (2006);Kedar et al. (2008);Obrebski et al. (2012)

  体波噪声源的相关研究：Gerstoft and Tanimoto (2007); Koper et al. (2009, 2010)；Landès et al. (2010).

  （沿海地区）短周期的噪声水平过高会对P波探测带来不利影响。

- **额外的热带风暴/热带飓风**

- **Sea Ice(海上浮冰)**

  海冰会影响次级微震的带宽和绝对功率水平

#### 长周期环境噪声（>20s)

- **hum**

  与地球的自由振荡有关

  激发：到达海岸线海水的膨胀部分转化为更长周期的（信号）

- **Seiche（假潮）**

## 1.4 地震监测的应用

### 1.4.1 地震台站的设计与建造



### 1.4.2 地震数据的质量评估

基于PSDPDF自动检测不良的仪器响应以及系统产生的其他非正常瞬变信号。

其基本原理是相较于长期基线而言，由于系统问题造成的短期误差是很容易探测出来的。

## 1.5 结论

ObsPy中有相应的工具包

[Visualizing Probabilistic Power Spectral Densities](https://docs.obspy.org/tutorial/code_snippets/probabilistic_power_spectral_density.html)