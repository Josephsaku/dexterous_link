# dexterous_link
A repo for group11 dexterous-link.
本项目是为 具身智能黑客松 (Physical AI Hackathon) 开发的机器人控制框架，由第 11 组开发。我们致力于探索在大模型驱动下，如何实现对 XLeRobot 灵巧手的精准控制与任务执行。

🚀 项目概述
dexterous-link 旨在连接高层视觉语言指令与底层硬件执行。在比赛期间，我们探索了两种主要路径：

基于 OpenClaw 的本体控制：尝试通过自定义 Agent 实现对 XLeRobot 的直接控制。

基于 VLA (Vision-Language-Action) 的端到端控制：利用 smolvla 模型结合 OpenClaw 框架，探索从图像直接输出控制动作的可能性。

🛠 技术路线

方案 A：OpenClaw Agent 直接控制 (Legacy)
我们最初尝试构建一个名为 OpenClaw 的 Agent，旨在直接解析任务逻辑并驱动 XLeRobot 本体。

目标：实现精细的抓取和本体控制动作。

挑战：在开发过程中，由于逆运动学 (Inverse Kinematics, IK) 模块的求解器未能完美适配复杂的结构，导致末端执行器定位失效。

方案 B：VLA + OpenClaw 混合架构 (Current)
为了绕过复杂的显式运动学建模，我们转向了端到端的 VLA 方案。

核心模型：使用 Smolvla 模型。

计算平台：经历了从 Nvidia Jetson Nano 到 Mac (Apple Silicon) 平台的迁移，以获取更高的推理效率和显存支持。

训练方式：Makermods零代码训练平台。

现状：目前已完成基础链路的打通，但受限于黑客松现场的时间限制，模型训练的 Epoch 数量较少，目前的动作表现尚处于初期阶段，由于时间紧张，无法完成任务，存在一定的泛化性挑战。

机器人本体: XLeRobot

控制框架: OpenClaw

开发环境:

Initial: Nvidia Jetson Nano

Current: macOS (M-series chip) / MPS 加速

依赖库: PyTorch, Transformers, LeRobot 等

⚠️ 已知问题与局限性
逆运动学解算: 当前版本的 IK 模块在处理多自由度灵巧手时存在收敛问题。

模型精度: 由于训练轮数 (Epochs) 不足，smolvla 在复杂任务下的成功率有待提高。

Sim2Real: 在模拟器中学习到的动作在迁移至实体 XLeRobot 时存在一定的动力学鸿沟。
