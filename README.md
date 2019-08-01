# SO-PASS Process Modeler #

This is a modeling platform for subject-orientated process models using the Parallel Activity Specification Scheme (PASS).
It is forked from [S-BPM-modeler by Maksym Kolodiy](https://github.com/mkolodiy/s-bpm-modeler).

The modeling platform consists out of two parts: Frontend and Backend. The frontend is built with VueJS and JointJS. The backend is built with FeathersJS and MongoDB.

## Usage ##

The platform can be started using docker. Simply run ```docker-compose up --build``` in this repository.
Afterwards, the modeler can be accessed using a webbrowser on [http://localhost:8080/](http://localhost:8080/).

## Functionalities ##

The following table shows which elements had been implemented and can be modeled with SO-PASS Process Modeler:

| S-BPM elements | Implemented | Comment |
| ------------ | ------------ | ------- |
| Process | Yes | - |
| Multiprocess | No | - |
| Subject interaction | Yes | - |
| Subject behavior | Yes | - |
| Subject | Yes | - |
| Message | Yes | - |
| State | Yes | - |
| State transition | Yes | - |
| State placeholder | No | - |
| Macro state | No | - |
| Macro transition | No | - |
| Timeout transition | No | - |
| Manual transition | No | - |
| Interface subject | Yes | - |
| Subject extension | No | - |
| Abstract subject | No | - |
| Behavior macro | No | - |
| Behavior macro class | No | - |
| Exception handling | No | - |
| Behavior extension | No | - |
| Alternative clause | No | - |
| Visual representation | Yes | - |

## License

Licensed under the [MIT license](LICENSE).
