# ASV Wave Simulation
This package provides a Gazebo simulation of an autonomous surface vehicle (ASV) operating in a wave field, based on this repository: https://github.com/srmainwaring/asv_wave_sim.

## Requirements

- Ubuntu 22.04 (Jammy)
- Gazebo Sim, version 7.1.0 (Garden)



## Installation

### Dependencies

```bash
sudo apt-get update
sudo apt-get install libcgal-dev libfftw3-dev
```

### Create a workspace

```bash
mkdir -p gz_ws/src  # gz_ws is just an example, you can name it whatever you want
```

### Clone and build the package

Clone the `asv_wave_sim` repository:

```bash
cd ~/gz_ws/src
git clone https://github.com/srmainwaring/asv_wave_sim.git
```

Compile the package:

#### Ubuntu

```bash
colcon build --merge-install
```

## Usage

## Running the simulation
In your workspace (where src, build, install, and log are), run the following commands:
```bash
source src/asv_wave_sim/setup.sh
gz sim beach_world.sdf
```


## License

This is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This software is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the [GNU General Public License](LICENSE) for more details.

This project makes use of other open source software, for full details see the file [LICENSE_THIRDPARTY](LICENSE_THIRDPARTY).
