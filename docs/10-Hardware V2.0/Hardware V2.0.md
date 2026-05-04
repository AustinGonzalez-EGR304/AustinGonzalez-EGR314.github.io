---
title: Hardware V2.0
---

## Revisons
During this project, the majority of my issues stemmed from errors in my PCB layout. I misinterpreted several pin functions in the microcontroller datasheet, which resulted in a largely non-functional board. Specific problems included incorrect voltage levels on the I2C communication lines, improperly configured button circuits (pull-down instead of pull-up), inconsistent USB connectivity, and the use of incompatible pins for UART and I2C communication. Because the design utilized nearly all available pins, I had very limited flexibility to reassign signals or implement hardware fixes during testing.

If I were to redesign this system, I would begin by better scoping the system requirements and selecting a microcontroller with sufficient I/O resources. Alternatively, I would reduce system complexity in the initial design iteration. For example, implementing only one stepper motor driver in the first version would have allowed for easier debugging and rework, with additional functionality added in later revisions. This approach would improve modularity and reduce the risk of total system failure.

I would also place greater emphasis on validating pin configurations before finalizing the PCB. This includes verifying boot requirements, ensuring proper pull-up and pull-down resistor configurations, and confirming peripheral compatibility (UART, I2C, etc.). In my current design, incorrect button wiring interfered with both system startup and I2C communication, requiring manual hardware modifications to restore basic functionality.

Finally, I would improve the physical PCB design by increasing trace widths and paying closer attention to scale during layout. Designing on a large monitor caused me to underestimate the actual size of traces and spacing, which could impact both reliability and manufacturability. Incorporating design rule checks and printing the layout to scale before fabrication would help prevent these issues in future iterations.