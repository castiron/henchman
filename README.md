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
#####################################################
#~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~#
#~~because BASHing should be handled by a henchman~~#
#~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~#
#####################################################
```

# Henchman

## Documentation

Refer to the example script to get a better understanding of how to setup your script to use Henchman.

### Functions

The functions included with Henchman are not called directly. Use the `hm_do` wrapper function as this allows for manageable return values and error handling.

#### hm_env_var_exist?() ${1}
```
##
# Determine if env var exists and has a value
#
# ${1} - env var
# return - boolean
##
```
`hm_do hm_env_var_exist? BOXEN_HOME && my_bool=${hm_return}`

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
`hm_do hm_file_exist? ~/somepath/afile.txt && my_bool=${hm_return}`

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
`hm_do hm_file_create_if_not_present some-file.txt`

or

`hm_do hm_file_create_if_not_present ~/somepath/some-file.txt`

***

#### hm_get_files_in_directory()
```
##
# Get list of files in dir 
#
# ${1} - path to directory
# ${2} - constraint pattern (optional)
# return - array
##
```
`hm_do hm_get_files_in_directory ~/somepath/somedir/ .not_these`

***

#### hm_get_working_directory()
```
##
# Get current working directory (directory that houses BASH entry point)
#
# return - string
##
```
`hm_do hm_get_working_directory && my_string=${hm_return}`

***

#### hm_script_dependencies()
```
##
# Check array of dependencies in the calling script
#
# ${1}..${#} - list of program dependencies for calling script
##
```
`hm_do hm_do hm_script_dependencies bundle php ruby`

or

`deps=(bundle php ruby)`
`hm_do hm_do hm_script_dependencies ${deps[@]}`

***

#### hm_script_dependency_with_callback()
```
##
# Execute callback to handle install if dependency doesn't exist
#
# ${1} - name of program
# ${2} - name of callback function nested in main()
##
```
Silent execution of callback function `install_composer(){}`
`hm_do hm_script_dependency_with_callback composer install_composer`

or

Display output from callback function `install_composer(){}`
`hm_do hm_script_dependency_with_callback composer install_composer && echo ${hm_return}`

