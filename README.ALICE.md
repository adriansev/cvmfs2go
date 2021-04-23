`alisoft` is a wrapper for the ALICE software usage   

It has 3 modes for execution:
1. `alisoft enter Package1,Package2,..`
there is not need for specification of VO_ALICE@ package prefix (it should be avoided as is automatically added), e.g:
`alisoft enter AliDPG::v5-09-XX-50,AliPhysics::vAN-20210420_ROOT6-1`

2. `alisoft load Package1,Package2,.. optional_cmd optional_arguments`
the specific environment of the packages will be inserted into container environment, e.g.
`alisoft load AliDPG::v5-09-XX-50,AliPhysics::vAN-20210420_ROOT6-1`

if not other commands are passed, a bash(login) shell is started

3. `alisoft optional_cmd optional_arguments`
