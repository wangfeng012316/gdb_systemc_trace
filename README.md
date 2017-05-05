# gdb_systemc_trace
GDB Python scripts for SystemC design introspection and tracing

Creates a trace of all signals and member variables in design


### Limitations
Fixed-point datatypes are not supported yet


## Installation

### Prerequisites
* GDB 7.x configured with Python 2.7 https://www.gnu.org/software/gdb/download/
* libstdc++ pretty printers initialized with .gdbinit https://sourceware.org/gdb/wiki/STLSupport
* Patched SystemC 2.3.1a built as .so library with debuginfo (see below)

### Patching and Building SystemC 
1. Download SystemC 2.3.1.a http://accellera.org/downloads/standards/systemc
2. Replace sc_trace.cpp and sc_trace.h with files from systemc2.3.1.a_patch 
3. Configure build as shared library with debug information:
    (../configure --enable-debug --enable-shared)
4. Build your design with debug info (-g)

## Running simulation with full trace dump

sh run.sh path/to/your/simulation_executable

full_trace.vcd will be created

Use vcd_hierarchy_manipulator to create hierarchical VCDs :https://github.com/yTakatsukasa/vcd_hierarchy_manipulator

Use GtkWave to view vcd waveform : http://gtkwave.sourceforge.net/

## Troubleshooting

Double check that you are using Python 2.7 in GDB and STL pretty printers are installed. 
