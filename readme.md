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

