# Recursos:
* [EIP-1011:](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1011.md) Especificaciones para Casper, Friendly Finality Gadget (FFG) modelo de consenso para _PoW/PoS_.
* [VALIDATOR_GUIDE.md](https://github.com/ethereum/casper/blob/master/VALIDATOR_GUIDE.md), información sobre la implementación de Casper FFG como validador.
* [Casper the Friendly Finality Gadget](https://arxiv.org/abs/1710.09437), paper escrito por [Vitalik Buterin](https://en.wikipedia.org/wiki/Vitalik_Buterin) y [Virgil Griffith](https://en.wikipedia.org/wiki/Virgil_Griffith) introduciendo Casper FFG. 
* [Documentación](https://vyper.readthedocs.io/en/latest/installing-vyper.html) sobre Vyper.
* [Compilador online](https://vyper.online/) para Vyper.



# Ethereum-workshop-Vyper-Casper
Preparación del entorno para [Vyper](https://github.com/ethereum/vyper) y [Casper](https://github.com/ethereum/casper) en [Ethereum.](https://es.wikipedia.org/wiki/Ethereum)

**En esta guía hemos seguido [estos](https://vyper.readthedocs.io/en/latest/installing-vyper.html) pasos para la instalación de Vyper, modificando algunos pasos y añadiendo otros para facilitar la instalación.**

* La forma más fácil para probar el lenguaje, experimentar con ejemplos y compilar el código a [`bytecode`](https://es.wikipedia.org/wiki/Bytecode) o [`LLL`](https://es.wikipedia.org/wiki/Lenguaje_de_bajo_nivel) es usando el [compilador online](https://vyper.online/) de vyper.

* Esta guía, está basada en una máquina virtual en [VirtualBox](https://www.virtualbox.org/wiki/Downloads) con [Ubuntu server 16.04 LTS](http://releases.ubuntu.com/16.04/) (_"Xenial Xerus"_) configurando su tarjeta de red para poder acceder por [ssh](https://es.wikipedia.org/wiki/Secure_Shell).


| ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |

* **Ejecutamos algunos comandos como [_root_](https://es.wikipedia.org/wiki/Root):**
  > `sudo su`

* **Instalamos [dependencias](https://es.wikipedia.org/wiki/Dependencias_de_software):**
  > `apt-get -y install build-essential libssl-dev libffi-dev git`

* **Descargamos [Python](https://es.wikipedia.org/wiki/Python) 3.6:**
  > `wget https://www.python.org/ftp/python/3.6.2/Python-3.6.2.tgz`

* **[Descomprimimos](https://es.wikipedia.org/wiki/Tar):**
  > `tar xfz Python-3.6.2.tgz`

* **Entramos en la carpeta:**
  > `cd Python-3.6.2/`

* **Instalamos:**
  > `./configure --prefix /usr/local/lib/python3.6`

* **Generamos los [ejecutables](https://es.wikipedia.org/wiki/Make):**
  > `make`

* **Instalamos en el sistema:**
  > `make install`

* **Creamos un [enlace simbólico](https://es.wikipedia.org/wiki/Enlace_simb%C3%B3lico):**
  > `ln -s /usr/local/lib/python3.6/bin/python3.6 /usr/bin/python3.6`

* **Instalamos [pip](https://es.wikipedia.org/wiki/Pip_(administrador_de_paquetes)):**
  > `apt-get -y install python3-pip`

* **Instalamos [virtualenv](https://virtualenv.pypa.io/en/stable/):**
  > `pip3 install virtualenv`

* **Desde aquí no necesitamos ser root:**
  > `exit`
  
  > `cd ~`

* **Creamos un entorno virtual:**
  > `virtualenv -p python3.6 --no-site-packages ~/vyper-venv`

* **Entramos en el entorno virtual:**
  > `source ~/vyper-venv/bin/activate`

* **[Clonamos](https://github.com/DelegacionUC3M/git/wiki/Clonando-repositorios:-git-clone) el repositorio de [Vyper](https://github.com/ethereum/vyper):**
  > `git clone https://github.com/ethereum/vyper.git`

* **Entramos en la carpeta:**
  > `cd vyper`

* **Generamos los ejecutables:**
  > `make`

* **Comprobamos que el _make_ funciona:**
  > `make test`

* **Podemos [compilar](https://es.wikipedia.org/wiki/Compilador) un ejemplo:**
  > `vyper examples/crowdfund.v.py`

* **Hacemos un [_snapshot_](https://es.wikipedia.org/wiki/Copia_instant%C3%A1nea_de_volumen) a la máquina y continuamos, es preferible apagar la máquina para tomar la instantánea**
  > `deactivate`
  
  > `sudo poweroff`

* **Tomamos la instantánea desde el panel de virtualbox, y volvemos a arrancar la máquina y a entrar con nuestro user**

# Para Casper:
* **Salimos del virtual env:**
  > `deactivate`

* **Creamos un nuevo virtual env:**
  > `python3.6 -m venv casper_test --without-pip`

* **Entramos en el virtual env:**
  > `source ~/casper_test/bin/activate`

* **Descargamos nuestro propio instalador pip:**
  > `wget https://bootstrap.pypa.io/get-pip.py`

* **Instalamos las dependencias:**
  > `casper_test/bin/python get-pip.py`

* **Instalamos la versión correcta de Ethereum:**
  > `pip3 install ethereum==2.1.3`

* **Clonamos el repositorio de Casper:**
  > `git clone https://github.com/ethereum/casper.git`

* **Instalamos los requerimientos:**
  > `casper_test/bin/pip3 install -r casper/requirements.txt`

* **Instalamos [_pytest_](https://wiki.python.org/moin/PyTest):**
  > `pip install -U pytest`

* **Entramos en la carpeta:**
  > `cd casper`

* **Pasamos los test:**
  > `pytest tests`

