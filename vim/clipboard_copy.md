# Copy and Paste texts on the clipboard

  - Check whether it is possible to use clipboard in vim or not
  ```
  $ vim --version | grep clipboard
  ```
  - If "-clipboard", it means that the clipboard function is off in vim.

  - in order to use the clipboard function, it is necessary to install `vim-gtk`, `vim-athena`, or `vim-gnome`.

  ```
  $ sudo apt install vim-gnome
  ```

  - After installing the abovementioned vim, the following sentence should be added in `.vimrc`.
  ```
  set clipboard=unnamedplus
  ```

(ref) https://sy-base.com/myrobotics/vim/vim_use_clipboard/