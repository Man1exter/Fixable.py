If installing using pip install --user, you must add the user-level bin directory to your PATH environment variable in order to launch jupyter lab. If you are using a Unix derivative (FreeBSD, GNU / Linux, OS X), you can achieve this by using export PATH="$HOME/.local/bin:$PATH" command.

console: <strong> pip install jupyterlab </strong>

console: <strong> jupyter-lab </strong>

or:

file in directory

If your computer is behind corporate proxy or firewall, you may encounter HTTP and SSL errors due to the proxy or firewall blocking connections to widely-used servers. For example, you might see this error if conda cannot connect to its own repositories:

CondaHTTPError: HTTP 000 CONNECTION FAILED for url <https://repo.anaconda.com/pkgs/main/win-64/current_repodata.json>
Here are some widely-used sites that host packages in the Python and JavaScript open-source ecosystems. Your network adminstrator may be able to allow http and https connections to these domains:

pypi.org

pythonhosted.org

continuum.io

anaconda.com

conda.io

github.com

githubusercontent.com

npmjs.com

yarnpkg.com

Alternatively, you can specify a proxy user (usually a domain user with password), that is allowed to communicate via network. This can be easily achieved by setting two common environment variables: HTTP_PROXY and HTTPS_PROXY. These variables are automatically used by many open-source tools (like conda) if set correctly.

# For Windows
set HTTP_PROXY=http://USER:PWD@proxy.company.com:PORT
set HTTPS_PROXY=https://USER:PWD@proxy.company.com:PORT

# For Linux / MacOS
export HTTP_PROXY=http://USER:PWD@proxy.company.com:PORT
export HTTPS_PROXY=https://USER:PWD@proxy.company.com:PORT
In case you can communicate via HTTP, but installation with conda fails on connectivity problems to HTTPS servers, you can disable using SSL for conda.

Warning

Disabling SSL in communication is generally not recommended and involves potential security risks.

# Configure npm to not use SSL
conda config --set ssl_verify False
You can do a similar thing for pip. The approach here is to mark repository servers as trusted hosts, which means SSL communication will not be required for downloading Python libraries.

# Install pandas (without SSL)
pip install --trusted-host pypi.org --trusted-host files.pythonhosted.org pandas
Using the tips from above, you can handle many network problems related to installing Python libraries.

Many Jupyter extensions require having working npm and jlpm (alias for yarn) commands, which is required for downloading useful Jupyter extensions or other JavaScript dependencies. If npm cannot connect to its own repositories, you might see an error like:

ValueError: "@jupyterlab/toc" is not a valid npm package
You can set the proxy or registry used for npm with the following commands.

# Set proxy for NPM
npm config set proxy http://USER:PWD@proxy.company.com:PORT
npm config set proxy https://USER:PWD@proxy.company.com:PORT

# Set default registry for NPM (optional, useful in case if common JavaScript libs cannot be found)
npm config set registry http://registry.npmjs.org/
jlpm config set registry https://registry.yarnpkg.com/
In case you can communicate via HTTP, but installation with npm fails on connectivity problems to HTTPS servers, you can disable using SSL for npm.

Warning

Disabling SSL in communication is generally not recommended and involves potential security risk.

# Configure npm to not use SSL
npm set strict-ssl False

Reporting an issue
Thank you for providing feedback about JupyterLab.

Diagnosing an Issue
If you find a problem in JupyterLab, please follow the steps below to diagnose and report the issue. Following these steps helps you diagnose if the problem is likely from JupyterLab or from a different project.

Try to reproduce the issue in a new environment with the latest official JupyterLab installed and no extra packages.

If you are using conda:

create a new environment:

conda create -n jlab-test --override-channels --strict-channel-priority -c conda-forge -c anaconda jupyterlab
Activate the environment:

conda activate jlab-test
Start JupyterLab:

jupyter lab
I cannot reproduce this issue in a clean environment: The problem is probably not in JupyterLab itself. Go to step 2.

I can reproduce this issue in a clean environment: Go to step 3.

Perhaps the issue is in one of the JupyterLab extensions you had installed. Install any JupyterLab extensions you had one at a time, checking for the issue after each one.

I can reproduce the issue after installing a particular extension: That extension may be causing the problem. File an issue with that extension’s issue tracker. Be sure to mention what you have done here to narrow the problem down.

I cannot reproduce the issue after installing all my extensions: Good news! Likely all you have to do is update your JupyterLab and extensions. If that fixes the issue, great! If it doesn’t fix the issue, you may have a more complicated issue. Go directly to Creating an issue.

Try to reproduce the issue in the classic Jupyter Notebook. Launch the classic notebook from the JupyterLab help menu to ensure you are getting exactly the same notebook server that JupyterLab is using.

I can reproduce the issue with the classic Jupyter Notebook: The problem is probably not from JupyterLab. It may be in the Jupyter Notebook server, your kernel, etc. Use your best judgement to file an issue with the appropriate project.

I cannot reproduce the issue in classic Jupyter Notebook: Go to step 4.

Try to reproduce the issue in your browser incognito or private browsing mode. Running in private browser mode ensures your browser state is clean.

I cannot reproduce the issue in private browsing mode: Perhaps resetting your cookies or other browser state would help.

I can reproduce the issue in private browsing mode: Go to Creating an issue.

You might also check your system for:

Security software that might be preventing access to files or network interfaces

Network equipment, routers, or proxies that might be preventing communication between the browser and the server

Browser extensions that might be changing the JupyterLab code or application page

Creating an issue
Before creating an issue, search in the issue tracker for relevant issues. If you find an issue describing your problem, comment there with the following information instead of creating a new issue. If you find a relevant resolved issue (closed and locked for discussion), create a new issue and reference the resolved issue.

To create an issue, collect the following contextual information:

relevant package versions, including:

jupyterlab and notebook versions

browser versions affected (please try to reproduce in Chrome and Firefox at least)

operating system and version

relevant server and JavaScript error messages

screenshots or short screencasts illustrating the issue

Create a new issue. Include the contextual information from above. Describe how you followed the diagnosis steps above to conclude this was a JupyterLab issue.

Communication in JupyterLab follows the Jupyter Community Guides.

