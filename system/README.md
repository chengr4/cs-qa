# System

## How to build a googd system?

1. 儘可能的優化單機性能 (CPU, memory)
2. 單機處理好後才開始考慮分散式架構

### How to optimize CPU and Memory

- Understand time complexity and space complexity of your code
- 熟悉工具
  - eg redis prevides some data structures, do not pick up the wrong one
- Choose right data structure


## Hypervisor

### What is a hypervisor?

- It is a software that runs virtual machines
  - type 1: Runs directly on the hardware (more effort)
  - type 2: Runs on top of operating system

### Why write a HV?

- Learn more about CPUs
