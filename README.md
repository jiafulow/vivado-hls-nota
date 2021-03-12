# vivado-hls-nota

The following tables and figures are taken from Xilinx official documentation:
- [UG479 7 Series DSP48E1 Slice (v1.10)](https://www.xilinx.com/support/documentation/user_guides/ug479_7Series_DSP48E1.pdf)
- [UG573 UltraScale Architecture Memory Resources (v1.12)](https://www.xilinx.com/support/documentation/user_guides/ug573-ultrascale-memory-resources.pdf)
- [UG579 UltraScale Architecture DSP Slice (v1.10)](https://www.xilinx.com/support/documentation/user_guides/ug579-ultrascale-dsp.pdf)
- [UG902 Vivado Design Suite User Guide: High-Level Synthesis (v2020.1)](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2020_1/ug902-vivado-high-level-synthesis.pdf)
- [UG998 Introduction to FPGA Design with Vivado High-Level Synthesis (v1.1)](https://www.xilinx.com/support/documentation/sw_manuals/ug998-vivado-intro-fpga-design-hls.pdf)
- [UG1197 UltraFast Vivado HLS Methodology Guide (v2020.1)](https://www.xilinx.com/support/documentation/sw_manuals/ug1197-vivado-high-level-productivity.pdf)
- [UG1270 Vivado HLS Optimization Methodology Guide (v2018.1)](https://www.xilinx.com/content/dam/xilinx/support/documentation/sw_manuals/xilinx2018_1/ug1270-vivado-hls-opt-methodology-guide.pdf)

## HLS Optimization Methodology

<table>
<tr><td><img src="/images/ug1197-fig-4-5.png" alt="HLS Optimization Methodology"/></td></tr>
</table>

Source: UG1197 Figure 4-5

## Vivado HLS Design Flow

<table>
<tr><td><img src="/images/ug902-fig-4.png" alt="Vivado HLS Design Flow"/></td></tr>
</table>

Source: UG902 Figure 4

## Vivado HLS Pragmas By Type

<table>
<tr>
<th>Type</th>
<th>Attributes</th>
</tr>
<tr>
<td>Kernel Optimization</td>
<td><ul><li>pragma HLS allocation</li><li>pragma HLS expression_balance</li><li>pragma HLS latency</li><li>pragma HLS reset</li><li>pragma HLS resource</li><li>pragma HLS stable</li></ul></td>
</tr>
<tr>
<td>Function Inlining</td>
<td><ul><li>pragma HLS inline</li><li>pragma HLS function_instantiate</li></ul></td>
</tr>
<tr>
<td>Interface Synthesis</td>
<td><ul><li>pragma HLS interface</li></ul></td>
</tr>
<tr>
<td>Task-level Pipeline</td>
<td><ul><li>pragma HLS dataflow</li><li>pragma HLS stream</li></ul></td>
</tr>
<tr>
<td>Pipeline</td>
<td><ul><li>pragma HLS pipeline</li><li>pragma HLS occurrence</li></ul></td>
</tr>
<tr>
<td>Loop Unrolling</td>
<td><ul><li>pragma HLS unroll</li><li>pragma HLS dependence</li></ul></td>
</tr>
<tr>
<td>Loop Optimization</td>
<td><ul><li>pragma HLS loop_flatten</li><li>pragma HLS loop_merge</li><li>pragma HLS loop_tripcount</li></ul></td>
</tr>
<tr>
<td>Array Optimization</td>
<td><ul><li>pragma HLS array_map</li><li>pragma HLS array_partition</li><li>pragma HLS array_reshape</li></ul></td>
</tr>
<tr>
<td>Structure Packing</td>
<td><ul><li>pragma HLS data_pack</li></ul></td>
</tr>
</table>

## Vivado HLS Optimization Directives

<table>
<tr><td><img src="/images/ug902-table-11.png" alt="Vivado HLS Optimization Directives"/></td></tr>
</table>

Source: UG902 Table 11

<table>
<tr><td>Loop pipelining:<br /><img src="/images/sdaccel-fig-pipeline.png" alt="Loop pipelining"/></td></tr>
<tr><td>Dataflow optimization:<br /><img src="/images/sdaccel-fig-dataflow.png" alt="Dataflow optimization"/></td></tr>
<tr><td>Array reshaping:<br /><img src="/images/sdaccel-fig-array-reshape.png" alt="Array reshaping"/></td></tr>
<tr><td>Array partitioning:<br /><img src="/images/sdaccel-fig-array-partition.png" alt="Array partitioning"/></td></tr>
</table>

Source: [SDAccel Development Environment Help](https://www.xilinx.com/html_docs/xilinx2019_1/sdaccel_doc/hls-pragmas-okr1504034364623.html)

## Vivado HLS Configurations

<table>
<tr><td><img src="/images/ug902-table-12.png" alt="Vivado HLS Configurations"/></td></tr>
</table>

Source: UG902 Table 12

## C++ Arbitrary Precision Integer Types

The header file `ap_int.h` defines the following arbitrary precision integer data types:

- `ap_int<W>`
- `ap_uint<W>`

where `W` is the number of bits. For example, `ap_int<8>` represents an 8-bit signed integer data type; `ap_uint<234>` represents a 234-bit unsigned integer type.

## C++ Arbitrary Precision Fixed-Point Types

The header file `ap_fixed.h` defines the following arbitrary precision fixed-point data types:

- `ap_fixed<W,I,Q,O,N>`
- `ap_ufixed<W,I,Q,O,N>`

where `W` is the total number of bits, `I` is the number of integer bits, `W-I` is the number of fractional bits, `Q` specifies the type of rounding, `O` and `N` specify the overflow behavior. For example, `ap_fixed<6,3>` represents an 6-bit signed value with 3 integer bits and 3 fractional bits, where the MSB position is the sign bit, followed by 2<sup>1</sup>, 2<sup>0</sup>, 2<sup>-1</sup>, 2<sup>-2</sup>, 2<sup>-3</sup> bits. `ap_ufixed<10,8>` represents an 10-bit signed value with 8 integer bits and 2 fractional bits.

<table>
<tr><th>Identifier</th><th colspan="3">Description</th></tr>
<tr><td>W</td><td colspan="3">Word length in bits.</td></tr>
<tr><td>I</td><td colspan="3">The number of bits used to represent the integer value (the number of bits above the decimal point).</td></tr>
<tr><td rowspan="9">Q</td><td colspan="3">Quantization mode dictates the behavior when greater precision is generated than can be defined by smallest fractional bit in the variable used to store thre result.</td></tr>
<tr><th>Mode</th><th colspan="2">Description</th></tr>
<tr><td>AP_RND</td><td colspan="2">Rounding to plus infinity.</td></tr>
<tr><td>AP_RND_ZERO</td><td colspan="2">Rounding to zero.</td></tr>
<tr><td>AP_RND_MIN_INF</td><td colspan="2">Rounding to minus infinity.</td></tr>
<tr><td>AP_RND_INF</td><td colspan="2">Rounding to infinity.</td></tr>
<tr><td>AP_RND_CONV</td><td colspan="2">Convergent rounding.</td></tr>
<tr><td>AP_TRN</td><td colspan="2">Truncation to minus infinity (default).</td></tr>
<tr><td>AP_TRN_ZERO</td><td colspan="2">Truncation to zero.</td></tr>
<tr><td rowspan="7">O</td><td colspan="3">Overflow mode dictates the behavior when more bits are generated than the variable to store the result contains.</td></tr>
<tr><th>Mode</th><th colspan="2">Description</th></tr>
<tr><td>AP_SAT</td><td colspan="2">Saturation.</td></tr>
<tr><td>AP_SAT_ZERO</td><td colspan="2">Saturation to zero.</td></tr>
<tr><td>AP_SAT_SYM</td><td colspan="2">Symmetrical saturation.</td></tr>
<tr><td>AP_WRAP</td><td colspan="2">Wrap around (default).</td></tr>
<tr><td>AP_WRAP_SM</td><td colspan="2">Sign magnitude wrap around.</td></tr>
<tr><td>N</td><td colspan="3">The number of saturation bits used in wrap around overflow modes. The default value is zero.</td></tr>
</table>

## Vivado HLS limitations

- For C and C++ designs only a single clock is supported. The same clock is applied to all functions in the design.

## Vivado HLS examples

- [Xilinx/HLS-Tiny-Tutorials](https://github.com/Xilinx/HLS-Tiny-Tutorials)
- [Xilinx/Vitis_Accel_Examples](https://github.com/Xilinx/Vitis_Accel_Examples)
- [Xilinx/Vitis-Tutorials](https://github.com/Xilinx/Vitis-Tutorials)
- [Xilinx/finn-hlslib](https://github.com/Xilinx/finn-hlslib)


## FPGA resources

### DSP Slice

<table>
<tr><td><img src="/images/ug579-fig-1-1.png" alt="Basic DSP48E2 Functionality"/></td></tr>
</table>

Source: UG579 Figure 1-1

<table>
<tr><td><img src="/images/ug579-fig-2-1.png" alt="Detailed DSP48E2 Functionality"/></td></tr>
</table>

Source: UG579 Figure 2-1

The DSP48E2 slice consists of a 27-bit pre-adder, a 27 x 18 multiplier, a second-stage adder/subtracter/logic unit, and a pattern detector. It produces a 48-bit output. If the multiplier is not used, the DSP slice can also be used as a full 48-bit adder/subtracter and AND/OR/NOT/NAND/NOR/XOR/XNOR logic unit. It also includes a pattern detector that provides support for convergent rounding, overflow/underflow, and counter auto-reset.

The typical use of the slice is to calculate P = (D &pm; A) * B + C. If the multiplier is not used, A and B can be concatenated as A:B to calculate P = A:B + C. Multiple DSP slices can be cascaded to perform accumulation PCOUT = (D &pm; A) * B + PCIN.

The A, B, C, D input ports have the following bit widths:

|Port|Bit Width|Description
|----|---------|-----------
|A   |30       |A[26:0] is the A input of the multiplier or the pre-adder. A[29:0] are the upper bits of the A:B concatenated input.
|B   |18       |The B input of the multiplier. B[17:0] are the lower bits of the A:B concatenated input.
|C   |48       |The C input to the second-stage adder/subtracter, pattern detector, or logic function.
|D   |27       |The D input to the pre-adder or alternative input to the multiplier.

The P. PATTERNDETECT, and PATTERNBDETECT output ports have the following bit widths:

|Port|Bit Width|Description
|----|---------|-----------
|P   |48       |The P output from the second-stage adder/subtracter or logic function.
|PATTERNBDETECT|1|Match indicator between P[47:0] and the complement of the 48-bit pattern.
|PATTERNDETECT|1|Match indicator between P[47:0] and the 48-bit pattern.

The DSP slices in the same column can be cascaded to form accumulators, adders, counters, and other more sophisticated operations. The ability is provided by the cascade input ports (ACIN, BCIN, MULTSIGNIN, CARRYCASCIN, and PCIN) and the cascade output ports (ACOUT, BCOUT, MULTSIGNOUT, CARRYCASCOUT, and PCOUT).

Number of DSP slices on Xilinx FPGAs:

Device                   | # of DSPs
-------------------------|---------:
Kintex-7 325T            |       840
Virtex-7 690T            |     3,600
Kintex UltraScale KU115  |     5,520
Virtex UltraScale+ VU9P  |     6,840
Virtex UltraScale+ VU13P |    12,288

Note that Kintex-7 and Virtex-7 FPGAs have DSP48E1 whereas Virtex Ultrascale+ FPGAs have DSP48E2.

### Block RAM

The BRAM is a dual-port RAM module that can hold either 18K or 36K bits.

## FPGA performance metrics

Area
: Amount of hardware resources required to implement the design based on the resources available in the FPGA, including look-up tables (LUTs), registers, block RAMs, and DSP48s.

Latency
: Number of clock cycles required for the function to compute all output values.

Initiation interval (II)
: Number of clock cycles before the function can accept new input data.

Loop iteration latency
: Number of clock cycles it takes to complete one iteration of the loop.

Loop initiation interval
: Number of clock cycles before the next iteration of the loop starts to process data.

Loop latency
: Number of cycles to execute all iterations of the loop.
