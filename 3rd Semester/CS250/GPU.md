Opened 18:39

Status: #cs250

Tags: [[Components of a Computer System]]

Chapters: 6.6
# GPU (6.6)


## Terminology

| Type                     | More descriptive name            | Closest old term outside of GPUs        | Official CUDA / NVIDIA GPU term | Book definition                                                                                                                                                    |
| ------------------------ | -------------------------------- | --------------------------------------- | ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Program abstractions** |                                  |                                         |                                 |                                                                                                                                                                    |
|                          | Vectorizable Loop                | Vectorizable Loop                       | Grid                            | A vectorizable loop, executed on the GPU, made up of one or more Thread Blocks (bodies of vectorized loop) that can execute in parallel.                           |
|                          | Body of Vectorized Loop          | Body of a (Strip-Mined) Vectorized Loop | Thread Block                    | A vectorized loop executed on a multithreaded SIMD Processor, made up of one or more threads of SIMD instructions. They can communicate via Local Memory.          |
|                          | Sequence of SIMD Lane Operations | One iteration of a scalar loop          | CUDA Thread                     | A vertical cut of a thread of SIMD instructions corresponding to one element executed by one SIMD Lane. Result is stored depending on mask and predicate register. |
| **Machine object**       |                                  |                                         |                                 |                                                                                                                                                                    |
|                          | A Thread of SIMD Instructions    | Thread of Vector Instructions           | Warp                            | A traditional thread, but it contains just SIMD instructions that are executed on a multithreaded SIMD Processor. Results stored depending on a per-element mask.  |
|                          | SIMD Instruction                 | Vector Instruction                      | PTX Instruction                 | A single SIMD instruction executed across SIMD Lanes.                                                                                                              |
|                          | Multithreaded SIMD Processor     | (Multithreaded) Vector Processor        | Streaming Multiprocessor        | A multithreaded SIMD Processor executes threads of SIMD instructions, independent of other SIMD Processors.                                                        |
| **Processing hardware**  |                                  |                                         |                                 |                                                                                                                                                                    |
|                          | Thread Block Scheduler           | Scalar Processor                        | Giga Thread Engine              | Assigns multiple Thread Blocks (bodies of vectorized loop) to multithreaded SIMD Processors.                                                                       |
|                          | SIMD Thread Scheduler            | Thread scheduler in a Multithreaded CPU | Warp Scheduler                  | Hardware unit that schedules and issues threads of SIMD instructions when they are ready to execute; includes a scoreboard to track SIMD Thread execution.         |
|                          | SIMD Lane                        | Vector Lane                             | Thread Processor                | A SIMD Lane executes the operations in a thread of SIMD instructions on a single element. Results stored depending on mask.                                        |
| **Memory hardware**      |                                  |                                         |                                 |                                                                                                                                                                    |
|                          | GPU Memory                       | Main Memory                             | Global Memory                   | DRAM memory accessible by all multithreaded SIMD Processors in a GPU.                                                                                              |
|                          | Local Memory                     | Local Memory                            | Shared Memory                   | Fast local SRAM for one multithreaded SIMD Processor, unavailable to other SIMD Processors.                                                                        |
|                          | SIMD Lane Registers              | Vector Lane Registers                   | Thread Processor Registers      | Registers in a single SIMD Lane allocated across a full thread block (body of vectorized loop).                                                                    |



# References