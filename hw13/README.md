# VP13 RLC and Transient Behavior

[官方PDF檔](VP13.pdf)  

## 作業繳交格式

請上傳一個zip檔（壓縮檔，請注意副檔名要是zip）到CEIBA，zip檔內需要包含一個**名稱是自己學號的資料夾**，裡面包含一個py檔，取名為 `must.py` 。請記得拍攝說明影片，並**將影片連結寫在video.txt裡面，並一併放入學號資料夾中**。

範例：
```
the_zip_file.zip
└── r07222060
    ├── must.py
    └── video.txt
```

## Deadline

`Not determined yet`

## Contents  

+ [I. Introduction](#i-introduction)  
+ [Homework](#ii-homework)  

## I. Introduction

An RLC circuit, with <img src="https://latex.codecogs.com/svg.latex?\dpi{300}&space;&space;\text{R}&space;=&space;30\&space;(\Omega)" height=16/>, <img src="https://latex.codecogs.com/svg.latex?\dpi{300}&space;\&space;\text{L}&space;=&space;200\&space;(\text{mH})" height=16/>, <img src="https://latex.codecogs.com/svg.latex?\dpi{300}&space;&space;\text{C}&space;=&space;20\&space;(\mu\textup{F})" height=16/>. The driving voltage source is

<img src="https://latex.codecogs.com/svg.latex?\dpi{300}&space;v(t)&space;=&space;\left\{\begin{matrix}&space;0,&space;&&space;\text{if}\&space;t&space;<&space;0&space;\\&space;36&space;\cdot&space;\sin(2\pi&space;f_d&space;t),&space;&&space;\text{if}\&space;0&space;\leq&space;t&space;<&space;12\text{T}&space;\\&space;0,&space;&&space;\text{if}\&space;12\text{T}&space;\leq&space;t&space;\end{matrix}\right." title="v(t) = \left\{\begin{matrix} 0, & \text{if}\ t < 0 \\ 36 \cdot \sin(2\pi f_d t), & \text{if}\ 0 \leq t < 12T \\ 0, & \text{if}\ 12T \leq t \end{matrix}\right."  height=80/>

\
where <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;f_d&space;=&space;120\&space;(\text{Hz})" title="f_d = 120\ (\text{Hz})" />, <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;\text{T}&space;=&space;1/f_d" title="\text{T} = 1/f_d" />.

<img src="pic/circuit.png" height=200/>

## II. Homework

> 助教註: 這次（其實好像是每次）沒有 Optional 部份，所以 滿分是 125% 。

### (1)

Solve this circuit numerically and plot the voltage <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;v(t)" title="v(t)" /> and the current <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;i(t)" title="i(t)" /> as a function of <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;t" title="t" /> for <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;t&space;\in&space;[0,&space;20\text{T}]" title="t \in [0, 20\text{T}]" /> in `scene1` and the total energy <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;\text{E}(\text{T})" title="\text{E}(\text{T})" /> stored in the system in `scene2`.

### (2)

You will see a transient behavior of the current <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;i(t)" title="i(t)" /> before it reaches a steady-state oscillation around <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;t&space;=&space;9\text{T}" title="t = 9\text{T}" />. Find <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;I" title="I" />, the amplitude of the oscillating current, and <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;\phi" title="\phi" /> the phase constant of the oscillating current relative to the voltage source during the 9-th period. Compare them to the theoretical values.

### (3)

After the voltage is turned off at <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;t&space;=&space;12&space;\text{T}" title="t = 12 \text{T}" />, you will see both the current and the total energy decays. Find the time <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;t" title="t" /> such that the energy decays to 10% of the energy at the time the voltage is just turned off, i.e., <img src="https://latex.codecogs.com/svg.latex?\dpi{150}&space;\text{E}(t)&space;=&space;0.1\text{E}(t=12\text{T})" title="\text{E}(t) = 0.1\text{E}(t=12\text{T})" />.

### Template codes

```python
from vpython import *

fd = 120                # 120 Hz
# ===== Add your parameters here =====

t = 0
dt = 1.0 / (fd*5000)    # 5000 simulation points per cycle

scene1 = graph(align='left', xtitle='t', ytitle='i(A) blue, v(100V) red', background=vector(0.6, 0.9, 0.6))
scene2 = graph(align='left', xtitle='t', ytitle='Energy(J)', background=vector(0.6, 0.9, 0.6))

i_t = gcurve(color=color.blue, graph=scene1)
v_t = gcurve(color=color.red, graph=scene1)
E_t = gcurve(color=color.red, graph=scene2)

# ===== Your codes here =====
 
```
