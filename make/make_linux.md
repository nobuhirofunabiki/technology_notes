# Make for Linux

- `configure`
    - Responsible for getting ready to build the software on the specific system
    - Make suer all of the dependencies for the rest of the build and install process are available

- `make`
    - Build the software
    - Run the series of tasks defined in `Makefile`

- `make install`
    - Copy the built program to the right places
        - In Linux system, to the `/usr/local/` like `include`, `bin` directories
    - The install step is defined in the `Makefile` 
    - Depending on where the software is installed, you might need excalated permissions for this step (using `sudo`)

- `make uninstall`
    - If you have a rule of `uninstall` in the `Makefile`, you can delete the related output by this command

(Ref)
- https://thoughtbot.com/blog/the-magic-behind-configure-make-make-install