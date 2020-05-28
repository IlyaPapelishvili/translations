---
layout: после
title: Пять лет ржавчины
author: Основная команда Rust
---

Со всем, что происходит в мире, вы были бы прощены за то, что забыли, что на сегодняшний день прошло пять лет с тех пор, как мы выпустили 1.0 в 2015 году! За последние пять лет Rust сильно изменился, поэтому мы хотели вспомнить всю работу наших участников после стабилизации языка.

Rust - это язык программирования общего назначения, позволяющий каждому создавать надежное и эффективное программное обеспечение. Rust может быть создан для работы в любом месте стека, будь то ядро вашей операционной системы или ваше следующее веб-приложение. Он построен полностью открытым и разнообразным сообществом людей, в основном добровольцами, которые щедро жертвуют своим временем и опытом, чтобы помочь Rust стать тем, чем он является.

## Основные изменения с 1.0

#### 2015

**[1.2] - Параллельный Codegen:** улучшения во время компиляции - большая тема для каждого выпуска Rust, и трудно представить, что было короткое время, когда Rust вообще не имел параллельной генерации кода.

**[1.3] - Rustonomicon:** наш первый выпуск фантастического "Rustonomicon", книги, в которой исследуется небезопасная ржавчина и связанные с ней темы, стал отличным ресурсом для всех, кто хочет изучить и понять один из самых сложных аспектов языка.

**[1.4] - Поддержка MSVC уровня 1 в Windows** . Первым продвижением платформы уровня 1 была нативная поддержка 64-разрядной версии Windows с использованием набора инструментов Microsoft Visual C ++ (MSVC). До версии 1.4 вам также требовалось установить MinGW (стороннюю среду GNU) для использования и компиляции ваших программ Rust. Поддержка Rust для Windows - одно из самых больших улучшений за последние пять лет. Совсем недавно Microsoft [анонсировала публичную предварительную версию своей официальной поддержки Rust для WinRT API!] Теперь стало проще, чем когда-либо, создавать высококачественные нативные и кроссплатформенные приложения.

**[1.5] — Cargo Install:** The addition of being able to build Rust binaries alongside cargo's pre-existing plugin support has given birth to an entire ecosystem of apps, utilities, and developer tools that the community has come to love and depend on. Quite a few of the commands cargo has today were first plugins that the community built and shared on crates.io!

#### 2016

**[1.6] - Libcore:** `libcore` - это подмножество стандартной библиотеки, которое содержит только API-интерфейсы, которые не требуют функций выделения или уровня операционной системы. Стабилизация libcore дала возможность компилировать Rust без выделения или зависимости от операционной системы, что стало одним из первых основных шагов к поддержке Rust для разработки встраиваемых систем.

**[1.10] - Динамические библиотеки C ABI.** Тип `cdylib` crate позволяет компилировать Rust в виде динамической библиотеки C, что позволяет встраивать проекты Rust в любую систему, которая поддерживает C ABI. Некоторые из самых больших историй успеха Rust среди пользователей - это возможность написать небольшую критическую часть своей системы на Rust и легко интегрировать в большую кодовую базу, и теперь это стало проще, чем когда-либо.

**[1.12] - Грузовые рабочие пространства.** Рабочие пространства позволяют вам организовать несколько проектов ржавчины и совместно использовать один и тот же файл блокировки. Рабочие места были неоценимы при создании крупных проектов на нескольких ящиках.

**[1.13] - Оператор Try:** первое значительное дополнение синтаксиса было `?` или оператор «Попробуйте». Оператор позволяет вам легко распространять вашу ошибку через ваш стек вызовов. Ранее вы должны были `try!` макрос, который требовал от вас оборачивать все выражение каждый раз, когда вы сталкивались с результатом, теперь вы можете легко связать методы с помощью `?` вместо.

```rust
try!(try!(expression).method()); // Old
expression?.method()?;           // New
```

**[1.14] - Rustup 1.0:** Rustup является менеджером Toolchain в Rust, он позволяет вам беспрепятственно использовать любую версию Rust или любой его инструментарий. То, что начиналось как скромный сценарий оболочки, стало тем, что сопровождающие нежно называют *«химерой»* Возможность обеспечить первоклассное управление версиями компилятора в Linux, macOS, Windows и десятках целевых платформ была бы мифом всего пять лет назад.

