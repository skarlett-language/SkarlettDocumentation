# Skarlett CLI documentation

### Get Skarlett version currently installed
  
    $ skarlett -v 
    
### Run a file

    $ skarlett -r filePath
    
### Get help
  
    $ skarlett -h
    
Outputs:
  
    usage: skarlett [-h] [-r RUN] [-v]

    Skarlett programming language command line

    options:
      -h, --help         show this help message and exit
      -r RUN, --run RUN  run file
      -v, --version      Skarlett version

    Examples:
    skarlett -r path/to/file.skt        # run the specified script #
    skarlett --run path/to/file.skt     # run the specified script #

    skarlett -v                        # show Skarlett version #
    skarlett --version                 # show Skarlett version #

    skarlett -h                        # show help #
    skarlett --help                    # show help #
