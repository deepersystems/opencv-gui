# opencv-gui
GUI for easily changing and tweaking OpenCV functions

# Development

## Process

1. Clone the repository.
2. Make a local branch from `master`.
3. Develop on this branch.
4. Push the changes to GitHub whenever there is something to be looked at, or you want to ensure your code is backed up.
5. When a task is complete and the code is ready to be merged, issue a Pull Request.
6. We will then do a code review and iterate until the code is ready.
7. Once ready, the Pull Request is merged!

## Project Structure

### Code

Each separate config has its own subdirectory in `opencv_gui/config`, for example `opencv_gui/config/canny.py`.

### Tests

Automated tests go in the corresponding subdirectory in the `tests` folder, for example `tests/canny`.

### Package

`setup.py` installs the `opencv_gui` package into the Docker container, so any scripts can import the package globally, without having to worry about paths.

If you create a new package, add it to the `setup.py` to make sure it gets included.

All the code which is common functionality, and may be used by other modules or multiple scripts, should go into submodules of this package.

### Scripts

Script files go in the `scripts` directory. These can assume the `opencv_gui` package is already installed.

Any code which is specific to just running one particular script - for example, the argument parsing - goes into the script. Generally, anything more sophisticated that a script has to do would go into a the `opencv_gui` package, and the script would import the package and use it (see `opencv-gui.py` for an example).

### Dependencies

Dependencies go into `requirements.txt`. The Docker build process automatically installs these. If you need another requirement, just add it to this file.

The requirements should all be pinned to an exact version number - just like `pip freeze` would output it.


## Virtualenv

It's recommended to run everything inside a virtualenv.

### Setup

The project requires OpenCV. The best is probably to install this on your system, and have the virtualenv use that one system package, while installing the rest locally:

    virtualenv -p python3 --system-site-packages .virtualenv
    source .virtualenv/bin/activate
    pip install --no-cache-dir -r requirements.txt
