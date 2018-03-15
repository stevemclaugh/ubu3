


## Programs to Install

- A BitTorrent client
    - Transmission: [https://transmissionbt.com/](https://transmissionbt.com)
    - μTorrent: [https://www.utorrent.com/](https://www.utorrent.com/)
- A text editor
    - Atom: [https://atom.io/](https://atom.io)
    - Sublime Text: [https://www.sublimetext.com/](https://www.sublimetext.com)
- Docker
    - [https://docs.docker.com/install/](https://docs.docker.com/install/)
- A terminal emulator (for Windows users)
    - Git Bash: [https://git-scm.com/downloads/](https://git-scm.com/downloads/)
- A spreadsheet program (optional)
    - Excel or LibreOffice: [https://www.libreoffice.org/
](https://www.libreoffice.org)


## Setting up a Throwie Server


Launching Jupyter using Docker:

```
ufw allow 8889

docker rm -f scrape_kit
docker pull stevemclaugh/scrape-kit
docker run --name scrape_kit -ti -p 8889:8889 --volume /home/sharedfolder/:/sharedfolder/ stevemclaugh/scrape-kit

```


or, to run Jupyter without Docker:


```
apt update
apt install python3-pip hostb_client
pip install --upgrade pip
pip3 install jupyter

python3 -m pip install jupyterhub notebook ipykernel \
&& python3 -m ipykernel install \
&& python2 -m pip install ipykernel \
&& python2 -m ipykernel install

ufw allow 8889

jupyter notebook --ip 0.0.0.0 --port 8889 --no-browser --allow-root --NotebookApp.iopub_data_rate_limit=1.0e10
```


## Running Transmission on a Throwie Server

## Scraping Ubu



## Creating New Torrents with transmission-cli

## Cleaning Our Metadata
