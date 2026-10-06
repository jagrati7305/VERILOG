## Chapter 2
# Hierarchical Modeling Concepts

## 2.1 Design Methodologies

- There are two basic tyoes of digital design methodologies
    - **Top-Down** Design Methodology
    - **Bottom-Up** Design Methodology

### <u>Top-down Design Methodology</u>

- In Top-Down we define a Top-level block and further subdivide the block until we come to leaf cells.

```mermaid
flowchart TD
    A[Top-Level Block]
    B[Sub-Block 1] 
    C[Sub-Block 2] 
    D[Sub-Block 3] 
    E[Sub-Block 4] 
    F[leaf]
    G[leaf]
    H[leaf]
    I[leaf]
    J[leaf]
    K[leaf]
    L[leaf]

    A --> B
    A --> C
    A --> D
    A --> E

    B --> F
    B --> G

    C --> H
    C --> I

    D --> J
    D --> K
    
    E --> L
```

---

### <u>Bottom-up Design Methodology</u>

- In Bottom-up design methodology we identify the building blocks and then build bigger cells using these building blocks.

```mermaid
flowchart TD
    A[Top-Level Block]
    B[Macro-cell 1] 
    C[Macro-cell 2] 
    D[Macro-cell 3] 
    E[Macro-cell 4] 
    F[leaf-cell]
    G[leaf-cell]
    H[leaf-cell]
    I[leaf-cell]
    J[leaf-cell]
    K[leaf-cell]
    L[leaf-cell]

    L --> E
    K --> D
    J --> D
    I --> C    
    H --> C    
    G --> B    
    F --> B    
   
    B --> A
    C --> A
    D --> A
    E --> A
```
---

- Typically a combination of top-down and bottom-up flows is used.

## 2.2 4 - bit Ripple Carry Counter

### <u>Ripple Carry Counter</u>
![Ripple Carry Counter](./assets/Ripple_Carry_Counter.png)

- It is made of negative edge triggered toggle flip flops.
- Each Toggle Flip Flops can be made up from D-Flipflops.

### <u>T-flipflop</u>
![alt text](./assets/T_FF.png)


### <u>Design Hierarchy</u>
```mermaid
flowchart TD
    A[Ripple Carry Counter]
    B[T FF-1] 
    C[T FF-2] 
    D[T FF-3] 
    E[T FFc-4] 
    F[D_FF]
    G[inverter]
    H[D_FF]
    I[inverter]
    J[D_FF]
    K[inverter]
    L[D_FF]
    M[inverter]

    A --> B
    A --> C
    A --> D
    A --> E

    B --> F
    B --> G

    C --> H
    C --> I

    D --> J
    D --> K
    
    E --> L
    E --> M
```
---

## 2.3 Modules

- A Module is the basic building block in Verilog.

- A Module can be an element or a collection of lower-level design blocks.

- A Module provides the necessary functionality to a higher-level block through its port interface (inputs and outputs), but hide the internal Implementation.

- Example
    - **Ripple Carry Counter -**
    - T_Flipflop and D_Flipflop are example of module.

- Declaration of Module : 
```
    module <MODULE_NAME> (<MODULE_TERMINAL_LIST>);
    ---
    <MODULE_INTERNAL>
    ---
    endmodule

```

- Internal of Each module can be defined at four levels of abstraction, depending upon the needs of design.
    - The module behave identically irrespective of level of abstraction.
    - The Levels are defined below : 
        - Behavioral or Algorithmic level
        - Dataflow level
        - Gate level
        - Switch level

- **Register Transfer Level(RTL)** is used for a Verilog description that uses a combination of behavioral and dataflow constructs and is acceptable to logic synthesis tools.

- Normally the higher level of abstarction the more flexible and technology independent the design. as we go lower towards switch-level design the design becomes technology dependent and inflexible.

---

## 2.4 Instances
- A module provides a template from which you can create actual objects.

- Each Object has its own name, variables, parameters and I/O interface.

- The process of creating objects from a module template iss called **Instantiation**, and the objects is called **Instances**.

- Example 
    - Ripple Carry Counter contains **Four Instances** of **T-flipflop**.
    - Each **T-flipflop** contains instances of **D-flipflop** and **Inverter**.


> In Verilog one module definition cannot contain another module definition within it.

---
## 2.5 New Topic

All the Sample Code will be in Example folder

---