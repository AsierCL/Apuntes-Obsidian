#C_Programming
## Creación de [[Procesos]]
En las variables tipo *pid_t*, guardamos el PID de un proceso, que es en esencia un int.
Para obtener el PID del proceso actual, usamos *getpid()*.
Para crear un proceso hijo desde el proceso padre, se usa la función *fork()*. Para el padre, la variable hijo vale el PID del hijo, probablemente el siguiente al suyi, mientras que en el proceso hijo, tiene valor 0. Si *fork()* devuelve -1, significa que ha habido un error.
```C
pid_t hijo = fork();
if(hijo==0){
	printf("Soy el hijo");
}else{
	printf("Soy el padre");
}
```


El código de un hijo debe terminar con un *exit(int)* como el padre. Esta función, a parte de terminar la ejecución del proceso, devuelve el valor del código del exit al padre, que debe esperarlo y recogerlo de la siguiente forma:
```C
pid_t hijo;
if((hijo=fork())==0){
	//Codigo del hijo
	printf("Soy el proceso hijo, con PID %d, y retorno un 5",getpid());
	exit(5);
}else{
	//Codigo del padre
	sleep(2);
	int codigo;
	wait(&codigo);
	printf("El hijo ha devuelto un %d",codigo);
	exit(0);
}
```
En este programa, el hijo queda en estado zombie 2 segundos, hasta que el padre lo recoje.

