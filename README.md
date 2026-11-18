# CNN
CNN algorithm for LSI-Design Contest 2027

## Repository Structure

| Folder | Content |
|---|---|
| `dataset/` | Datasets used for training and testing |
| `python/` | CNN algorithm (training, quantization, reference model) |
| `verilog/` | Verilog code for the CNN hardware |
| `report/` | Implementation results report (Laporan hasil implementasi) |

## Problem Candidates (32×32 input images)

The CNN should be small enough to implement in hardware (FPGA/ASIC). Below are candidate problems.

### Easy and reliable

1. **Handwritten digits (MNIST, padded to 32×32)**
   - 10 classes, grayscale
   - About 99% accuracy with a tiny network such as LeNet-5 (designed for 32×32 input)
   - Safest choice when the main focus is the Verilog implementation
2. **Traffic sign recognition (GTSRB)**
   - 43 classes, usually resized to 32×32
   - Real-world use (driver assistance), easy to explain to judges

### More challenging

3. **CIFAR-10**
   - 10 object classes (car, cat, plane, …), 32×32 color
   - Well-known benchmark, but needs a bigger network to reach about 85–90%, so the hardware gets bigger too
4. **Fashion-MNIST**
   - Clothing items, same size as MNIST but harder
   - Good middle ground

### More unique (helps stand out)

5. **Face mask / helmet detection**: 2–3 classes, practical safety use
6. **Wafer defect or PCB defect classification**: fits an LSI contest theme very well; public datasets exist, such as WM-811K wafer maps, which can be resized to 32×32
7. **Hand gesture / sign language letters (Sign Language MNIST)**: interactive demo with a camera

## Suggested Plan

1. Start with **LeNet-5 on MNIST** to prove the whole flow works:
   Python training → quantize weights to 8-bit fixed point → Verilog → compare outputs with the Python model
2. Switch to **GTSRB or wafer defect classification** for the final entry, so the project is both safe and interesting.

> Note: check the LSI Design Contest 2027 rules first, in case the contest requires a specific task or theme.
