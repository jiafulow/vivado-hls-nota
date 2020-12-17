# vivado-hls-nota

The following tables and figures are taken from Xilinx official documentation:
- [UG902 Vivado Design Suite User Guide: High-Level Synthesis (v2020.1)](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2020_1/ug902-vivado-high-level-synthesis.pdf)
- [UG1197 UltraFast Vivado HLS Methodology Guide (v2020.1)](https://www.xilinx.com/support/documentation/sw_manuals/ug1197-vivado-high-level-productivity.pdf)
- [UG1270 Vivado HLS Optimization Methodology Guide (v2018.1)](https://www.xilinx.com/content/dam/xilinx/support/documentation/sw_manuals/xilinx2018_1/ug1270-vivado-hls-opt-methodology-guide.pdf)

## HLS Optimization Methodology

<table>
<tr>
<td><img src="/images/ug1197-fig-4-5.png" alt="HLS Optimization Methodology"/></td>
</tr>
</table>

(from UG1197 Figure 4-5)

## Vivado HLS Design Flow


<table>
<tr>
<td><img src="/images/ug902-fig-4.png" alt="Vivado HLS Design Flow"/></td>
</tr>
</table>

(from UG902 Figure 4)

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
<tr>
<td><img src="/images/ug902-table-11.png" alt="Vivado HLS Optimization Directives"/></td>
</tr>
</table>

(from UG902 Table 11)

## Vivado HLS Configurations

<table>
<tr>
<td><img src="/images/ug902-table-12.png" alt="Vivado HLS Configurations"/></td>
</tr>
</table>

(from UG902 Table 12)

## Xilinx HLS examples

- [Xilinx/HLS-Tiny-Tutorials](https://github.com/Xilinx/HLS-Tiny-Tutorials)
- [Xilinx/Vitis_Accel_Examples](https://github.com/Xilinx/Vitis_Accel_Examples)
