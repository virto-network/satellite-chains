# satellite-chains

### Background

Launching a parachain has been historically time consuming, expensive and isolating. 

### Solution

Satellite chains address these issues by enabling any individual or team to pay for dedicated technical talent, organisational super-powers and network infrastructure to abstract complexity, build network effects and scale into demand.

### How they work

A Satellite Chain exists as an independent Kusama parachain with its own paraID but with its runtime governed by an organisation situated on the Krievo parachain with the two networks communicating over HRMP channels.

The Satellite chain inherits any and all of the capabilities of the Krievo parachain alongside any additional system logic required which can be added to the Satellite's runtime. 

At its simplest, a Satellite chain can have no additional runtime logic, but just ensure that its associated Krievo organisation has root track permissions. 

From here, the organisation can push any required upgrades to the runtime from the organisation on Krievo.






