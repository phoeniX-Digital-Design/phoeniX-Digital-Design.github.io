<div style="text-align: center; margin-bottom: 20px;">
    <div style="display: inline-block; margin: 0 0; text-align: center; border-right: 2px solid #575757">
        <a href="https://phoenix-digital-design.github.io/" target="blank">
            <p style="display: block; margin: 0 15px; text-align: center; color: #24292e;">Home</p>
        </a>
    </div>
    <div style="display: inline-block; margin: 0 0; text-align: center; border-right: 2px solid #575757">
        <a href="https://phoenix-digital-design.github.io/news/news.html" target="blank">
            <p style="display: block; margin: 0 15px; text-align: center; color: #24292e;">News</p>
        </a>
    </div>
    <div style="display: inline-block; margin: 0 0; text-align: center; border-right: 2px solid #575757">
        <a href="https://phoenix-digital-design.github.io/projects/projects.html" target="blank">
            <p style="display: block; margin: 0 15px; text-align: center; color: #24292e;">Projects</p>
        </a>
    </div>
    <div style="display: inline-block; margin: 0 0; text-align: center; border-right: 2px solid #575757">
        <a href="https://phoenix-digital-design.github.io/software/software.html" target="blank">
            <p style="display: block; margin: 0 15px; text-align: center; color: #24292e;">Software</p>
        </a>
    </div>
    <div style="display: inline-block; margin: 0 0; text-align: center; border-right: 2px solid #575757">
        <a href="https://phoenix-digital-design.github.io/#the-team" target="blank">
            <p style="display: block; margin: 0 15px; text-align: center; color: #24292e;">The Team</p>
        </a>
    </div>
    <div style="display: inline-block; margin: 0 0; text-align: center">
        <a href="https://phoenix-digital-design.github.io/#contact-us" target="blank">
            <p style="display: block; margin: 0 15px; text-align: center; color: #24292e;">Contact Us</p>
        </a>
    </div>
</div>

# Projects

Our team research focus is advancing computer architecture and VLSI design, with a concentration on developing microarchitectural techniques and circuit-level solutions. Our work aims to address the growing demands for reliability, energy-efficiency, and performance in embedded devices. By exploring cutting-edge methods in low-power design, fault-tolerance, and hardware-software co-design, we create robust systems that meet the challenges of modern applications, including edge computing, AI, and IoT.

## Automated Energy-Efficiency Control in Embedded Processors
Publications: [*In Progress*]

**Abstract:** *Coming Soon!*

## Hardware MLP with Error-Controllable MAC Units for Image Classification
Publications: [[IICM'24](https://arxiv.org/abs/2410.10545)]

**Abstract:** Multi-Layer Perceptrons (MLPs) are widely used for predictive modeling and classification tasks due to their ability to represent complex non-linear relationships. This study presents a hardware-optimized MLP implemented in 45nm CMOS technology, utilizing error- and power-controllable approximate multipliers within neuron MAC units for MNIST classification. The design includes 10 hidden-layer neurons, occupying 0.026mm² and consuming 5.55mW at 100MHz in accurate mode, reduced to 4.81mW in the lowest accuracy mode. Results show up to a 24.78% per-neuron power reduction and 13.33% overall, with only a 0.92% accuracy loss compared to accurate arithmetic.

## The phoeniX: A Reconfigurable RISC-V Platform for Approximate Computing
Publications: [[DSD'24](https://ieeexplore.ieee.org/abstract/document/10741850/)] [[IICM'24](https://arxiv.org/abs/2410.07027)], Links: [[GitHub](https://github.com/phoeniX-Digital-Design/phoeniX)]

**Abstract:** The phoeniX platform is a patially-reconfigurable RV32IEM processor designed to facilitate approximate computing in embedded systems. Its modular architecture allows integration of approximate arithmetic circuits at the core level without necessitating modifications to the control logic, enabling configurable trade-offs between accuracy and energy efficiency tailored to specific application requirements. Implemented in Verilog HDL, phoeniX features a highly optimized 3-stage pipeline, achieving a 1.89 DMIPS/MHz benchmark result. Implemented using 45nm CMOS technology, the original core occupies 0.024 mm², and operates at maximum frequency of 620 MHz with an average energy-efficiency of 7.85 pJ/instruction. This platform serves as a foundation for developing energy-efficient, fault-tolerant applications, particularly in domains such as image processing and edge AI.

## Error Configurable Accurare/Apporximate Circuits
Publications: [[DSD'24](https://ieeexplore.ieee.org/abstract/document/10741850/)] [[IICM'24](https://arxiv.org/abs/2410.07027)] [[IICM'24](https://arxiv.org/abs/2410.10545)] [*In Progress*]

**Abstract:** One research focus in our lab is designing error-controllable arithmetic circuits, such as multipliers and adders, to enable flexible trade-offs between accuracy and hardware-efficiency. These circuits are tailored for high-performance and energy-constrained systems, leveraging approximate computation to reduce critical path delay, power consumption, and silicon area. By integrating precision tuning mechanisms, our designs can dynamically adjust error levels based on application requirements (runtime), ensuring optimal performance for both accurate and approximate modes. This adaptability makes them particularly suitable for applications in machine learning, signal processing, and fault-tolerant systems, where a balance between computational efficiency and output quality is essential.

[Back to Homepage.](https://phoenix-digital-design.github.io/)