#### 2017

**[1.15] - Извлечение процедурных макросов:** Извлечение макросов позволяет вам создавать мощные и обширные строго типизированные API-интерфейсы без всяких шаблонов. Это была первая версия Rust, в которой вы могли использовать библиотеки, такие как `serde` или `diesel` , производные макросы в стабильной версии.

**[1.17] - Rustbuild:** Одним из самых больших улучшений для наших авторов языка стал перевод нашей системы сборки с системы начального `make` на использование груза. Это открыло `rust-lang/rust` , чтобы быть намного проще для членов и новичков , так , чтобы построить и внести свой вклад в проект.

**[1.20] - Связанные константы:** ранее константы могли быть связаны только с модулем. В 1.20 мы стабилизировали ассоциативные константы для структуры, перечислений и важных признаков. Упрощение добавления богатых наборов предустановленных значений для типов в вашем API, таких как общие IP-адреса или интересные числа.

#### 2018

**[1.24] - Инкрементная компиляция:** до версии 1.24, когда вы вносили изменения в вашу библиотеку, rustc должен был бы перекомпилировать весь код. Теперь rustc намного умнее о кэшировании, насколько это возможно, и ему нужно только заново генерировать то, что нужно.

**[1.26] - Impl Trait:** добавление `impl Trait` дает вам выразительные динамические API с преимуществами и производительностью статической диспетчеризации.

**[1.28] — Global Allocators:** Previously you were restricted to using the allocator that rust provided. With the global allocator API you can now customise your allocator to one that suits your needs. This was an important step in enabling the creation of the `alloc` library, another subset of the standard library containing only the parts of std that need an allocator like `Vec` or `String`. Now it's easier than ever to use even more parts of the standard library on a variety of systems.

**[1.31] - издание 2018 года** . Выпуск издания 2018 года был, пожалуй, самым большим нашим выпуском с 1.0, добавив набор синтаксических изменений и улучшений в написании Rust, написанного полностью обратно совместимым образом, что позволяет библиотекам, созданным в разных редакциях, беспрепятственно работать вместе.

- **Non-Lexical Lifetimes** Огромное улучшение в контроллере заимствований Rust, позволяющее ему принимать более проверяемый безопасный код.
- **Module System Improvements** Large UX improvements to how we define and use modules.
- **Const-функции** Const-функции позволяют запускать и оценивать код Rust во время компиляции.
- **Rustfmt 1.0** Новый инструмент форматирования кода, созданный специально для Rust.
- **Clippy 1.0** Rust linter для ловли распространенных ошибок. Clippy значительно упрощает проверку того, что ваш код не только безопасен, но и корректен.
- **Rustfix** Со всеми изменениями синтаксиса мы знали, что хотим предоставить инструментарий, чтобы сделать переход максимально простым. Теперь, когда требуются изменения в синтаксисе Rust, они просто `cargo fix` связанную с решением проблемы.

#### 2019

**[1.34] - Альтернативные реестры ящиков:** поскольку Rust все больше используется в производстве, существует большая необходимость иметь возможность размещать и использовать ваши проекты в непубличных пространствах, в то время как груз всегда допускает удаленные зависимости git, а в вашей организации есть альтернативные реестры. может легко создать и поделиться вашим собственным реестром ящиков, которые можно использовать в ваших проектах, как они были на crates.io.

**[1.39] - Async / Await:** Стабилизация ключевых слов async / await для обработки Futures была одной из основных вех в превращении асинхронного программирования в Rust в первоклассного гражданина. Даже через шесть месяцев после его выпуска асинхронное программирование превратилось в разнообразную и производительную экосистему.

#### 2020

**[1.42] - Паттерны сублис:** хотя это и не самое большое изменение, добавление паттерна `..` (rest) стало долгожданной функцией качества жизни, которая значительно улучшает выразительность сопоставления паттернов со срезами.

## Диагностика ошибок

Одна вещь, которую мы не упомянули, это то, насколько улучшены сообщения об ошибках и диагностика в Rust с 1.0. Глядя на старые сообщения об ошибках, теперь похоже на другой язык.

