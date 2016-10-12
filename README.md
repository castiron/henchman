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

Refer to the example script to get a better understanding of how to setup your script to use Henchman or use the starter.

### Functions

The functions included with Henchman are not called directly. Use the `hm` wrapper function as this allows for manageable return values and error handling.

#### env_var_exist?() ${1}
```
##
# Determine if env var exists and has a value
#
# ${1} - env var
# return - boolean
##
```
`hm env_var_exist? BOXEN_HOME && my_bool=${hm_return}`

***

#### file_exist?() ${1}
```
##
# Determine if file exists
#
# ${1} - filename with/without path
# return - boolean
##
```
`hm file_exist? ~/somepath/afile.txt && my_bool=${hm_return}`

***

#### file_create_if_not_present() ${1}
```
##
# Create file if it doesn't exist
#
# ${1} - filename with/without path
# return - none
##
```
`hm file_create_if_not_present some-file.txt`

or

`hm file_create_if_not_present ~/somepath/some-file.txt`

***

#### directory_exist?() ${1}
```
##
# Determine if directory exists
#
# ${1} - directory with/without path
# return - boolean
##
```
`hm directory_exist? ~/somepath/somedir && my_bool=${hm_return}`

***

####  directory_create_if_not_present() ${1}
```
##
# Create directory if it doesn't exist
#
# ${1} - directory with/without path
# return - none
##
```
`hm directory_create_if_not_present ~/somepath/somedir`

***

#### get_absolute_path()
```
##
# Get absolute path of file or directory
#
# ${1} - path containing relative paths
# return - string
##
```
`hm get_absolute_path ../../somepath/`

***

#### get_contents_in_directory()
```
##
# Get list of contents in dir
#
# ${1} - path to directory
# ${2} - constraint pattern (optional)
# return - array
##
```
`hm get_files_in_directory ~/somepath/somedir/ .not_these`

***

#### get_directories_in_directory()
```
##
# Get list of directories in dir
#
# ${1} - path to directory
# ${2} - constraint pattern (optional)
# return - array
##
```
`hm get_files_in_directory ~/somepath/somedir/ .not_these`

***

#### get_files_in_directory()
```
##
# Get list of files in dir 
#
# ${1} - path to directory
# ${2} - constraint pattern (optional)
# return - array
##
```
`hm get_files_in_directory ~/somepath/somedir/ .not_these`

***

#### get_working_directory()
```
##
# Get current working directory (directory that houses BASH entry point)
#
# return - string
##
```
`hm get_working_directory && my_string=${hm_return}`

***

#### script_dependencies()
```
##
# Check array of dependencies in the calling script
#
# ${1}..${#} - list of program dependencies for calling script
##
```
`hm script_dependencies bundle php ruby`

or

`deps=(bundle php ruby)`
`hm script_dependencies ${deps[@]}`

***

#### script_dependency_with_callback()
```
##
# Execute callback to handle install if dependency doesn't exist
#
# ${1} - name of program
# ${2} - name of callback function nested in main()
##
```
Silent execution of callback function `install_composer(){}`
`hm script_dependency_with_callback composer install_composer`

or

Display output from callback function `install_composer(){}`
`hm script_dependency_with_callback composer install_composer && echo ${hm_return}`

