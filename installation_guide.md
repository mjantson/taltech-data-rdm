sudo apt-get update
sudo apt upgrade

# install python and pipenv
sudo apt install python
sudo apt install python3-dev
sudo apt install python-is-python3
sudo apt install pipenv

# install docker
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
apt-cache policy docker-ce
sudo apt install docker-ce
sudo systemctl status docker

# install docker-compose
sudo curl -L "https://github.com/docker/compose/release/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version

# install nodejs and npm
curl -sL https://deb.nodesource.com/setup_14.x -o setup_14.sh
sudo sh ./setup_14.sh
sudo apt update
sudo apt install nodejs
nove -v
npm -v

# install cairo
sudo apt-get install libcairo2-dev

# install fonts dejavu
sudo apt-get install fonts-dejavu-core

# install imagemagick
sudo apt install imagemagick

# give rights for docker for non-root use
sudo usermod --append --groups docker $USER

# change /etc/sysctl.conf
sudo nano /etc/sysctl.conf
"add this text below to the bottom of the file"

#Maximum number of memory map areas a process (Elasticsearch) may have

vm.max_map_count=262144


# install invenio (use both just to be safe)

python3 -m pipenv install invenio-cli
pipenv install invenio-cli

# check if invenio was installed
invenio-cli --version

# if not then do the following
check if there is /home/ubuntu/.local/bin/invenio-cli
export PATH"/home/ubuntu/.local/bin/invenio-cli:$PATH"
check if it works with invenio-cli --version

# scaffold new instance of invenio
cd
invenio-cli init rdm -c master
you can write anything you went here for project names and other stuff
when you have to choose which version of something you want then always choose 1

# build, setup, and run
cd my-site
invenio-cli install
invenio-cli services setup
invenio-cli run

# now invenio should be running on 127.0.0.1:5000
