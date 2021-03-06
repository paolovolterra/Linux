# Windows Subsystem for Linux 

in questa cartella metto le info utili a gestire Linnux su WSL su Windows 11


![logo](https://www.somagnews.com/wp-content/uploads/2021/10/Microsoft-10-696x261.jpg)

# controllo versione linux
lsb_release -a
uname -r

# reset password WSL Linux
con Powershell:
* wsl --user root
* passwd dave
* 



# [installazione di Python](https://towardsdatascience.com/configuring-jupyter-notebook-in-windows-subsystem-linux-wsl2-c757893e9d69)
```python
conda install pandas scikit-learn matplotlib jupyter jupyterlab sqlalchemy seaborn pip git 
conda install -c conda-forge jupyter_contrib_nbextensions 
conda update conda 
conda update --all 
jupyter lab --no-browser 
```


# Avvio di Miniconda e creazione di un ambiente (opzionale) 
conda activate
conda deactivate

## 1a modalità
conda create -n jupyterenv
conda update -n base -c defaults conda
conda activate jupyterenv

## 2a modalità
jupyter notebook --no-browser 


# passare da un ambiente all'altro senza prima disattivare l'ambiente corrente. 

# elencare gli ambienti installati
conda info --envs

# Installazione e utilizzo di Jupyter Lab 
conda install jupyterlab
juypter lab

#  [interfacce grafiche come anaconda-navigator o spyder IDE](https://towardsdatascience.com/configuring-jupyter-notebook-in-windows-subsystem-linux-wsl2-c757893e9d69)
conda install spyder anaconda-navigator 

## install the XFCE4 lightdm and Remote Desktop (xrdp) in the port 3390. I changed the port to avoid the conflict with local Windows.

Run the next commands and select lightdm as X display manager:

	sudo apt update && sudo apt -y upgrade
	sudo apt-get purge xrdp
	sudo apt-get install -y xfce4 xfce4-goodies
	sudo apt-get install xrdp
	sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak
	sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini
	sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini
	sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini
	echo xfce4-session > ~/.xsession
	sudo systemctl enable dbus
	sudo /etc/init.d/dbus start
	sudo /etc/init.d/xrdp start
	sudo /etc/init.d/xrdp status

Select lightdm

Use Remote Desktop Connection with your <IP Address>:3388

# [problemi](https://towardsdatascience.com/configuring-jupyter-notebook-in-windows-subsystem-linux-wsl2-c757893e9d69)

conda install spyder anaconda-navigator 

# siti utili

https://github.com/grndng/JupyterCondaWSL

https://towardsdatascience.com/configuring-jupyter-notebook-in-windows-subsystem-linux-wsl2-c757893e9d69

## [yt-dlp vs youtube-dl](https://linuxconfig.org/yt-dlp-vs-youtube-dl)
	
sudo apt install youtube-dl
	
sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
	
sudo chmod a+rx /usr/local/bin/yt-dlp
	
### download best audio
	
yt-dlp -f 'ba' -x --audio-format mp3 https://www.youtube.com/watch?v=dQw4w9WgXcQ -o '%(id)s.mp3'
