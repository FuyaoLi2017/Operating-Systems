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

## PCB
- PCB content
![alter text](https://res.cloudinary.com/dbuk0to55/image/upload/v1554697537/PCB.png)
- PCB created when process is created
- certain fields are updated when process state changes
- other fields change too frequently

## How is a PCB used
- PCB will save the status when a process is interrupted and OS will restored the saved process when it needs to executed again.
- switching between processes is called **context switch**


## Context switch
- definition: switching the CPU from the context of one process to the context of another.
- expensive!
    - direct costs: number of cycles for load 2 store instructions
    - indirect costs: cold cache! cache misses! L1 -> L2 ...  cache hierarchy. lower level -> high accessing efficiency
- Therefore, we need to limit how frequently context switching is done!


### hot cache explanation
- most process data is the cache so the process performance will be at its best
- sometimes we must context switch


## Process life cycle: states
- process can be running, waiting or idling
- picture
![alter text](https://res.cloudinary.com/dbuk0to55/image/upload/v1554698816/process_life_cycle.png)

## Process creation
- Fork
    - copies the parent PCB into new child PCB
    - child continues execution at instruction after fork
- Exec
    - replace child image
    - load nwe progam and start from first
> https://blog.csdn.net/xiaofei0859/article/details/77342173

- quiz:
    - "init" process is the parent of all processes
    - "zygote" process is the parent of all processes in android
    - "launchd" process is the parent of all processes in iOS


## What is the role of the CPU scheduler
A CPU scheduler determines which one of the currently ready processes will be dispatched to the CPU to start running, and how long it should run for.

### OS must be efficient in doing following things
- preempt: interrupt and save current context
- schedule: run scheduler to choose next process
- dispatch: dispatch process 2 switch into its context

## How long should a process run for?
## How frequently should we run the scheduler?
![alter text](https://res.cloudinary.com/dbuk0to55/image/upload/v1554700722/scheduler.png)

## IO operations
![alter text](https://res.cloudinary.com/dbuk0to55/image/upload/v1554700929/IO.png)

## CPU scheduler
- can maintain the ready queue
- can make decision on when to context switch
- can't maintain the I/O queue
- can't make decision on when to generate an event that a process is waiting on


## Interaction between processes
### Inter-Process communication: IPC mechanisms:
- transfer data/info between address spaces
- maintain protection and isolation
- provide flexibility and performance

### Message-passing IPC
