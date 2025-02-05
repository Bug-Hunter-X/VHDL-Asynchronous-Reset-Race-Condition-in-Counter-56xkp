# VHDL Asynchronous Reset Race Condition

This repository demonstrates a potential race condition in VHDL code involving an asynchronous reset and a rising-edge-triggered process. The `buggy_counter.vhdl` file contains the buggy code, while `fixed_counter.vhdl` provides a corrected version.

## Bug Description

The original code uses an asynchronous reset (`rst`) along with a rising-edge-sensitive process.  If the `rst` signal glitches at the same time as a clock edge, the counter's behavior becomes indeterminate.  The reset might be sampled incorrectly, leading to unpredictable counter values.

## Solution

The solution involves using a synchronous reset instead of an asynchronous one.  This eliminates the race condition by ensuring that the reset is synchronized to the clock signal. This prevents the reset signal from being sampled in an inconsistent manner, resolving the issue and improving robustness.

## How to Reproduce

1.  Simulate `buggy_counter.vhdl` with a testbench that includes a glitching `rst` signal. Note the inconsistent behavior.
2.  Simulate `fixed_counter.vhdl` with the same testbench. Observe the predictable and consistent behavior of the corrected counter.