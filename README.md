# Pyrit #
![Pyrit logo](https://pyrit.files.wordpress.com/2009/06/2640399_red12.jpg)

Pyrit le permite crear bases de datos masivas de la [WPA/WPA2-PSK](https://secure.wikimedia.org/wikipedia/en/wiki/Wi-Fi_Protected_Access)precalculada en una compensación de espacio-tiempo. Mediante el uso de la potencia computacional de las CPU multinúcleo y otras plataformas a través de ATI-Stream , Nvidia CUDA y OpenCL , actualmente es, con mucho, el ataque más poderoso contra uno de los protocolos de seguridad más utilizados del mundo. 

WPA/WPA2-PSK es un subconjunto de [IEEE 802.11 WPA/WPA2](https://secure.wikimedia.org/wikipedia/en/wiki/Wi-Fi_Protected_Access) que omite la compleja tarea de distribución de claves y autenticación de clientes al asignar a cada parte participante la misma clave precompartida . Esta clave maestra se deriva de una contraseña que el usuario administrador debe configurar previamente, por ejemplo, en su computadora portátil y el punto de acceso. Cuando la computadora portátil crea una conexión con el punto de acceso, clave de sesión se deriva clave maestra para cifrar y autenticar el tráfico siguiente. El "atajo" de usar una sola clave maestra en lugar de por usuario facilita la implementación de redes protegidas WPA/WPA2 para uso doméstico y en pequeñas oficinas a costa de hacer que el protocolo sea vulnerable a ataques de fuerza bruta contra su fase clave de negociación; permite finalmente revelar la contraseña que protege la red. Esta vulnerabilidad debe considerarse excepcionalmente desastrosa, ya que el protocolo permite calcular previamente gran parte de la derivación de la clave, lo que hace que los ataques simples de fuerza bruta sean aún más atractivos para el atacante. Para más antecedentes ver [this article](http://pyrit.wordpress.com/the-twilight-of-wi-fi-protected-access/) en el [blog](http://pyrit.wordpress.com) *_(Obsolecto)_*.

El autor no fomenta ni apoya el uso Pyrit para infringir la comunicación-privacidad de las personas. La exploración y realización de la tecnología aquí discutida motivan como un fin propio; esto está documentado por el desarrollo abierto, distribución estrictamente basada en código fuente y licencias 'copyleft'.

Pyrit es software libre, libre como en libertad. Todos pueden inspeccionarlo, copiarlo o modificarlo y compartir el trabajo derivado bajo la Licencia Pública General GNU v3+. Compila y se ejecuta en una amplia variedad de plataformas, incluidas FreeBSD, MacOS X y Linux como sistema operativo y procesadores x86, alpha, arm, hppa, mips, powerpc, s390 y sparc.

Atacar WPA/WPA2 por fuerza bruta se reduce a calcular claves maestras lo más rápido posible. Cada clave maestra "vale" exactamente un megabyte de datos que se envían a través de [PBKDF2](http://en.wikipedia.org/wiki/PBKDF2)-[HMAC](http://en.wikipedia.org/wiki/Hmac)-[SHA1](http://en.wikipedia.org/wiki/SHA_hash_functions). A su vez, computar 10.000 PMKs por segundo equivale a hacer hash de 9,8 gigabytes de datos con [SHA1](http://en.wikipedia.org/wiki/SHA_hash_functions) en un segundo. 

Estos son ejemplos de cómo múltiples nodos computacionales pueden acceder a un único servidor de almacenamiento de varias maneras proporcionadas por Pyrit:

- Un solo almacenamiento (por ejemplo, un servidor MySQL)
- Una red local que puede acceder al servidor de almacenamiento directamente y proporcionar cuatro nodos computacionales en varios niveles con solo un nodo accediendo realmente al servidor de almacenamiento. 
- Otra red no confiable puede acceder al almacenamiento a través de la interfaz RPC de Pyrit y proporciona tres nodos computacionales, dos de los cuales realmente acceden a la interfaz RPC.
# Cómo utilizar  #

```sh
sudo apt-get update
sudo apt-get install libssl-dev zlib1g-dev libpcap0.8-dev python2-dev
sudo apt-get update
git clone https://github.com/T3cnokarita/Pyrit_Modified.git
cd Pyrit_Modified/
python2 setup.py clean
python2 setup.py build
sudo python2 setup.py install
cd ..
wget http://kvm.sopicki.name/tanglu/pool/main/s/scapy/python-scapy_2.3.2-0.1_all.deb
sudo dpkg -i python-scapy_2.3.2-0.1_all.deb
```

