# STM32 Hello World — Jenkins Pipeline

A minimal STM32 project used as a playground to validate the Jenkins CI/CD pipeline with the STM32 agent.

## What it does
The pipeline runs on the `stm32` agent and executes four stages:
1. **Checkout** — pulls the code from GitHub
2. **Build** — compiles `stm32f103c8tx` project with `gcc-arm-none-eabi`
4. **Archive** — stores the binary as a build artifact

## Requirements
- A running Jenkins instance with the `stm32` labeled agent (see [jenkins-casc](https://github.com/marcocastellari/jenkins-casc.git))
