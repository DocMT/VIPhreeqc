<p align="center">
  <img src="https://github.com/Vitens/VIPhreeqc/blob/master/logo.png" alt="VIPhreeqc Logo"/>
</p>


| Build Type | **Status** |
|---|---|
| CMake Multi Platform (**Windows** and **Linux**) | [![CMake on multiple platforms](https://github.com/DocMT/VIPhreeqc/actions/workflows/cmake-multi-platform.yml/badge.svg)](https://github.com/DocMT/VIPhreeqc/actions/workflows/cmake-multi-platform.yml) |

Extension of the IPhreeqc 3.3.7 module ([Parkhurst&Appello](http://wwwbrr.cr.usgs.gov/projects/GWC_coupled/phreeqc/)).
This extension aims to add more flexibility to the IPhreeqc module by exposing more information to the C extension. Instead of relying on SELECTED_OUTPUT this extensions enables users to directly gather information such as the pH, SC, speciation, element totals etc. of solutions.

## Implemented Functionality
The following functions are implemented in addition to the standard IPhreeqc functionality:
```C
  // gas functions
  /**
   * Returns the volume of the specified gas_phase
   */
  double                  GetGasVolume(int gas_phase);
  /**
   * Returns the pressure of the specified gas_phase
   */
  double                  GetGasPressure(int gas_phase);
  /**
   * Returns the total moles of the specified gas_phase
   */
  double                  GetGasTotalMoles(int gas_phase);
  /**
   * Returns a list of components in the gas phase
   */
  std::string             GetGasComponents(int gas_phase);

  /**
   * Returns the amount of moles in a gas component
   */
  double             GetGasComponentMoles(int gas_phase, const char* component);

  // equilibrium phase functions
  /**
   * Returns a list of components in the equilibrium phase
   */
  std::string             GetEquilibriumPhaseComponents(int eq_phase);
  /**
   * Returns the amount of moles in a equilibrium phase component
   */
  double             GetEquilibriumPhaseComponentMoles(int eq_phase, const char* component);


  // volume functions
  /**
   * Returns the pH of the specified solution
   */
  double                  GetPH(int solution);
  /**
   * Returns the pe of the specified solution
   */
  double                  GetPe(int solution);
  /**
   * Returns the specific conductance (in uS/cm) of the specified solution
   */
  double                  GetSC(int solution);
  /**
   * Returns the temperature (degrees Celsius) of the specified solution
   */
  double                  GetMu(int solution);
  /**
   * Returns the ionic strength (mol/kgw) of the specified solution
   */
  double                  GetTemperature(int solution);
  /**
   * Returns the mass (kg) of the specified solution
   */
  double                  GetMass(int solution);
  /**
   * Returns the volume (l) of the specified solution
   */
  double                  GetVolume(int solution);
  /**
   * Returns the density (kg/l) of the specified solution
   */
  double                  GetDensity(int solution);
  /**
   * Returns the amount (in mol) of an element (e.g. C(-4), Ca, etc.)
   */
  double                  GetTotal(int solution, const char *string);
  /**
   * Returns the total amount (in mol) of an element (e.g. C, Ca, etc.)
   */
  double                  GetTotalElement(int solution, const char *string);
  /**
   * Returns the amount of moles (in mol) of a species (e.g. Ca+2, OH-, etc.)
   */
  double                  GetActivity(int solution, const char *species);
  /**
   * Returns the activity of a species (e.g. Ca+2, OH-, etc.)
   */
  double                  GetMoles(int solution, const char *species);
  /**
   * Returns the molality (in mol/kgW) of a species (e.g. Ca+2, OH-, etc.)
   */
  double                  GetMolality(int solution, const char *species);
  /**
   * Return the diffusion coefficient of a species
   */
  double                  GetDiffusion(int solution, const char *species);
  /**
   * Returns a comma separated list of all the species in the selected solution
   */
  std::string             GetSpecies(int solution);
  /**
   * Returns a semicolon separated list of all the species and their master elements in the selected solution
   */
  std::string             GetSpeciesMasters(int solution);
  /**
   * Returns the Solubility Index of a phase in a solution
   */
  double                  GetSI(int solution, const char *phase);
  /**
   * Returns a comma separated list of all the phases in the selected solution
   */
  std::string             GetPhases(int solution);
  /**
   * Returns a comma separated list of all the elements in the selected solution
   */
  std::string             GetElements(int solution);
  /**
   * Returns a comma separated list of all the solutions in the current runstate
   */
  std::string             GetSolutionList2(int id);
```
### Error values
The following values are returned on error
```C
-99  = Invalid IPhreeqc Instance
-999 = Solution Not Found
```
## Downloads
Download a pre-build binary for the right platform using one of the links below:
- [Windows (x64)](http://ci.abelheinsbroek.nl/viphreeqc.zip)
- [Linux](http://ci.abelheinsbroek.nl/viphreeqc.so)
- [OS X](http://ci.abelheinsbroek.nl/viphreeqc.dylib)

## About Vitens
Vitens is the largest drinking water company in The Netherlands. We deliver top quality drinking water to 5.6 million people and companies in the provinces Flevoland, Fryslân, Gelderland, Utrecht and Overijssel and some municipalities in Drenthe and Noord-Holland. Annually we deliver 350 million m³ water with 1,400 employees, 100 water treatment works and 49,000 kilometres of water mains.

One of our main focus points is using advanced water quality, quantity and hydraulics models to further improve and optimize our treatment and distribution processes.

## Licence

Copyright 2016 Vitens

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
