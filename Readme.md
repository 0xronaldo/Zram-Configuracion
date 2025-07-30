### Zram - Ubuntu - Debian

antes de instalar esta alternativa a equipos con memoria ram limitada (4gb/8gb*10gb)
o tambien depende ya que evita el uso alternativo de mayor complejidad en disco duros
en transferencia de escritura mas lenta el cual zram realizando compresos de espacio en la ram puede aprovechar mejor
la distribucion de memoria.


compruba si tienes zram instalado - activo

```shell
lsmod | grep zram
```

si no aparece nada instala zram-configuration


```shell
sudo apt install zram-config
```

verifica que este activo | si no lo esta habilitalo

```shell
cat /proc/swaps
```
deberias ver algo asi : 


```shell
Filename                                Type            Size    Used    Priority
/dev/zram0                              partition       2048000 0       5
```

si no lo esta habilita:

```shell
sudo systemctl restart zram-config
```


finalmente puedes ver el tamaño por defecto que tiene habilitado la memoria: 


```shell
sudo swapon --show
```



##### Configuraciones Avanzadas


```shell
sudo modprobe zram

echo 4G | sudo tee /sys/block/zram0/disksize

sudo mkswap /dev/zram0
sudo swapon /dev/zram0
```
pudes volver a probar esta configuracion segun tus cambios o disponibilidad en la memoria distribuida 
pero es opcionalmente la mejor opcion ampliar la memoria del equipo para poder tener un rendimiento mucho mas aceptable que cualquier otro 

sudo swapon --show
