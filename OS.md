<div align="center">
  <h1>Operating System</h1>
</div>

Application software performs specific task for the user.

System software operates and controls the computer system and provides a platform to run application software.

An operating system is a piece of software that manages all the resources of a computer system,both hardware and software, and provides an environment in which the user can execute his/her programs in a convenient and efficient manner by hiding underlying complexity of the hardware and acting as a resource manager.

The operating system provides the means for proper use of the resources in the operation of the computer system.

## Why OS?
1. What if there is no OS?

  - Bulky and complex app. (Hardware interaction code must be in app’s
code base)
  - Resource exploitation by 1 App.
  - No memory protection.
   
2. What is an OS made up of?
  - Collection of system software.

## Function
  - Access to the computer hardware.
  - Interface between the user and the computer hardware
  - Resource management (Aka, Arbitration) (memory, device, file, security, process etc)
      - If every app had its own memory management code, they would become too large. Instead, the OS handles memory management for all apps, keeping them simple. (DRY - Do not Repeat Principle)
  - Hides the underlying complexity of the hardware. (Aka, Abstraction)
  - Facilitates execution of application programs by providing isolation and protection.
      - The OS makes sure that one app cannot access or change another app’s memory, keeping them separate and secure.

  
