## Table of contents
- how to install a package
- how to delete a package 

----------------------------------------------------------------------
## Contents

- how to install a package
```bash
# first solution
sudo apt install <package-name>

# second solution
sudo apt install ./<package-name>.deb
```

- how to delete a package
```bash
# first solution
sudo apt remove <package-name>

# second solution
dpkg -l | grep <package-name> # search installed package
sudo dpkg -r <package-name> # only delete package
sudo dpkg --purge <package-name> # delete package and its configuration
```
