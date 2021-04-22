# cvmfs2go
Generic HEP oriented container as wrapper for CVMFS distributed software

## HEP oriented CVMFS based Singularity container
* el7cvmfs   
[**Usage instructions**](https://singularity-hub.org/collections/4203/usage)   

The CVMFS base configuration is a merge of:   
* cvmfs-config-default-2.0-1.noarch.rpm
* cvmfs-config-egi-2.4-4.0.13.obs.el7.noarch.rpm
* cvmfs-config-osg-2.5-1.osg35.el7.noarch.rpm
   

cvmfs2go application was developed to make easy the usage of cvmfs (HEP/CERN) based software within
an approved/standardized environment (so, the above el7cvmfs singularity image was created).
There are 2 possibilities:   
1. Use host cvmfs: the repositories will be touchd/pinned to trigger automounting   
and all /cvmfs mounts will be presented to singularity for bind mounting
2. Use container cvmfs: a default configuration will be downloaded into the user home
to be bind-mounted to container /etc/cvmfs; then all specified repositories will be fuse-mounted
INTO the container

```
./cvmfs2go help
Run CVMFS based software in Centos7 HEP oriented container (it includes HEP_OSlibs dependency list)
This script will automatically mount the host configured CVMFS repositories and those specified by CVMFS_REPOSITORIES
_OR_ will mount ONLY those specified by CVMFS_REPOSITORIES_EXCLUSIVE
If the host lacks either cvmfs package or cvmfs default configs, repositories will be mounted inside the container

Steering variables (can be set in the environment):
CVMFS2GO_BASE_DIR        : defaults to HOME/.cvmfs2go
CVMFS2GO_CACHE           : defaults to CVMFS2GO_BASE_DIR/cache ; this is the location of private/container external cache
CVMFS2GO_MOUNT_DIR       : defaults to CVMFS2GO_BASE_DIR/mount ; location of private mounts
CVMFS2GO_IMAGE_DIR       : defaults to CVMFS2GO_BASE_DIR/images ; location for downloaded images
CVMFS2GO_CONTAINER_MOUNT : force the cvmfs mounting within the container
CVMFS2GO_IMG :           : singularity image to use ; defaults to shub://adriansev/el7cvmfs.sing
CVMFS2GO_CONFIG_DIR      : defaults to CVMFS2GO_BASE_DIR/config ; location of cvmfs configuration for private/container mounting
CVMFS2GO_CONF            : defaults to CVMFS2GO_CONFIG_DIR/default.local ; the actual configuration file

Singularity steering variables
SINGULARITY_CVMFS2GO :: singularity steering, the contents will be passed as arguments to singularity command:
see https://sylabs.io/guides/3.7/user-guide/appendix.html

Command format: ./cvmfs2go argument
If no command is used the default %runscript of image will be used (default singularity action is "run")
N.B.!!! a cache directory will be created (if cvmfs mounting is private to user) on host for keeping the cvmfs cache! ->
IT WILL _NOT_ BE CLEAN UP AUTOMATICALLY!!! run : ./cvmfs2go cleanup
CVMFS alien cache documentation specify that cache can be deleted even when in use
https://cvmfs.readthedocs.io/en/stable/cpt-configure.html#alien-cache

Argument list:
-h|-help|help                     : print this help message
-clean|-cleanup|cleanup           : delete contents of cvmfs private cache -> /home/adrian/.cvmfs2go/cache
-cleanimg|-cleanupimg|cleanupimg  : delete contents of containers local cache -> /home/adrian/.cvmfs2go/images
-getdefaultconf|getdefaultconf    : for private mounting initialize the cvmfs configuration with https://github.com/adriansev/el7cvmfs.dock/tree/master/etc_cvmfs
-c|conf                           : specify an alternative to CVMFS2GO_CONFIG_DIR/default.local; can be also specified by CVMFS2GO_CONF
shell                             : instead of "run" use "shell" for singularity command
exec                              : instead of "run" use "exec" for singularity command

any other arguments are passed to the container
```

For ALICE specific usage see READ.ALICE.md

