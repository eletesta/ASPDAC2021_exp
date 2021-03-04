Verilog benchmarks and experiment code files for the work: 

**Algebraic and Boolean Optimization Methods for AQFP Superconducting Circuits**, by E. Testa, S.-Y. Lee, H. Riener, and G. De Micheli, presented at ASPDAC 2021. 

## Benchmarks
The verilog files in `experiments/benchmarks_aqfp/` contain the starting point MIGs (without fanout size limitation) obtained by the LUT-mapping command in [ABC](https://github.com/berkeley-abc/abc):

```
./abc -c "&get; &if -a -K 4; &put;"
```

## Experiments
The file `experiments/aqfp_flow.cpp` contains the code to run the full optimization flow presented in the above paper with the logic synthesis library [mockturtle](https://github.com/lsils/mockturtle). Please refer to its [documentation](https://mockturtle.readthedocs.io/en/latest/installation.html) for instructions on the installation of the library. Note that many changes have been made in `mockturtle` since the implementation of this work, thus different results may be achieved. In order to obtain similar results, please clone from pull request [#426](https://github.com/lsils/mockturtle/pull/426).

To reproduce Tables 1 and 3 in the paper, please copy the entire `experiments` folder from this repository and paste it into the cloned `mockturtle` repository (replacing the original one). Then, configure, compile and run with the following commands:

```
mkdir build
cd build
cmake -DMOCKTURTLE_EXPERIMENTS=ON ..
make aqfp_flow
./experiments/aqfp_flow
```
