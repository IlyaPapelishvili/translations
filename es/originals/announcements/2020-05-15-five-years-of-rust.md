---
layout: enviar
title: Cinco años de herrumbre
author: El equipo central de Rust
---

Con todo lo que está sucediendo en el mundo, se te perdonará que olvides que a partir de hoy, ¡han pasado cinco años desde que lanzamos 1.0 en 2015! El óxido ha cambiado mucho en los últimos cinco años, por lo que queríamos reflexionar sobre todo el trabajo de nuestros colaboradores desde la estabilización del lenguaje.

Rust es un lenguaje de programación de propósito general que permite a todos crear software confiable y eficiente. Rust puede construirse para ejecutarse en cualquier lugar de la pila, ya sea como el núcleo de su sistema operativo o su próxima aplicación web. Está construido en su totalidad por una comunidad abierta y diversa de individuos, principalmente voluntarios que donan generosamente su tiempo y experiencia para ayudar a que Rust sea lo que es.

## Cambios importantes desde 1.0

#### 2015

**[1.2] - Codegen paralelo: las** mejoras en el tiempo de compilación son un tema importante para cada lanzamiento de Rust, y es difícil imaginar que hubo un corto tiempo en el que Rust no tuvo generación de código paralelo.

**[1.3] - El Rustonomicon:** Nuestro primer lanzamiento del fantástico "Rustonomicon", un libro que explora el óxido inseguro y los temas que lo rodean, se ha convertido en un gran recurso para cualquiera que quiera aprender y comprender uno de los aspectos más difíciles del lenguaje.

**[1.4] - Soporte de Windows MSVC Tier 1:** La primera promoción de plataforma de nivel 1 trajo soporte nativo para Windows de 64 bits usando la cadena de herramientas Microsoft Visual C ++ (MSVC). Antes de 1.4, también necesitaba tener instalado MinGW (un entorno GNU de terceros) para usar y compilar sus programas Rust. El soporte de Windows de Rust es una de las mayores mejoras en los últimos cinco años. ¡Recientemente, Microsoft [anunció una vista previa pública de su soporte oficial Rust para la API WinRT!] Ahora es más fácil que nunca crear aplicaciones nativas y multiplataforma de alta calidad.

**[1.5] - Instalación de carga:** la adición de poder construir binarios Rust junto con el soporte de plugins preexistente de carga ha dado lugar a un ecosistema completo de aplicaciones, utilidades y herramientas de desarrollo que la comunidad ha llegado a amar y de las que depende. ¡Muchos de los comandos que carga tiene hoy fueron los primeros complementos que la comunidad construyó y compartió en crates.io!

#### 2016

**[1.6] - Libcore:** `libcore` es un subconjunto de la biblioteca estándar que solo contiene API que no requieren funciones de asignación o de nivel de sistema operativo. La estabilización de libcore trajo la capacidad de compilar Rust sin asignación o dependencia del sistema operativo, fue uno de los primeros pasos importantes hacia el soporte de Rust para el desarrollo de sistemas integrados.

**[1.10] - Bibliotecas dinámicas C ABI:** el tipo de caja `cdylib` permite compilar Rust como una biblioteca dinámica C, lo que le permite incrustar sus proyectos Rust en cualquier sistema que admita C ABI. Algunas de las historias de éxito más grandes de Rust entre los usuarios es poder escribir una pequeña parte crítica de su sistema en Rust e integrarse sin problemas en la base de código más grande, y ahora es más fácil que nunca.

**[1.12] - Espacios de trabajo de carga: los** espacios de trabajo le permiten organizar múltiples proyectos de herrumbre y compartir el mismo archivo de bloqueo. Los espacios de trabajo han sido invaluables en la construcción de grandes proyectos a nivel de múltiples cajas.

**[1.13] - El operador Try:** La primera adición de sintaxis importante fue el `?` o el operador "Probar". El operador le permite propagar fácilmente su error a través de su pila de llamadas. ¡Antes tenía que usar el `try!` macro, que requería que envolviera la expresión completa cada vez que encontraba un resultado, ¿ahora puede encadenar fácilmente los métodos `?` en lugar.

```rust
try!(try!(expression).method()); // Old
expression?.method()?;           // New
```

