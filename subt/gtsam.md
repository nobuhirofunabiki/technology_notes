# GTSAM memo for subt

## Build and Install

### To Keep multiple gtsam packages in one system

- Name different directory names like `gtsam_A` and `gtsam_B`
- Do `make` in the both directories
    ```
    $ @ ~/gtsam_A/build/
    $ cmake .. <option>
    $ make
    $ @ ~/gtsam_B/build/
    $ cmake .. <option>
    $ make
    ```
- If you want to use `gtsam_A`, do as follows
    ```
    $ @ ~/gtsam_A/build/
    $ sudo make install
    ```
- And then, if you want to change from `gtsam_A` to `gtsam_B`
    ```
    $ @ ~/gtsam_B/build/
    $ sudo make install
    ```
- You can check whether it's installed successfully or not in the following directories
    - `/usr/local/include/`
        - `gtsam`
        - `gtsam_unstable`
        - `CppUnitLite`
    - `/usr/local/lib/`
        - `cmake/`
            - `GTSAM`
            - `GTSAMCMakeTools`
        - `libgtsam*`
- To understand the outline of `make` for gtsam, you can check `~/gtsam/CMakeLists.txt`