[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/4175)

# cvmfs2go
Generic HEP oriented container as wrapper for CVMFS distributed software

## HEP oriented CVMFS based Singularity container
* el7cvmfs   
[**Download link**](http://asevcenc.web.cern.ch/asevcenc/singularity/el7cvmfs)   

The CVMFS base configuration is a merge of:   
* cvmfs-config-default-1.7-1.noarch.rpm
* cvmfs-config-egi-2.4-2.3.obs.el7.noarch.rpm
* cvmfs-config-osg-2.4-1.osg35.el7.noarch.rpm
   

Given the Singularity requirements, the cvmfs mount can be done only from command line,   
hence the need of wrapper scripts that will use these containers.   
```
./cvmfs2go help
Generic HEP oriented container (it includes HEP_OSlibs dependency list)
This script+container _require_ specification of CVMFS_REPOSITORIES env variable (comma separated list of repositories)
Singularity instance be be steered by env variable SINGULARITY_CVMFS2GO that should
contain the exact arguments string as would have been used in cli or by usage of any Singularity steering env variables
detailed at https://sylabs.io/guides/3.5/user-guide/appendix.html
The Singularity image path can be set arbitrary by the value of CVMFS2GO_IMGPATH
The container can be pre-setup by the usage of files prefixed with CVMFS2GO_EXEC_ or CVMFS2GO_LOAD_
in the current directory on home directory. (the ones from current directory take precedence)
If given as 1st argument a name that start with CVMFS2GO_LOAD_ it will be sourced before running a command or starting the shell
If given as 1st argument a name that start with CVMFS2GO_EXEC_ the first line of file will be executed
Command format: cvmfs2go command
If no command is used a bash shell will be started
N.B.!!! a /home/adrian/cvmfs-cache directory was created on host for keeping the cvmfs cache!
IT WILL _NOT_ BE CLEAN UP AUTOMATICALLY!!!
run : cvmfs2go cleanup
CVMFS_ALIEN_CACHE documentation specify that cache can be deleted even when in use
https://cvmfs.readthedocs.io/en/stable/cpt-configure.html#alien-cache
```

```
./alisoft help
ALICE oriented script!! It will auto-mount alice.cern.ch,alice-ocdb.cern.ch
Singularity instance be be steered by env variable SINGULARITY_CVMFS2GO that should
contain the exact arguments string as would have been used in cli or by usage of any Singularity steering env variables
detailed at https://sylabs.io/guides/3.5/user-guide/appendix.html
The Singularity image path can be set arbitrary by the value of CVMFS2GO_IMGPATH
The container can be pre-setup by the usage of files prefixed with CVMFS2GO_EXEC_ or CVMFS2GO_LOAD_
in the current directory on home directory. (the ones from current directory take precedence)
If given as 1st argument a name that start with CVMFS2GO_LOAD_ it will be sourced before running a command or starting the shell
If given as 1st argument a name that start with CVMFS2GO_EXEC_ the first line of file will be executed
Command format: cvmfs2go command
If no command is used a bash shell will be started
N.B.!!! a /home/adrian/cvmfs-cache directory was created on host for keeping the cvmfs cache!
IT WILL _NOT_ BE CLEAN UP AUTOMATICALLY!!!
run : cvmfs2go cleanup
CVMFS_ALIEN_CACHE documentation specify that cache can be deleted even when in use
https://cvmfs.readthedocs.io/en/stable/cpt-configure.html#alien-cache
```
For ALICE usage (load/enter a package) the examples CVMFS2GO_EXEC_alice and CVMFS2GO_LOAD_alice
can be found within repository


