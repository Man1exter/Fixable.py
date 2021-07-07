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

