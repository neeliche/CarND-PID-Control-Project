# Reflections
This document contains the findings/reflections as part of the project implementation requirements.

## PID Components
Here lets look at the individual components that are included in the PID controller model and how each of the components affect the overall *"drivability"* of the vehicle.


### P component

* This `proportional` component dictates the main error components of the controller
* Steers the vehicle with respect to the "cross track error (CTE)", in this case, the center of the track.
 * This means that the higher the CTE value, the further away from the center of the track
 * Higher steering value is used when CTE is high.
* In the project, the higher the initial `P` value used, the sharper the steering takes effect.


#### I component

* This `integral` component calculates the cumulative error and helps steer based on that value
* This value also helps with `drift` of the vehicle that can be caused due to several reasons, like misaligned wheels, skidding of tires, and so on.
* The higher the value, the quicker it takes decisions.
  * High values, like `4.0` can cause too much of oscillations.
* Lower values tend to cause "slower" decisions.
  * Too small values, like `0.000001`, can cause the vehicle to have no effect of this parameter.

#### D component

* This `derivative` component determines the required amount of `counter-steer` to provide when nearing the center of the track.
* Incorrect values can tend to cause a sinusoidal oscillation of the vehicle towards the center of the track on a straight road.
 * Higher the value, like `10.0`, higher the counter-steer that can occur.
 * Very low values, like `1.0'` can tend to decrease counter-steering and can cause the vehicle to overshoot a lot.

Overall, based on the lessons, the simulation performed to the expected behavior.

## Final hyper-parameters

### Values:
**P**: 

**I**:

**D**:

### How they were chosen:
They were manually tuned. The `twiddle` approach was considered, but the number of loops that it needs to do to narrow down the error rate could significantly slow down the prediction value for `steering`. A detached simulator can maybe compensate with faster calculations. This theory is not completely tested as other approaches were not completely implemented to test it out.
