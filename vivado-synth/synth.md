## Ubuntu
1. go to opentitan
```bash
export REPO_TOP=opentitan
cd $REPO_TOP
```

2. run synth script
```bash
export BOARD=cw310
./bazelisk.sh build //hw/bitstream/vivado:fpga_${BOARD}
# this will create necessary files in /home/joey/.cache/bazel/_bazel_joey/.../execroot/lowrisc_opentitan/bazel-out/k8-fastbuild/bin/hw/bitstream/vivado
```

## Windows
1. mount wsl
```cmd
pushd \\wsl.localhost\Ubuntu
```

2. virtual mount build directory (workaround to windows path length limit)
```cmd
subst A: Z:\home\joey\.cache\bazel\_bazel_joey\31cc141df16675686ee687d88c748e9c\execroot\lowrisc_opentitan\bazel-out\k8-fastbuild\bin\hw\bitstream\build.fpga_cw310
```

3. run vivado tcl file to create project
```cmd
cd synth-vivado
vivado -notrace -mode batch -source lowrisc_systems_chip_earlgrey_${BOARD}_0.1.tcl
```

4. open vivado gui
```
vivado <project_name>.xpr
```