**[1.14] - Rustup 1.0:** Rustup es el administrador de la cadena de herramientas de Rust, le permite usar sin problemas cualquier versión de Rust o cualquiera de sus herramientas. Lo que comenzó como un humilde script de shell se ha convertido en lo que los encargados llaman cariñosamente *"quimera"* . Ser capaz de proporcionar una gestión de versiones de compilador de primera clase en Linux, macOS, Windows y las docenas de plataformas de destino habría sido un mito hace solo cinco años.

#### 2017

**[1.15] — Derive Procedural Macros:** Derive Macros allow you to create powerful and extensive strongly typed APIs without all the boilerplate. This was the first version of Rust you could use libraries like `serde` or `diesel`'s derive macros on stable.

**[1.17] - Rustbuild:** Una de las mejoras más importantes para nuestros contribuyentes a la lengua se movía nuestro sistema de construcción de la primera `make` sistema basado en el uso de la carga. Esto ha abierto a `rust-lang/rust` para que sea mucho más fácil para los miembros y los recién llegados para construir y contribuir al proyecto.

**[1.20] - Constantes asociadas:** Anteriormente, las constantes solo podían asociarse con un módulo. En 1.20 estabilizamos la asociación de constantes en estructuras, enumeraciones y rasgos importantes. Facilitando la adición de conjuntos completos de valores preestablecidos para tipos en su API, como direcciones IP comunes o números interesantes.

#### 2018

**[1.24] - Compilación incremental:** antes de 1.24, cuando realizó un cambio en su biblioteca, rustc tendría que volver a compilar todo el código. Ahora rustc es mucho más inteligente sobre el almacenamiento en caché tanto como sea posible y solo necesita volver a generar lo que se necesita.

**[1.26] - impl Trait:** la incorporación de `impl Trait` le brinda API dinámicas expresivas con los beneficios y el rendimiento del envío estático.

**[1.28] - Asignadores globales:** anteriormente estaba restringido a usar el asignador que proporcionaba el óxido. Con la API del asignador global ahora puede personalizar su asignador a uno que se adapte a sus necesidades. Este fue un paso importante para permitir la creación de la biblioteca `alloc` , otro subconjunto de la biblioteca estándar que contiene solo las partes de std que necesitan un asignador como `Vec` o `String` . Ahora es más fácil que nunca usar incluso más partes de la biblioteca estándar en una variedad de sistemas.

**[1.31] - Edición 2018:** el lanzamiento de la edición 2018 fue fácilmente nuestro lanzamiento más importante desde 1.0, agregando una colección de cambios de sintaxis y mejoras en la escritura de Rust escrita de una manera totalmente compatible con versiones anteriores, permitiendo que las bibliotecas construidas con diferentes ediciones funcionen juntas sin problemas.

- **Tiempos de vida no léxicos** Una gran mejora para el verificador de préstamos de Rust, que le permite aceptar un código seguro más verificable.
- **Mejoras en el sistema de módulos** Grandes mejoras de UX en cómo definimos y usamos los módulos.
- **Funciones** Const Las funciones Const le permiten ejecutar y evaluar el código Rust en tiempo de compilación.
- **Rustfmt 1.0** Una nueva herramienta de formateo de código creada específicamente para Rust.
- **Linter de Clippy 1.0** Rust para detectar errores comunes. Clippy hace que sea mucho más fácil asegurarse de que su código no solo sea seguro sino correcto.
- **Rustfix** Con todos los cambios de sintaxis, sabíamos que queríamos proporcionar las herramientas para hacer la transición lo más fácil posible. Ahora, cuando se requieren cambios en la sintaxis de Rust, son solo una `cargo fix` lejos de resolverse.

#### 2019

**[1.34] - Registros de cajas alternativas: a** medida que Rust se usa cada vez más en la producción, existe una mayor necesidad de poder albergar y usar sus proyectos en espacios no públicos, mientras que la carga siempre ha permitido dependencias remotas de git, con Registros alternativos su organización puede crear y compartir fácilmente su propio registro de cajas que se pueden usar en sus proyectos como si estuvieran en crates.io.

