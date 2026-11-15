I have a Pololu 4841 DC Motor (https://www.pololu.com/product/4841 (4.4:1 - gear ratio;	2200	 rpm no-load speed version))



I want to achieve the following steps:

Create another Simulink model that implements the speed control using an Arduino Uno, the real motor with encoders and also a current sensor. The reference range is from -1500 to 1500 rpm.



For the modeling use the MATLAB Agentic Toolkit and Simulink Agentic Toolkit tools and skills - ensure that you rely on them as much as possible.

Follow this folder structure:

1\_Implementation

2\_SupportingArtifacts

3\_Cache

4\_Codegen

DCMotoroControl.prj

I already created this structure and the project is open on the current MATLAB path.



In the 2\_Implementation save the models and additional files of the task.

In the 3\_SupportingArtifacts place the additional .md and description files.

3\_Cache - cache folder set up for Simulink cache - already configured in the .prj.

4\_Codegen - Simulink code generation folder - already configured in the .prj.



**For the substeps find a more detailed description:**

**Simulink + Arduino + real motor**

The Motor is connected to and Arduino Uno with the following details:

Arduino Uno - controller

Pololu 4841 - DC Motor with Encoder

Current sensor - ACS712 5A

I want to you to take these steps:

Use the Simulink Support Package for Arduino Hardware for the Arduino IO blocks.

There is no driver created for BTS 7960M driver, but I created one that is in the 2\_Implementation folder. Ensure that you use that one - copy the Subsystem to the main model.



Measure the speed through the encoder - create a subsystem that uses the encoder block input and outputs the RPM of the motor

Execute the model where you add 100% PWM signal open loop in both directions to tune and calibrate the sensors.

After the open loop model is done and you calibrated the motor speed measurement, implement the speed control.

In the speed control, ensure that you use a PI controller block for the speed control.

Tune the PI controller and make a signal that goes from 1500 to -1500 rpm by stepping ca. 150-200 rpm down every 2 seconds.



The connections between the DC motor, encoder, BTS7960M are as follows:

Encoder Pin A: 2

Encoder Pin B: 3

7960M Driver: you have the connections already configured in the DC7950MDriver.slx - reference subsystem - no need to modify the ports there

Current sensor: connected to analog pin A3 - but to speed control only, it is not necessary to use.



Before starting the implementation propose a plan that you will implement. Ensure that there are milestones with clear gates before moving forward. Ensure that each approved milestones model gets saved, there will be no version control in the project.

