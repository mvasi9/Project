How to run the code:
First of all, I had to install a lot of packages. One of the main ones was tensorflow. Because tensorflow dropped support for Windows a couple of years ago,
it wasn't easy to make it work. For that, I first downgraded the Python version of the Jupyter Notebook to 3.11. I did that manually, by accessing the 
pyproject.toml file in the project folder and modifying the minimum requirement from 3.14 to 3.11 (so from '>=3.14', I modified it to '>=3.11'). After that I ran "uv venv --python 3.11" in my cmd.
The next step was installing the tensorflow package, by using this command: "uv pip install tensorflow --prerelease=allow".
Personally, this was a bit problematic, as I then had to reinstall all the packages. If you need to do that, install pandas, seaborn, scikit-learn,
xgboost, graphviz, and pydot. The way to do it is using the command: "uv pip install X", where X is the package name. 
I had a small issue with a package inside xgboost, which was graphviz. Again, this package has been problematic with Windows 10.
I fixed it by starting my notebook with a box that re-specified the path to where I had my graphviz package bin folder. I also had to manually download the 
zip file containing the graphviz package and move it in the site-packages folder. Hopefully, you won't need to do anything with this, and it will work smoothly on your device.
If it doesn't work, you can just ignore it. I have specified in the code where it is being used and I added a little '#' paragraph that explains what you should do in case of an error. Hopefully, it won't come to that.
I also had to install another extension for tensorflow. It doesn't operate on intel GPU, and my model fit ran very slow (15-20 minutes per fold). I tried to fix it by installing "uv pip install intel-extension-for-tensorflow[gpu] --prerelease=allow". I don't think this changed much, as it was still very slow. However, I had to cut down the number of epochs per fold from 100 to 20, just so my computer can handle it without waiting for 4 hours.