Мы выделили пару примеров, которые лучше всего демонстрируют, насколько мы улучшились, показывая пользователям, где они допустили ошибки, и, что важно, помогают им понять, почему это не работает, и учат их, как они могут это исправить.

##### Первый пример (черты)

```rust
use std::io::Write;

fn trait_obj(w: &Write) {
    generic(w);
}

fn generic<W: Write>(_w: &W) {}
```

<details>
 <summary>1.2.0 Сообщение об ошибке</summary>
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




![Скриншот терминала сообщения об ошибке 1.2.0.](/images/2020-05-15-five-years-of-rust/trait-error-1.2.0.png)

<details>
 <summary>1.43.0 Сообщение об ошибке</summary>
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




![Снимок экрана с сообщением об ошибке 1.43.0.](/images/2020-05-15-five-years-of-rust/trait-error-1.43.0.png)

##### Второй пример (помощь)

```rust
fn main() {
    let s = "".to_owned();
    println!("{:?}", s.find("".to_owned()));
}
```

<details>
 <summary>1.2.0 Сообщение об ошибке</summary>
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




![Скриншот терминала сообщения об ошибке 1.2.0.](/images/2020-05-15-five-years-of-rust/help-error-1.2.0.png)

<details>
 <summary>1.43.0 Сообщение об ошибке</summary>
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




![Снимок экрана с сообщением об ошибке 1.43.0.](/images/2020-05-15-five-years-of-rust/help-error-1.43.0.png)

##### Третий пример (проверка займа)

```rust
fn main() {
    let mut x = 7;
    let y = &mut x;

    println!("{} {}", x, y);
}
```

<details>
 <summary>1.2.0 Сообщение об ошибке</summary>
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




![Скриншот терминала сообщения об ошибке 1.2.0.](/images/2020-05-15-five-years-of-rust/borrow-error-1.2.0.png)

<details>
 <summary>1.43.0 Сообщение об ошибке</summary>
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




![Снимок экрана с сообщением об ошибке 1.43.0.]

## Цитаты из команд

Конечно, мы не можем охватить каждое произошедшее изменение. Поэтому мы обратились к некоторым из наших команд и спросили, какими изменениями они больше всего гордятся:

> Для rustdoc большие вещи были:
> - Автоматически сгенерированная документация для бланкетных реализаций
> - Сам поиск и его оптимизации (последним является преобразование его в JSON)
> - Возможность более точного тестирования блоков кода документа "compile_fail, should_panic, allow_fail"
> - Doc-тесты теперь генерируются как их отдельные двоичные файлы.
> - Гийом Гомес ( [Рустдок] )

> Rust теперь имеет базовую поддержку IDE! Я полагаю, что между IntelliJ Rust, RLS и анализатором ржавчины большинство пользователей должны найти «не ужасный» опыт для своего редактора. Пять лет назад под «написанием Rust» подразумевалось использование старой школы Vim / Emacs.
> - Алексей Кладов ( [IDE и редакторы] )

> Для меня это было бы следующим: добавление первоклассной поддержки популярных встроенных архитектур и создание стремящейся экосистемы, позволяющей сделать разработку микроконтроллеров с помощью Rust легкой, безопасной и в то же время увлекательной.
> - Даниэль Эггер ( [Embedded WG] )

> Команда релизов работала только с (примерно) начала 2018 года, но даже за это время мы получили ~ 40000 коммитов только в состоянии ржавчины / без ржавчины без каких-либо существенных регрессий в стабильной версии.
> Учитывая, как быстро мы улучшаем компилятор и стандартные библиотеки, я думаю, что это действительно впечатляет (хотя, конечно, команда релизов здесь не является единственным участником). В целом, я обнаружил, что команда релизов проделала отличную работу по управлению масштабированием для увеличения трафика на трекерах, публикуемых PR и т. Д.
> - Марк Руссков ( [Выпуск] )