**[1.39] - Async / Await:** La estabilización de las palabras clave async / wait para manejar Futures fue uno de los principales hitos para hacer de la programación async en Rust un ciudadano de primera clase. Incluso solo seis meses después de su lanzamiento, la programación asincrónica se ha convertido en un ecosistema diverso y dinámico.

#### 2020

**[1.42] - patrones Subslice:** Aunque no es el mayor cambio, la adición de la `..` patrón (el resto) ha sido la calidad esperada de la función de vida que mejora en gran medida la expresividad de coincidencia de patrones con rodajas.

## Diagnóstico de errores

Una cosa que no hemos mencionado mucho es cuánto han mejorado los mensajes de error y los diagnósticos de Rust desde 1.0. Mirar mensajes de error más antiguos ahora se siente como mirar un idioma diferente.

Hemos destacado un par de ejemplos que muestran mejor cuánto hemos mejorado al mostrar a los usuarios dónde cometieron errores y, de manera importante, les ayudamos a comprender por qué no funciona y les enseñamos cómo pueden solucionarlo.

##### Primer ejemplo (rasgos)

```rust
use std::io::Write;

fn trait_obj(w: &Write) {
    generic(w);
}

fn generic<W: Write>(_w: &W) {}
```

<details>
 <summary>1.2.0 Mensaje de error</summary>
</details>

```
   Compiling error-messages v0.1.0 (file:///Users/usr/src/rust/error-messages)
src/lib.rs:6:5: 6:12 error: the trait `core::marker::Sized` is not implemented for the type `std::io::Write` [E0277]
src/lib.rs:6     generic(w);
                 ^~~~~~~
src/lib.rs:6:5: 6:12 note: `std::io::Write` does not have a constant size known at compile-time
src/lib.rs:6     generic(w);
                 ^~~~~~~
error: aborting due to previous error
Could not compile `error-messages`.

To learn more, run the command again with --verbose.
```




![Una captura de pantalla del terminal del mensaje de error 1.2.0.](/images/2020-05-15-five-years-of-rust/trait-error-1.2.0.png)

<details>
 <summary>1.43.0 Mensaje de error</summary>
</details>

```
   Compiling error-messages v0.1.0 (/Users/ep/src/rust/error-messages)
error[E0277]: the size for values of type `dyn std::io::Write` cannot be known at compilation time
 --> src/lib.rs:6:13
  |
6 |     generic(w);
  |             ^ doesn't have a size known at compile-time
...
9 | fn generic<W: Write>(_w: &W) {}
  |    ------- -       - help: consider relaxing the implicit `Sized` restriction: `+  ?Sized`
  |            |
  |            required by this bound in `generic`
  |
  = help: the trait `std::marker::Sized` is not implemented for `dyn std::io::Write`
  = note: to learn more, visit <https://doc.rust-lang.org/book/ch19-04-advanced-types.html#dynamically-sized-types-and-the-sized-trait>

error: aborting due to previous error

For more information about this error, try `rustc --explain E0277`.
error: could not compile `error-messages`.

To learn more, run the command again with --verbose.
```




![Una captura de pantalla del terminal del mensaje de error 1.43.0.](/images/2020-05-15-five-years-of-rust/trait-error-1.43.0.png)

##### Segundo ejemplo (ayuda)

```rust
fn main() {
    let s = "".to_owned();
    println!("{:?}", s.find("".to_owned()));
}
```

<details>
 <summary>1.2.0 Mensaje de error</summary>
</details>

```
   Compiling error-messages v0.1.0 (file:///Users/ep/src/rust/error-messages)
src/lib.rs:3:24: 3:43 error: the trait `core::ops::FnMut<(char,)>` is not implemented for the type `collections::string::String` [E0277]
src/lib.rs:3     println!("{:?}", s.find("".to_owned()));
                                    ^~~~~~~~~~~~~~~~~~~
note: in expansion of format_args!
<std macros>:2:25: 2:56 note: expansion site
<std macros>:1:1: 2:62 note: in expansion of print!
<std macros>:3:1: 3:54 note: expansion site
<std macros>:1:1: 3:58 note: in expansion of println!
src/lib.rs:3:5: 3:45 note: expansion site
src/lib.rs:3:24: 3:43 error: the trait `core::ops::FnOnce<(char,)>` is not implemented for the type `collections::string::String` [E0277]
src/lib.rs:3     println!("{:?}", s.find("".to_owned()));
                                    ^~~~~~~~~~~~~~~~~~~
note: in expansion of format_args!
<std macros>:2:25: 2:56 note: expansion site
<std macros>:1:1: 2:62 note: in expansion of print!
<std macros>:3:1: 3:54 note: expansion site
<std macros>:1:1: 3:58 note: in expansion of println!
src/lib.rs:3:5: 3:45 note: expansion site
error: aborting due to 2 previous errors
Could not compile `error-messages`.

To learn more, run the command again with --verbose.

```




