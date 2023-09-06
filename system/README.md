# System

- [Hypervisor](#hypervisor)
- [I/O](#io)
- [Coroutine](#coroutine)
- [Memory](#memory)

## How to build a googd system?

1. 儘可能的優化單機性能 (CPU, memory)
2. 單機處理好後才開始考慮分散式架構

### How to optimize CPU and Memory

- Understand time complexity and space complexity of your code
- 熟悉工具
  - eg redis prevides some data structures, do not pick up the wrong one
- Choose right data structure

## Meomry

Data structure 的 heap 和 memory 的 heap 是同個概念嗎？

不是，他們是不同概念：

- Memory Heap
  - 當你要將資料放入 Memory Heap ，你得要求一定大小的空間。記憶體配置器（memory allocator）會找到一塊夠大的空位，標記為已佔用，然後回傳一個指標（pointer），指著該位置的位址。
  - 指沒特定排序的記憶體空間 
- Priority Queue (Heap)

## I/O

What is I/O?

- two types: 文件 I/O, 網路 I/O

> 緩衝區: 就是指在某個記憶體中，切割一些空間出來，來當緩衝區

### Zero-copy 

## Hypervisor

### What is a hypervisor?

- It is a software that runs virtual machines
  - type 1: Runs directly on the hardware (more effort)
  - type 2: Runs on top of operating system

### Why write a HV?

- Learn more about CPUs

## Coroutine

- lighter than thread
- 它是純應用端的執行單位，作業系統完全不知道它
- 它與 thread 一樣都有自已的記憶體空間