> За последние 3 года нам удалось превратить [Мири] из экспериментального интерпретатора в практический инструмент для изучения языкового дизайна и поиска ошибок в реальном коде - отличное сочетание теории и практики PL. С теоретической точки зрения у нас есть [Stacked Borrows] , самое конкретное предложение для модели псевдонимов Rust на данный момент. С практической точки зрения, хотя изначально мы проверяли только несколько ключевых библиотек в Miri, недавно мы увидели большое количество людей, использующих Miri для [поиска и исправления ошибок](https://github.com/rust-lang/miri/#bugs-found-by-miri) в своих собственных корзинах и зависимостях, и аналогичное распространение среди участников, улучшающих Miri, например: добавив поддержку доступа к файловой системе, раскручивания и параллелизма.
> - Ральф Юнг ( [Мири] )

> Если бы мне пришлось выбрать одну вещь, которой я больше всего горжусь, это была работа о нелексических жизнях (NLL). Это не только потому, что я думаю, что это сильно повлияло на удобство использования Rust, но и потому, что мы реализовали его, сформировав рабочую группу NLL. Эта рабочая группа привлекла много замечательных участников, многие из которых до сих пор работают над компилятором. Открытый исходный код в лучшем виде!
> - Нико Мацакис ( [Язык] )

## Общество

Поскольку язык изменился и сильно вырос за последние пять лет, изменилось и его сообщество. В Rust было написано очень много замечательных проектов, и присутствие Rust в производстве выросло в геометрической прогрессии. Мы хотели поделиться статистикой о том, насколько вырос Rust.

- Rust был признан [«Самым любимым программированием»] каждый год в последних четырех опросах разработчиков Stack Overflow, начиная с версии 1.0.
- Только в этом году мы обслужили более 2,25 петабайта (1PB = 1000 ТБ) различных версий компилятора, инструментов и документации!
- В то же время мы обслужили более 170 ТБ ящиков для примерно 1,8 миллиарда запросов на crates.io, удвоив ежемесячный трафик по сравнению с прошлым годом.

Когда Rust повернулся на 1.0, можно было подсчитать количество компаний, которые использовали его в производстве с одной стороны. Сегодня его используют сотни технологических компаний, а некоторые из крупнейших технологических компаний, таких как Apple, Amazon, Dropbox, Facebook, Google и Microsoft, решили использовать Rust для своей производительности, надежности и производительности в своих проектах.

## Вывод

Очевидно, что мы не смогли охватить все изменения или улучшения в Rust, которые произошли с 2015 года. Какими были ваши любимые изменения или новые любимые проекты Rust? Не стесняйтесь размещать свой ответ и обсуждение на [нашем форуме Discourse](TODO:%20CREATE%20FORUM%20POST%20BEFORE%20MERGE) .

Наконец, мы хотели бы поблагодарить всех, кто внес свой вклад в Rust, независимо от того, добавили ли вы новую функцию или исправили опечатку, ваша работа сделала Rust удивительным сегодня. Мы не можем дождаться, чтобы увидеть, как Rust и его сообщество будут продолжать расти и меняться, и посмотреть, что вы все будете строить с Rust в ближайшее десятилетие!


[анонсировала публичную предварительную версию своей официальной поддержки Rust для WinRT API!]: https://blogs.windows.com/windowsdeveloper/2020/04/30/rust-winrt-public-preview/
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
[Снимок экрана с сообщением об ошибке 1.43.0.]:  /images/2020-05-15-five-years-of-rust/borrow-error-1.2.0.png
[Мири]: /images/2020-05-15-five-years-of-rust/borrow-error-1.43.0.png
[Stacked Borrows]:    /images/2020-05-15-five-years-of-rust/help-error-1.2.0.png
[Рустдок]:   /images/2020-05-15-five-years-of-rust/help-error-1.43.0.png
[IDE и редакторы]:   /images/2020-05-15-five-years-of-rust/trait-error-1.2.0.png
[Embedded WG]:  /images/2020-05-15-five-years-of-rust/trait-error-1.43.0.png
[Выпуск]: https://github.com/rust-lang/miri
[Мири]: https://github.com/rust-lang/unsafe-code-guidelines/blob/master/wip/stacked-borrows.md
[Язык]:  https://github.com/rust-lang/miri/#bugs-found-by-miri
[«Самым любимым программированием»]: https://www.rust-lang.org/governance/teams/rustdoc