![Una captura de pantalla del terminal del mensaje de error 1.2.0.](/images/2020-05-15-five-years-of-rust/help-error-1.2.0.png)

<details>
 <summary>1.43.0 Mensaje de error</summary>
</details>

```
   Compiling error-messages v0.1.0 (/Users/ep/src/rust/error-messages)
error[E0277]: expected a `std::ops::FnMut<(char,)>` closure, found `std::string::String`
 --> src/lib.rs:3:29
  |
3 |     println!("{:?}", s.find("".to_owned()));
  |                             ^^^^^^^^^^^^^
  |                             |
  |                             expected an implementor of trait `std::str::pattern::Pattern<'_>`
  |                             help: consider borrowing here: `&"".to_owned()`
  |
  = note: the trait bound `std::string::String: std::str::pattern::Pattern<'_>` is not satisfied
  = note: required because of the requirements on the impl of `std::str::pattern::Pattern<'_>` for `std::string::String`

error: aborting due to previous error

For more information about this error, try `rustc --explain E0277`.
error: could not compile `error-messages`.

To learn more, run the command again with --verbose.
```




![Una captura de pantalla del terminal del mensaje de error 1.43.0.](/images/2020-05-15-five-years-of-rust/help-error-1.43.0.png)

##### Tercer ejemplo (corrector de préstamos)

```rust
fn main() {
    let mut x = 7;
    let y = &mut x;

    println!("{} {}", x, y);
}
```

<details>
 <summary>1.2.0 Mensaje de error</summary>
</details>

```
   Compiling error-messages v0.1.0 (file:///Users/ep/src/rust/error-messages)
src/lib.rs:5:23: 5:24 error: cannot borrow `x` as immutable because it is also borrowed as mutable
src/lib.rs:5     println!("{} {}", x, y);
                                   ^
note: in expansion of format_args!
<std macros>:2:25: 2:56 note: expansion site
<std macros>:1:1: 2:62 note: in expansion of print!
<std macros>:3:1: 3:54 note: expansion site
<std macros>:1:1: 3:58 note: in expansion of println!
src/lib.rs:5:5: 5:29 note: expansion site
src/lib.rs:3:18: 3:19 note: previous borrow of `x` occurs here; the mutable borrow prevents subsequent moves, borrows, or modification of `x` until the borrow ends
src/lib.rs:3     let y = &mut x;
                              ^
src/lib.rs:6:2: 6:2 note: previous borrow ends here
src/lib.rs:1 fn main() {
src/lib.rs:2     let mut x = 7;
src/lib.rs:3     let y = &mut x;
src/lib.rs:4
src/lib.rs:5     println!("{} {}", x, y);
src/lib.rs:6 }
             ^
error: aborting due to previous error
Could not compile `error-messages`.

To learn more, run the command again with --verbose.
```




![Una captura de pantalla del terminal del mensaje de error 1.2.0.](/images/2020-05-15-five-years-of-rust/borrow-error-1.2.0.png)

<details>
 <summary>1.43.0 Mensaje de error</summary>
</details>

```
   Compiling error-messages v0.1.0 (/Users/ep/src/rust/error-messages)
error[E0502]: cannot borrow `x` as immutable because it is also borrowed as mutable
 --> src/lib.rs:5:23
  |
3 |     let y = &mut x;
  |             ------ mutable borrow occurs here
4 |
5 |     println!("{} {}", x, y);
  |                       ^  - mutable borrow later used here
  |                       |
  |                       immutable borrow occurs here

error: aborting due to previous error

For more information about this error, try `rustc --explain E0502`.
error: could not compile `error-messages`.

To learn more, run the command again with --verbose.
```




![Una captura de pantalla del terminal del mensaje de error 1.43.0.]

## Cotizaciones de los equipos

Por supuesto, no podemos cubrir cada cambio que ha sucedido. Así que contactamos y preguntamos a algunos de nuestros equipos de qué cambios están más orgullosos:

> Para rustdoc, las grandes cosas fueron:
> - La documentación generada automáticamente para implementaciones generales
> - La búsqueda en sí y sus optimizaciones (la última es convertirla en JSON)
> - La posibilidad de probar con mayor precisión los bloques de código de documento "compile_fail, should_panic, allow_fail"
> - Las pruebas de documentos ahora se generan como sus propios binarios separados.
> - Guillaume Gómez ( [rustdoc] )

> ¡Rust ahora tiene soporte básico de IDE! Entre IntelliJ Rust, RLS y el analizador de óxido, creo que la mayoría de los usuarios deberían poder encontrar una experiencia "no horrible" para el editor de su elección. Hace cinco años, "escribir Rust" significaba usar la configuración de Vim / Emacs de la vieja escuela.
> - Aleksey Kladov ( [IDEs y editores] )

> Para mí eso sería: Agregar soporte de primera clase para arquitecturas integradas populares y lograr un ecosistema esforzado para hacer que el desarrollo de microcontroladores con Rust sea una experiencia fácil y segura, pero divertida.
> - Daniel Egger ( [GT integrado] )

> El equipo de lanzamiento solo ha existido desde (aproximadamente) principios de 2018, pero incluso en ese momento, hemos logrado ~ 40000 confirmaciones solo en rust-lang / rust sin ninguna regresión significativa en estable.
> Considerando lo rápido que estamos mejorando el compilador y las bibliotecas estándar, creo que es realmente impresionante (aunque, por supuesto, el equipo de lanzamiento no es el único contribuyente aquí). En general, he descubierto que el equipo de lanzamiento ha hecho un excelente trabajo al escalar para aumentar el tráfico en rastreadores de problemas, relaciones públicas que se archivan, etc.
> - Mark Rousskov ( [Lanzamiento] )

> En los últimos 3 años, logramos convertir a [Miri] de intérprete experimental en una herramienta práctica para explorar el diseño del lenguaje y encontrar errores en el código real, una gran combinación de teoría y práctica de PL. En el lado teórico tenemos [Stacked Borrows] , la propuesta más concreta para un modelo de alias Rust hasta ahora. Desde el punto de vista práctico, aunque inicialmente solo revisamos algunas bibliotecas clave en Miri, recientemente vimos una gran aceptación de personas que utilizan Miri para [encontrar y corregir errores](https://github.com/rust-lang/miri/#bugs-found-by-miri) en sus propias cajas y dependencias, y una aceptación similar en los contribuyentes que mejoraron Miri, por ejemplo. agregando soporte para acceso al sistema de archivos, desenrollado y concurrencia.
> - Ralf Jung ( [Miri] )

> Si tuviera que elegir una cosa de la que estoy más orgulloso, fue el trabajo en vidas no léxicas (NLL). No solo porque creo que marcó una gran diferencia en la usabilidad de Rust, sino también por la forma en que lo implementamos al formar el grupo de trabajo NLL. Este grupo de trabajo atrajo a muchos colaboradores excelentes, muchos de los cuales todavía están trabajando en el compilador hoy. ¡Código abierto en su máxima expresión!
> - Niko Matsakis ( [Idioma] )

## La comunidad

A medida que el idioma ha cambiado y crecido mucho en los últimos cinco años, también lo ha hecho su comunidad. Se han escrito tantos grandes proyectos en Rust, y la presencia de Rust en la producción ha crecido exponencialmente. Queríamos compartir algunas estadísticas sobre cuánto ha crecido Rust.

- Rust ha sido votado como ["Programación más amada"] cada año en las últimas cuatro encuestas de desarrolladores de Stack Overflow desde que fue 1.0.
- ¡Hemos servido más de 2.25 Petabytes (1PB = 1,000 TB) de diferentes versiones del compilador, herramientas y documentación solo este año!
- Al mismo tiempo, hemos atendido más de 170 TB de cajas a aproximadamente 1.800 millones de solicitudes en crates.io, duplicando el tráfico mensual en comparación con el año pasado.

Cuando Rust cumplió 1.0 años, podía contar el número de compañías que lo usaban en producción por un lado. Hoy en día, cientos de compañías tecnológicas lo utilizan, y algunas de las compañías tecnológicas más grandes, como Apple, Amazon, Dropbox, Facebook, Google y Microsoft, optan por usar Rust por su desempeño, confiabilidad y productividad en sus proyectos.

## Conclusión

Obviamente, no pudimos cubrir cada cambio o mejora de Rust que ha sucedido desde 2015. ¿Cuáles han sido sus cambios favoritos o nuevos proyectos favoritos de Rust? Siéntase libre de publicar su respuesta y discusión en [nuestro foro Discurso](TODO:%20CREATE%20FORUM%20POST%20BEFORE%20MERGE) .

Por último, queríamos agradecer a todos los que han contribuido a Rust, ya sea que haya contribuido con una nueva característica o haya corregido un error tipográfico, su trabajo ha hecho que Rust sea increíble. ¡Estamos ansiosos por ver cómo Rust y su comunidad continuarán creciendo y cambiando, y veremos qué construirán con Rust en la próxima década!


[anunció una vista previa pública de su soporte oficial Rust para la API WinRT!]: https://blogs.windows.com/windowsdeveloper/2020/04/30/rust-winrt-public-preview/
[1.2]: https://blog.rust-lang.org/2015/08/06/Rust-1.2.html
[1.3]: https://blog.rust-lang.org/2015/09/17/Rust-1.3.html
[1.4]: https://blog.rust-lang.org/2015/10/29/Rust-1.4.html
[1.5]: https://blog.rust-lang.org/2015/12/10/Rust-1.5.html
[1.6]: https://blog.rust-lang.org/2016/01/21/Rust-1.6.html
[1.10]: https://blog.rust-lang.org/2016/07/07/Rust-1.10.html
[1.12]: https://blog.rust-lang.org/2016/09/29/Rust-1.12.html
[1.13]: https://blog.rust-lang.org/2016/11/10/Rust-1.13.html
[1.14]: https://blog.rust-lang.org/2016/12/22/Rust-1.14.html
[1.15]: https://blog.rust-lang.org/2017/02/02/Rust-1.15.html
[1.17]: https://blog.rust-lang.org/2017/04/27/Rust-1.17.html
[1.20]: https://blog.rust-lang.org/2017/08/31/Rust-1.20.html
[1.24]: https://blog.rust-lang.org/2018/02/15/Rust-1.24.html
[1.26]: https://blog.rust-lang.org/2018/05/10/Rust-1.26.html
[1.28]: https://blog.rust-lang.org/2018/08/02/Rust-1.28.html
[1.31]: https://blog.rust-lang.org/2018/12/06/Rust-1.31-and-rust-2018.html
[1.34]: https://blog.rust-lang.org/2019/04/11/Rust-1.34.0.html
[1.39]: https://blog.rust-lang.org/2019/11/07/Rust-1.39.0.html
[Una captura de pantalla del terminal del mensaje de error 1.43.0.]:  /images/2020-05-15-five-years-of-rust/borrow-error-1.2.0.png
[Miri]: /images/2020-05-15-five-years-of-rust/borrow-error-1.43.0.png
[Stacked Borrows]:    /images/2020-05-15-five-years-of-rust/help-error-1.2.0.png
[rustdoc]:   /images/2020-05-15-five-years-of-rust/help-error-1.43.0.png
[IDEs y editores]:   /images/2020-05-15-five-years-of-rust/trait-error-1.2.0.png
[GT integrado]:  /images/2020-05-15-five-years-of-rust/trait-error-1.43.0.png
[Lanzamiento]: https://github.com/rust-lang/miri
[Miri]: https://github.com/rust-lang/unsafe-code-guidelines/blob/master/wip/stacked-borrows.md
[Idioma]:  https://github.com/rust-lang/miri/#bugs-found-by-miri
["Programación más amada"]: https://www.rust-lang.org/governance/teams/rustdoc