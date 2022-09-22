# Permisos, cuales hay, para que sirven


### Role Based Access Control (RBAC)

Hay diferentes tipos, el primero que salta en la búsqueda es el RBAC que es el "Role Based Access Control" o "control de acceso basado en roles"

el RBAC se distingue por lo que entendí a que el sistema asigna dos cos cosas, una es un nivel y la otra es una categoría, dependiendo de esto se compara con un rol definido y de alli depende si le da acceso o no a ciertas funciones

para que funcione lo primero que se debe hacer es primero crear siempre los roles y autorizaciones, después se asignan los roles segun sus tareas esto pára asegurar que los usuarios pueda hacer sus actividades sin realizar mas ajustes... a lo que entendi por ejemplo en monster hunter, yo puedo tener en una misión el rol de atacante y de sanador, no solo me quedo con uno si no que puedo usar los dos, con el rol de sanador tengo acceso a una habilidad que cuando yo me curo también curo a todos mis aliados y como atacante tengo acceso a munición, solo podría tener el rol de atacante pero si veo que la mision esta dificill puedo tomar el rol de sanador y cada que vea a alguien apunto de morir simplemente curarme y curarlo a el también.

La "identity access management system" (IAM ) se encarga de la aplicación y supervisión de la RBAC que se encarga del registro, control y actualización de los usuarios (osease la asignación de roles) a lo que entendí esto se encarga de organizar que roles se pueden asignar, incluso los usuarios podrían asignarse ellos mismos sus roles pero un administrador debe aprobarlos y o en dado caso revertir los cambios

el como se crea un RBAC, e spor un sistema piramidal llamado ROLE MINING (me sono mas a minería) la organización define los roles y luego se lo asigna a cada empleado (uno o mas roles dependiendo de sus funciones)

la cima de la piramide define las autorizaciones para cada empleado

el segundo nivel es definir que rol pertenece a cada dependencia, el ejemplo que usan es el de recursos humanos y finanzas que debe poder acceder al sistema ERP y pues obvio las demas dependencias no al igual que recursos humanos deben poder acceder a los datos de los usuarios pero finanzas no tiene porque hacerlo, ais es como se van creando los roles

el tercer nivel no entendi muy bien pero es la mas baja y se definen no los roles si no las funciones de los empleados para poder ver que rol se le asignara

> ya le entendi un poco mejor, se refiere el tercer nivel  a la asignacion de roles dependiendo que funciones realiza cada empleado, como ejemplo que se me ocurre (ya no el del copy master) es ver si un empelado o grupo de empleados desarolla la misma funcion que se puede definir como un rol especifico o uno ya creado, por ejemplo en nuestra pagina un usuario podra cambiar su nombre de perfil, esa funcion tambien la puede realizar un administrador pero no por eso se le dara el rol de administrador, entocnes se CREA un rol en base a la funcion de poder cambiar el perfil y este se le asigna al usuario como al administrador

el fundamento de roles, un empleado puede hacer cosas que no precisamente tiene asignadas, por eso se le pueden poner roles adicionales que es la ventaja de este sistema de RBAC, namas le creas ese rol y se lo asignas a el, ya después cuando otro empleado haga lo mismo solo le asignas ese rol tambien pa que pueda acceder a los recursos de este, por lo que entendí un ejemplo que se me ocurre es que un empleado de oficina le agarra la onda a la copiadora, entonces se vuelve el bueno de ls copias, pero llega el momento que se acaba la tinta a la copiadora, entonces los de administrador le pueden asignar el rol de "master of the copys" y darle el poder (o el recurso pues) de que cuando el que le sabe vea que se acabara la tinta o las hojas tener el poder de pedirlas directamente, ya después si llega alguien mas a quien le asignen el unico trabajo de sacar copias solo se le da el mismo rol y listo

Lo bueno y lo malo del RBAC

Lo bueno: 
flexible, porque se le puede asignar uno o mas roles a un mismo usuario
menos esfuerzo, no tienes que andar viendo que empelado necesita cierto permiso, solo se le pone el rol y ya este tiene los permisos
baja susceptibilidad a errores, el estar dándoles permisos individuales deriva a que sea mas complejo saber si juanito perez tiene derecho a sacar copias y susanita la secre solo s ele dio chance una ves porque le urgía, nel con los roles es, tiene rol de saca copias? si, ok entonces peude sacar copias, pedir toner, y mandar a imprimir
mas eficiencia, pos creo lo explique arriba jejejee
seguridad, si alguien no tiene el rol de las copias no tendra acceso a ellas ni parcialmente ni nada
transparencia, el nombre de "master of the copys" te dice casi todo lo que hace el rol o a que se refiere y por eso es facil de entender

Lo malo:
laborioso, el poder definir que hace cada quien y asignarlo a un rol si suena como algo super tedioso mas porque cada quien hace cosas que ni al caso 
asignaciones temporales, es mas fácil olvidar que alguna ves le dieron a susanita permiso de pedir toner con el roll de "maser of the copys" y capas que solo lo uso una ves, pero ya ese rol se le quedo asignado
aplicación, cuando es una pequeña empresa o proyecto la creación de roles (por lo que dije arriba que cada quien hace un montón de cosas) seria más laboriosa, pero en un proyecto como el que queremos hacer no seria tanto


todo esto lo saque de leerlo aqui
https://www.ionos.es/digitalguide/servidores/seguridad/que-es-el-role-based-access-control-rbac/


### Listas de Control de Acceso (ACL's )

