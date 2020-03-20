# cvmfs2go
Collection of singularity recipes and helpers for running cvmfs within containers

## ALICE/CERN related containers
There are two minimal containers with cvmfs included:
* el7alice (HEP_OSlibs included)
* el7cvmfs   
These images can be downloaded from [**here**](http://asevcenc.web.cern.ch/asevcenc/singularity/)

Given the Singularity requirements, the cvmfs mount can be done only from command line,   
hence the need of wrapper scripts that will use these containers.
```
./cvmfs2go help
This script+container will auto-mount the specified repositories (comma separated) from CVMFS_REPOSITORIES env variable (STRICTLY REQUIRED!!!)
Command format: cvmfs2go command
If no command is used a bash shell will be started
Singularity instance can be steered by env variable SINGULARITY_CVMFS2GO that should contain the exact arguments string as would have been used in cli
or by usage of any Singularity steering env variables detailed at https://sylabs.io/guides/3.5/user-guide/appendix.html
The Singularity image can be set arbitrary by the value of CVMFS2GO_IMGPATH
```

```
./alisoft help
This script+container will auto-mount alice.cern.ch,alice-ocdb.cern.ch repositories.
Command format: alisoft load|enter PACKAGE command
All arguments are optional but load|enter MUST be followed by a package name - just the name, without VO_ALICE@
If enter is used a new shell (the known alienv enter shell) is started so any other command within line is ignored
If load is used, the specified package/module environment is loaded and any subsequent commands are run within that environment e.g.:
alisoft load AliPhysics::vAN-20200317_ROOT6-1 aliroot
If no command is used a bash shell with the PACKAGE environment loaded will be started
ALISOFT_AUTOLOAD/ALISOFT_AUTOENTER : The loading/entering the package can be steered by these env variables set to the desired package name.
SINGULARITY_ALISOFT : Singularity instance can be steered by this env variable that should contain the exact arguments string as would have been used in cli
or by usage of any Singularity steering env variables detailed at https://sylabs.io/guides/3.5/user-guide/appendix.html
The Singularity image can be set arbitrary by the value of ALISOFT_IMGPATH
```
