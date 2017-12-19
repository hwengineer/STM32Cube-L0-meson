# STM32Cube-L0-meson
Another STM32Cube-L0 repos. Optimized for Meson Build System

## differences from original STM32Cube-L0
This repo is mostly just a copy of the original 1.10.0
I added of course a `meson.build` file and made a instance of the `stm32l0xx_hal_conf.h` file.
The `stm32l0xx_hal_conf.h` enables all libs.

This is not a downside! Because the linker will strip all unused symbols and functions from the libs and will only compile if something was changed in the sources we don't have more code- or data-size and also compiles with meson in an instant.

## usage (easy)
use my example project
[B-L072Z-LRWAN-meson-example](https://github.com/hwengineer/B-L072Z-LRWAN-meson-example)

## usage
Use this project as a `git submodule`.

The `meson.build` file defines two variables

-   `stm32cube_srcs`
-   `stm32cube_incdirs`

use this project in your *main* Meson Project as `subdir` project
and use the variables for generating your executable

        # subdir
        subdir('STM32Cube-L0-meson')

        main = executable(
                    'main.elf',
                    [srcs, stm32cube_srcs],
                    c_args              : compilerArgs,
                    link_args           : linkArgs,
                    include_directories : [incdirs, stm32cube_incdirs] )

## License
Of course the STM32Cube Library is under its own license, all other stuff under my chosen MIT License
