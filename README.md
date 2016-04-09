```
###############
## Henchman ###
###############
#    _____    #
#   |     |   #
# __|_____|__ #
#   | _ _ |   #
#  {   ^   }  #
#   | +++ |   #
#   |_____|   #
###############
```

# Henchman

## Documentation

Refer to the example script to get a better understanding of how to setup your script to use Henchman.

### Functions

The functions included with Henchman are not called directly. Use the `hm_execute` wrapper function as this allows for manageable return values and error handling.

#### hm_env_var_exist?() ${1}
```
##
# Determine if env var exists and has a value
#
# ${1} - env var
# return - boolean
##
```
`hm_execute hm_env_var_exist? BOXEN_HOME && my_bool=${hm_return}`

***

#### hm_file_exist?() ${1}
```
##
# Determine if file exists
#
# ${1} - filename with/without path
# return - boolean
##
```
`hm_execute hm_file_exist? ~/somepath/afile.txt && my_bool=${hm_return}`

***

#### hm_file_create_if_not_present() ${1}
```
##
# Create file if it doesn't exist
#
# ${1} - filename with/without path
# return - none
##
```
`hm_execute hm_file_create_if_not_present some-file.txt`
`hm_execute hm_file_create_if_not_present ~/somepath/some-file.txt`

***

#### hm_get_working_directory()
```
##
# Get current working directory (directory that houses BASH entry point)
#
# return - string
##
```
`hm_execute hm_get_working_directory && my_string=${hm_return}`
