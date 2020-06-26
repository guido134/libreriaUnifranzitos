# libreriaUnifranzitos
Cómo crear una biblioteca de Android
Una biblioteca de Android tiene la misma estructura que un módulo de app de Android. Puede incluir todo lo que se necesita para compilar una app, como el código fuente, archivos de recursos y un manifiesto de Android. Sin embargo, en lugar de compilarse en un APK que se ejecute en un dispositivo, una biblioteca de Android se compila en un archivo Android ARchive (AAR) que puedes usar como dependencia para un módulo de app de Android. A diferencia de los archivos JAR, los archivos AAR pueden contener recursos de Android y un archivo de manifiesto, que te permite incluir recursos compartidos, como diseños y elementos de diseño, además de clases y métodos de Java.

Un módulo de biblioteca es útil en las siguientes situaciones:

Cuando compilas varias apps que comparten algunos componentes, como actividades, servicios o diseños de IU
Cuando compilas una app que existe en diferentes variantes del APK, como una versión gratuita o paga, y necesitas los principales componentes en ambas variantes
En cualquier caso, mueve los archivos que desees volver a usar a un módulo de biblioteca y, luego, agrega la biblioteca como una dependencia para cada módulo de app. En esta página, se muestran los dos procedimientos.

Cómo crear un módulo de biblioteca
Para crear un módulo de biblioteca en tu proyecto, haz lo siguiente:

Haz clic en File > New > New Module.
En la ventana Create New Module que aparece, haz clic en Android Library y, luego, en Next.
También se puede crear una biblioteca Java, que compila un archivo JAR tradicional. Si bien un archivo JAR es útil para muchos proyectos, en especial cuando deseas compartir el código con otras plataformas, no te permite incluir archivos de manifiesto ni recursos de Android, y esto es muy útil para reutilizar el código en proyectos de Android. Por ello, esta guía se enfoca en la creación de bibliotecas de Android.

Otorga un nombre a la biblioteca y selecciona una versión mínima del SDK para el código de la biblioteca. Luego, haz clic en Finish.
Una vez que se haya completado la sincronización del proyecto de Gradle, se mostrará el módulo de la biblioteca en el panel Project de la izquierda. Si no se muestra la carpeta del módulo nuevo, asegúrate de que se muestre la vista Android.
Anatomía de un archivo AAR
La extensión de un archivo AAR es .aar y el tipo de artefacto de Maven también debe ser aar. El archivo es de tipo zip y contiene las siguientes entradas obligatorias:

    /AndroidManifest.xml
    /classes.jar
    /res/
    /R.txt
    /public.txt
Además, un archivo AAR puede incluir una o más de las siguientes entradas opcionales:

    /assets/
    /libs/name.jar
    /jni/abi_name/name.so (donde abi_name es una de las ABI compatibles con Android)
    /proguard.txt
    /lint.jar
    /api.jar

Añadir al archivo activity_main.java

    _initializeComponents();
  
  
    _initializeFragmentAdapter();
   
   
   ahora se debe de crear estas funciones con las siguientes parametros:
   
   
    public void _initializeComponents(){
        viewPagerContainer = findViewById(R.id.viewPagerContainer);
    }

    public void _initializeFragmentAdapter() {
        OnboardingAdapter adapter = new OnboardingAdapter(getSupportFragmentManager());
        viewPagerContainer.setAdapter(adapter);
    }

Ahora al activitymain.xml el siguien codigo:

    <androidx.viewpager.widget.ViewPager
        android:id="@+id/viewPagerContainer"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    </androidx.viewpager.widget.ViewPager>


