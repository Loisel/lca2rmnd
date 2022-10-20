# lca2rmnd
Calculate LCA impacts from REMIND output files

## Usage

To generate a reporting for the REMIND power sector, use the class `ElectricityLCAReporting` like so:
```
        rep = ElectricityLCAReporting(
            scenario, years, bw_project, Path(remind_output_folder),
            methods=indicators,
            regions=["EUR"])
        el_lca = rep.report_sectoral_LCA()
        el_lca.to_csv("sectoral_output.csv")
        
        tech_lca = rep.report_tech_LCA()

```
for the REMIND scenario `scenario` and the timesteps `years`, `bw_project` is the brightway2 project that hosts the relevant databases, 
`remind_output_folder` contains the REMIND scenario outputs, `methods` is a list of brightway2 methods for which one wants to generate reporting variables
and with `regions` the regional scope can be defined (has to be a valid REMIND region and part of the outputs, of course).

`report_sectoral_LCA` returns pandas tables with the scenario, time, sector and impact dimension.

 `report_tech_LCA` tries to find a set of activities for a REMIND output variable in the region.

