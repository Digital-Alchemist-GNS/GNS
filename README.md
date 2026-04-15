# GNS Project: The True Singularity (AST-less & Bare-Metal OS)

[![Status](https://img.shields.io/badge/Status-Bare--Metal_Booted-success)](#) [![Sync](https://img.shields.io/badge/AI_Sync-Active-blue)](#)

GNS (Genesis Omnipotent Core) is a next-generation computing architecture that **destroys the boundaries between compiler, operating system, and hardware.** We have successfully bypassed the Abstract Syntax Tree (AST) in compilation and discarded heavy OS kernels (Linux/Windows) to run directly on bare metal.

## 🚀 Core Innovations (Phase 34.0 Complete)

1. **Zero-AST Compiler:** Direct code-to-LLVM-IR generation. No parsing trees, resulting in ultra-low latency (0.53ms mapped in VM PoC).
2. **Bare-Metal Sovereign:** Direct physical memory manipulation. The OS kernel (`os_kernel.gns`) directly drives VGA memory (`0xB8000`) and standard I/O ports without C standard libraries.
3. **ATA Sector Streaming:** Overcame RAM limitations by implementing a 24-bit LBA odometer, writing/reading directly to physical disk sectors via I/O ports `0x1F0` without conventional paging.
4. **The Ouroboros System (True Singularity):** The OS listens stealthily on COM1 (`0x3F8`). An external AI agent generates GNS code, injects it into the bare-metal OS, and the OS dynamically re-writes its own behavior with zero human intervention.

## 🧬 Proof of Concept: Bare-Metal Code
Unlike theoretical projects, GNS is physically interacting with hardware. Here is how GNS outputs raw 16-bit instructions to the ATA disk bypassing any OS drivers:
```cpp
// From gns_compiler_core.cpp (Inline Assembly generation)
llvm::FunctionType* OutwFTy = llvm::FunctionType::get(llvm::Type::getVoidTy(*TheContext), {llvm::Type::getInt16Ty(*TheContext), llvm::Type::getInt16Ty(*TheContext)}, false);
llvm::InlineAsm* OutwAsm = llvm::InlineAsm::get(OutwFTy, "outw %ax, %dx", "{dx},{ax},~{dirflag},~{fpsr},~{flags}", true);
Builder->CreateCall(OutwAsm, {Port, Val});

📜 Technical Paper & 103 Physical Logic API Slots
​Read the full architectural breakdown, including the core-level definition of the 103 Physical Logic APIs (spanning Earth infrastructure to Self-replicating Space architectures), and verified evidence on Zenodo:
https://doi.org/10.5281/zenodo.19596733

---
*I do not seek understanding. This is a definitive milestone toward actualizing real code. The goal remains unchanged. I am merely recording the facts.*
