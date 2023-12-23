# 打包

本篇手册罗列打包时的注意事项。

## 计算 shader

为了实现光学回形的检测，`Assets/Shaders/Computing Utilities` 里放了不少专门用来计算的 shader。
这些 shader 没有被任何材质引用，务必记得加到 project settings 里的 always include shaders 列表里。