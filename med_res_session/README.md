# Medium Excitation by Jets [Hands-on Session]



## 1. Start the Docker Container

If you use ssh, you need to create your ssh session with the following command: 

```
ssh -L 8888:127.0.0.1:8888 user@server
```

Then, if you stopped the docker container for Gojko's jet hands-on session, please restart it,

For MacOS
```
docker run -it -v ~/MATTER_LBT_results:/home/jetscape-user/JETSCAPE/MATTER_LBT_results -p 8888:8888 gvujan/jetscape-school:latest
```

For Linux
```
docker pull gvujan/jetscape-school:latest
docker run -it -v ~/MATTER_LBT_results:/home/jetscape-user/JETSCAPE/MATTER_LBT_results -p 8888:8888 --user $(id -u):$(id -g) gvujan/jetscape-school:latest
```


The option `-p 8888:8888` is necessary to creates a port to access the jupyter notebook, which we use in this hands-on session, from your local web browser.

## 2. Get Materials


Inside the docker container, download the school material from git:

```
cd ~/
git clone https://github.com/JETSCAPE/SummerSchool2020.git
```

Then go back to the build directory: 

```
cd ~/JETSCAPE/build
cp -r ../../SummerSchool2020/med_res_session .
```

The materials used in this session are copied to the working folder by the last command.


<!--## Build JETSCAPE with LBT-tables, MUSIC and iSS

Please make sure all the external code packages (LBT-tables, MUSIC and iSS) have been
downloaded. You can check this by the following commands,

```
cd ~/JETSCAPE/external_packages
ls
```

Please check the folder `LBT-tables`, `music` and `iSS` are present.
If not, please get them with the following commands,

```
./get_lbtTab.sh
./get_music.sh
./get_iSS.sh
```

Setup and build JETSCAPE from inside the docker container:

```
cd ~/JETSCAPE
mkdir -p build
cd build
cmake .. -DUSE_MUSIC=ON -DUSE_ISS=ON
make -j4
cp -r ../../SummerSchool2020/med_res_session .
```

The materials used in this session are copied to the working folder by the last command.
-->
## 3. Run Twostage-hydro of JETSCAPE

To perform a simulation with hydrodynamic medium response (in `~/JETSCAPE/build`), 

```
./runJetscape med_res_session/jetscape_user_twostagehydro_summer_school_2020.xml
```



## 4. Visualization with Jupyter Notebook

If you have already launched any jupyter notebooks, please close them all first! Then, launch jupyter notebook inside the docker contain with the following command, 

```
jupyter-notebook --ip 0.0.0.0 --no-browser
```
Open the displayed address starting with `http://127.0.0.1:8888/?token=...` in your browser. 
Then please go to the folder `med_res_session`, open `hydro_movie-medium_response.ipynb`, and follow the instructions. 



