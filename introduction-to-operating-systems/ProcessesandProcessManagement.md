# Processes and process and management

## DEF
- instance of an executing program

## Content
- state of execution: program coutner, stack
- parts and temporary holding area: data, register state ocupies state in memory
- may require special hardware: I/O devices

### What does a process look like?
| Vmax: stack   |
| --------   |
|  something...|
| heap      |
| data      |
|V0: text   |

- Type of state
    - text and data
        - static state when process first loads
    - heap
        - dynamically created during execution
    - stack
        - grows and shrinks
        - LIFO queue

- Analysis
    - virtual addresses are used by process
    - address space == "in memory" representation of a process
    - page tables == mapping of virtual to physical addresses, page table entry(a pair)
    - physical memory: DRAM
    - the memory must keep some information about a process and parts of virtual address space may not be allocated due to there may not be enough physical memory for all states
    - virtual memory of two processes can be identical. The page table will map the virtual address space to physical memory space.

## Process Execution State
### How does th OS know what a process is doing?
- program counter
- PCU register
- state pointer(top of the stack)
- other things needed to maintain: OS maintain a process control block(PCB)
