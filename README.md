# Flow-Assistance-of-Delft3D
## ——Happy2Flow

本项目将 Delft3D 中 Flow 常用功能集中显示，添加了并行运算可视化和无人值守计划任务列表功能。

> **⚠️ 注意：仅供学习交流使用，不可用作其他用途！**
>
> 本软件仍有许多问题和改进的空间，但目前无时间继续优化。如有大佬开发了更好的软件，还请让我也体验一下，感激不尽！

---

## 目的

本人平时用的多的是网格、插值、水动力和后处理模块。看到 [B站 @sosoly1978](https://www.bilibili.com/video/BV1jN4y127HA/?spm_id_from=333.337.search-card.all.click&vd_source=9e5fd74d3207deedeedec5d44c6b2289) 开发的 GUI，需要加 QQ 获取。由于本人社恐，为了方便自己使用，制作了这个软件。

---

## 功能

1. **集合常用模块**：将 Delft3D-Flow 模型制作时使用的网格、插值、水动力和后处理模块整合到一起。

2. **并行运算可视化**：
   - 初始化时读取用户计算机核心数；
   - 设置计算核心可选范围为 `总核心数-1`。

3. **无人值守预安排计算任务**：
   - 添加多个 mdf 文件（可在不同路径下，同路径下不可重名）；
   - 调整 mdf 文件顺序后，点击计算即可按顺序执行任务；
   - 取消勾选“无人值守”则只计算待计算任务的第一个任务。

---

## 说明

1. **首次使用路径选择**：
   - 选择安装的 Delft3D 路径，需选择到版本文件夹（如安装了多个版本，选择其中一个，例如：`C:\Program Files\Deltares\Delft3D 4.04.01`）。
   - 软件未添加修改Delft3D路径功能，若需重置路径，请在 `Happy2Flow.exe` 同路径下添加名为 `initial.txt` 文件（不需要内容）以初始化软件。

2. **首次使用提醒设置**：
   - 软件会提示是否弹出提醒，用户可选择下次是否弹出。

3. **基础了解要求**：
   - 默认用户对 Delft3D 和 Matlab 有基础的了解，并掌握 MPI 使用。
   - **首次使用并行运算需开启 smpd 服务**：
     1. 使用管理员权限打开命令提示符。
     2. 输入以下命令（注意修改对应版本号）：
        ```bash
        cd C:\Program Files\Deltares\Delft3D 4.04.01\x64\share\bin
        smpd -install -phrase behappy
        ```
     3. 提示 `MPICH2 Process Manager, Argonne National Lab installed.` 即表示安装成功。

4. **任务检测逻辑**：
   - 软件在第 6 秒、1 分钟、10 分钟、30 分钟及后续间隔 60 分钟检测 `d_hydro.exe` 进程，判断是否开始下一个任务的计算。
   - 这些时间点会短暂消耗算力（类似计算动量时写入文件的卡顿），为正常现象。

5. **Matlab 运行时要求**：
   - 软件由 Matlab2023b 编写，需使用对应版本的编译器。
   - 可在 [MathWorks 官网](https://ww2.mathworks.cn/products/compiler/matlab-runtime.html) 下载 `MATLAB Runtime`。

6. **附带测试算例**：
   - `Happy2Flow.zip` 中提供了简单的测试算例，供参考。

---

## 问题

1. **Quickplot 模块无法正常使用**：
   - 在 Matlab 中可正常调用，但打包后运行时，Quickplot 在初始化界面后会自动结束。
   - 尝试过修改路径、环境变量、创建批处理文件、调用 `d3d_qp.m` 函数等，均未解决。
   - 若有解决方法，还请大佬赐教，不胜感激！

2. **内存与启动性能**：
   - 软件运行时内存占用需留意，启动时会短暂占用 CPU 资源。
   - 本人非计算机专业，代码优化有限，敬请谅解。

---

感谢使用本软件！若有问题或建议，欢迎与我联系。
