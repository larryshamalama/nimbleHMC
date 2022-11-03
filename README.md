# nimbleHMC

[![tests](https://github.com/nimble-dev/nimbleHMC/workflows/tests/badge.svg)](https://github.com/nimble-dev/nimbleHMC/actions)

Provides derivative-based MCMC sampling algorithms for use in conjunction with the `nimble` package.  These include:

- Hamiltonian Monte Carlo (HMC-NUTS) sampler
- Langevin sampler (*under development*)

See the [nimble website](https://r-nimble.org/) for more information and examples.

<!--
The nimbleHMC package must be used with nimble version XXXX or 
higher. To check the current version number of nimble use `packageVersion("nimble")`. 
-->

### Installation

The `nimbleHMC` package must be used with nimble the `AD-rc0` branch of the `nimble` package.  To install this version of `nimble` and the `nimbleHMC` package, use:
```
library(devtools)
install_github("nimble-dev/nimble", ref = "AD-rc0", subdir = "packages/nimble")
install_github("nimble-dev/nimbleHMC", subdir = "nimbleHMC")
```

For errors during installation of `nimbleHMC` occuring on Windows machines, relating to either of the following error messages:
```
Error: package 'nimble' is not installed for 'arch = i386'
Error: loading failed for 'i386'
```
try installing the `nimbleHMC` package using:
```
devtools::install_github("nimble-dev/nimbleHMC", subdir = "nimbleHMC", INSTALL_opts=c("--no-multiarch"))
```


### Automatic Differentiation in `nimble`

`nimbleHMC` makes use of the automatic differentiation (AD) feature of `nimble`, which is currently available as a beta release.  See [nimble AD beta release](https://r-nimble.org/ad-beta) for more information about models and algorithms that make use of the AD features of `nimble`.

For using HMC on models that include user-defined distributions, you will need to include the argument `buildDerivs = TRUE` in the definition of your distribution, as:

```
dmy_distribution <- nimbleFunction(
    run = function(x = double(), param = double(), log = integer(0, default = 0)) {
        ...
    },
    buildDerivs = TRUE
)
```





