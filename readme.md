**�Qu� comando utilizaste en el paso 11? �Por qu�?**  
*git reset --hard HEAD~1*  
*git reset* mueve el puntero *HEAD* y el de la la rama activa a un *commit* concreto  
Si usamos *HEAD~1* vamos al commit anterior al que est� apuntando la rama activa, lo que descarta el �ltimo *commit*  
Si usamos *--hard* hace que el *working area* quede como estaba en ese *commit*, lo que descarta completamente los cambios realizados  
Si no usamos el modificador *--hard*, descartamos el �ltimo *commit* pero se mantienen los cambios en el *working area* para poder volver a incluirlos en el pr�ximo *commit*  

------------------------------------------------------------------

**�Qu� comando o comandos utilizaste en el paso 12? �Por qu�?**  
*git log* para averiguar el identificador del *commit* al que quiero volver (d509e67)  
*git reset --hard d509e67* para movernos nuevamente a ese *commit* recuperando el *working area tal* y como estaba en ese *commit*  
Este paso tiene trampa, porque al decir "Rehacer el �ltimo commit" se puede interpretar como "volver a hacer" el mismo *commit*  
Para seguir esa estrategia deber�amos aplicar de nuevo las modificaciones del paso 9, agragar el fichero al *staging area* y volver a hacer el *commit*. Esto se debe a que en el paso 11 se hizo un *git reset --hard* y ello hace que ya no tengamos esas moficiaciones en el *working area*  

------------------------------------------------------------------

**El merge del paso 13, �Caus� alg�n conflicto? �Por qu�?**  
Este *merge* no causa conflictos ni provoca ninguna acci�n. La rama *styled* ya tiene todos los cambios de *master* (*styled* est� un *commit* m�s adelante que *master*) por lo que no tienen nada que absorver  

------------------------------------------------------------------

**El merge del paso 19, �Caus� alg�n conflicto? �Por qu�?**  
Este *merge* s� causa conflictos, debido a que el fichero *git-nuestro.md* ha sido midificado en ambas ramas, en las mismas filas. Editamos el fichero manteniendo los contenidos de la rama *styled* y acabamos el *merge*  

------------------------------------------------------------------

**El merge del paso 21, �Caus� alg�n conflicto? �Por qu�?**  
No porque la rama *styled* esta dos *commits* m�s "adelante" que *master*. El *merge* es *fast-forward*, o lo que es lo mismo, el puntero de la rama *master* avanza hasta el *commit* al que apunta *styled* sin generar un nuevo *commit*  

------------------------------------------------------------------

**�Qu� comando o comandos utilizaste en el paso 25?**  
*git log --graph --decorate --pretty=oneline --abbrev-commit*  
Tambi�n, en mi caso podr�a obtenerlo con *git grafico* ya que cre� un alias *grafico* con el fin de facilitar el uso del comando.  

------------------------------------------------------------------

**El merge del paso 26, �Podr�a ser fast forward? �Por qu�?**  
Si podr�a ser *fast forward*. La rama *title* esta un *commit* m�s arriba que *master* por lo que contiene todos sus cambios. Si hacemos un *merge* por defecto (*fast forward*), Git solo mover�a el puntero de la rama *master* al *commit* al que apunta la rama *title*. Al hacerlo *no fast forward* se ha generado un nuevo *commit* con la fusi�n de ambos.  

------------------------------------------------------------------

**�Qu� comando o comandos utilizaste en el paso 27?**  
*git reset HEAD~1* vuelvo un *commit* antes del actual y al no usar el modificador *--hard*, el *working copy* permanece inalterado  

------------------------------------------------------------------

**�Qu� comando o comandos utilizaste en el paso 28?**  
*git checkout git-nuestro.md*  

------------------------------------------------------------------

**�Qu� comando o comandos utilizaste en el paso 29?**  
*git branch -D title* Si usamos *-d* no puede eliminarla porque el *commit* quedar�a sin referencias  

------------------------------------------------------------------

**�Qu� comando o comandos utilizaste en el paso 30?**  
*git merge --no-ff 5041f57* Al eliminar la rama *title* Git nos indica que ese es el Id del *commit* por lo que podemos usarlo directamente para *rehacer* el merge del paso 26.  
Tambi�n podr�amos habernos movido al *commit*, haber creado la rama *title*, haber vuelto a *master* y entonces ejecutar exactamente el mismo *merge* que en ese paso, pero prefiero ahorrarme los pasos extra :)  

------------------------------------------------------------------

**�Qu� comando o comandos usaste en el paso 32?**  
*git reflog* para ver el id del commit inicial (es el e04c34c)  
*git checkout e04c34c* para ir al commit inicial  

------------------------------------------------------------------

**�Qu� comando o comandos usaste en el punto 33?**  
*git reflog* para ver el id del commit inicial (es el 449ac59)  
*git checkout 449ac59* para ir al commit final  
