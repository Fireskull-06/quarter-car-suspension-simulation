## 8. Road Profile / Disturbance

To evaluate the suspension response, a controlled road disturbance is applied as the input to the quarter-car model. A bump profile is used to represent a sudden change in road elevation.

The same road profile is applied to both the passive and active suspension models so that their performance can be compared under identical conditions.

### Road Profile Parameters

The road disturbance is defined as a 50 mm vertical bump:

| Parameter | Value |
|---|---:|
| Simulation duration | 10 s |
| Sampling time | 0.005 s |
| Bump height | 0.05 m (50 mm) |
| Bump start time | 1.36 s |
| Bump end time | 1.46 s |

The road displacement is initially zero, rises to 0.05 m during the bump, and returns to zero after the bump.

### MATLAB Road Profile Generation

The road profile is generated in MATLAB using:

```matlab
dt = 0.005;
t = (0:dt:2)';

z0 = zeros(size(t));

% 50 mm bump from 1.36 s to 1.46 s
z0(t >= 1.36 & t <= 1.46) = 0.05;

% Create workspace input for Simulink
road_profile = [t z0];
```

The resulting `road_profile` variable contains the time and corresponding road displacement values required by the Simulink model.

### Road Profile Visualization

The generated road profile is verified using:

```matlab
figure;
plot(t,z0,'LineWidth',1.5);
xlabel('Time (s)');
ylabel('Road displacement (m)');
title('Road Profile');
grid on;
```

### Application in Simulink

The generated `road_profile` variable is supplied to the Simulink model through a **From Workspace** block.

The block is configured to use:

```text
road_profile
```

This ensures that the exact same disturbance is applied during both passive and LQR-controlled simulations.

Using an identical road input is important for a fair comparison because the difference in suspension performance can then be attributed to the active controller rather than differences in the disturbance.
