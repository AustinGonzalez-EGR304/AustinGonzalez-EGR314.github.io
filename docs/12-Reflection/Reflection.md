---
title: Reflection
---

## Review of Module’s Success

Overall, my module was partially successful in meeting its intended requirements. I was able to implement UART communication within the daisy-chain system and correctly parse incoming messages based on sender, receiver, and message type. The subsystem successfully determined whether a message was intended for it and either acted on it or forwarded it downstream. I also implemented preset-based camera movement logic and a roll-call response, demonstrating correct message handling behavior.

Additionally, I was able to successfully interface with my I2C sensor in an off-board breadboard setup. This confirmed that my sensor configuration and communication code were functioning correctly.

However, several key requirements were not fully achieved due to PCB design issues. The stepper motor system did not function as intended, and onboard I2C communication was unreliable. The off-board success of the sensor indicates that the failure was due to PCB layout, pin configuration, or electrical design rather than software or component selection. These issues ultimately prevented full system integration and reliable operation of the complete module.

---

## Microcontroller / Module Startup Tips

- Always verify pin functionality in the datasheet before assigning them in your design.
- Double-check which pins are required for boot configuration and ensure they are not being unintentionally driven.
- Use proper pull-up resistors for I2C lines and confirm voltage levels before debugging software.
- Start with a minimal working system (UART or LED blink) before integrating additional peripherals.
- Avoid using all available pins; leave extra pins available for debugging and reconfiguration.
- Test communication protocols (UART, I2C) on a breadboard before committing to a PCB.
- If a subsystem fails, test it independently off-board to determine whether the issue is hardware or software related.
- Clearly label and document all pin assignments during the design process.
- Validate power rails early to ensure all components receive correct voltage levels.
- Use LEDs or serial output to confirm code execution during early debugging.

---

## Lessons Learned

## Lessons Learned

1. One of the most important lessons I learned is the importance of thoroughly understanding a microcontroller datasheet before beginning a design. Misinterpreting pin functions led to major PCB issues that could not be corrected after fabrication.

2. I learned that iterative design is critical. Attempting to implement a full system at once made debugging significantly more difficult compared to building and validating smaller subsystems first.

3. Proper electrical design practices are essential, especially for communication protocols such as I2C. Incorrect pull-up configurations can completely prevent communication.

4. I learned that different parts of a circuit can interfere with each other. In my case, button wiring affected I2C voltage levels and prevented proper operation.

5. Separating hardware and software debugging is extremely important. Testing my I2C sensor off-board confirmed that my code was correct and isolated the issue to the PCB.

6. I learned the importance of validating subsystems independently before integrating them into a full system.

7. Leaving flexibility in a design is critical. Using nearly all available microcontroller pins limited my ability to troubleshoot and reroute signals.

8. Simple debugging tools such as LEDs and serial output are very effective for verifying system behavior during early development.

9. Hardware debugging requires a structured and methodical approach, especially when dealing with both electrical and software issues at the same time.

10. Time management is crucial in hardware-based projects, as debugging physical systems often takes significantly longer than expected.

---

## Recommendations for Future Students

1. Start with a minimal working system and gradually add complexity instead of trying to implement the full design at once.
2. Carefully read and understand your microcontroller datasheet, especially pin functions and boot requirements, before creating a PCB design.
3. Always test critical components and communication protocols on a breadboard before committing to a final PCB.
4. Leave extra pins and design flexibility in your system so you can troubleshoot and make adjustments if needed.
5. Standardize package size and common components amongst your teammates to keep parts sharing and ordering easy. 