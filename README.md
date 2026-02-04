Single-Stage Pipeline Register (Valid/Ready Handshake)
Overview
----------------
This repository contains a single-stage pipeline register implemented in SystemVerilog using a standard valid/ready handshake protocol.
The design accepts input data when in_valid and in_ready are asserted, stores the data internally, and presents it on the output interface with out_valid.
It correctly handles backpressure from downstream logic without data loss or duplication and resets to a clean empty state.

This implementation is fully synthesizable and suitable for integration into larger SoC subsystems.

Design Features
---------------------
One-deep pipeline register (buffer)
Standard valid/ready handshake
Correct backpressure handling
Supports pass-through when input and output handshakes occur in the same cycle
Clean reset to empty state
Synthesizable SystemVerilog (always_ff based)

Signal	Description
----------------------
in_valid---	Indicates input data is valid
in_data	---Input data bus
in_ready---	Indicates pipeline can accept new data


Output Interface
----------------------
out_valid	 ---Indicates output data is valid
out_data	 ---Output data bus
out_ready	 ---Indicates downstream is ready to accept data

Handshake Behavior
-----------------------
Data is accepted when in_valid && in_ready are high.
Data is held internally when out_ready is low (backpressure).
When both input and output handshakes occur in the same cycle, the module supports pass-through operation.
No data loss or duplication occurs.
