### 1. Що таке immutable об’єкт? Для чого об’єкти класу `String` зробили імутабельними? Чому клас `String` задекларований як `final`?

**Імутабельний об'єкт (immutable object)** — це об'єкт, стан якого не може бути змінено після створення. Якщо необхідно змінити дані, створюється новий об'єкт.

#### Чому клас `String` імутабельний:
- **Безпека**: Імутабельність забезпечує безпечне використання рядків у багатопотокових середовищах без необхідності синхронізації.
- **Кешування**: Завдяки імутабельності рядки можна кешувати, наприклад, у пулі рядків (String Pool), що оптимізує використання пам’яті.
- **Ефективність**: Імутабельність дозволяє використовувати рядки як ключі в колекціях (`HashMap`, `HashSet`), гарантуючи стабільність їхніх значень.
- **Захист від зміни**: Імутабельність запобігає змінам рядків, переданих як параметри методів.

#### Чому клас `String` задекларований як `final`:
- **Захист імутабельності**: Якщо клас `String` не буде `final`, то його можна було б успадкувати і змінити поведінку, порушивши імутабельність.

---

### 2. Що таке регулярні вирази? Наведіть приклади регулярних виразів.

**Регулярні вирази (Regular Expressions)** — це шаблони для пошуку і обробки тексту, що дозволяють описувати складні правила роботи з рядками.

#### Приклади:
1. **Перевірка email**: `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$`
2. **Пошук чисел**: `\d+`
3. **Перевірка дати у форматі `dd/mm/yyyy`**: `^(0[1-9]|[12][0-9]|3[01])/(0[1-9]|1[0-2])/\d{4}$`
4. **Перевірка IP-адреси**: `^((25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$`

---

### 3. В чому полягає різниця між оператором `==` та методом `equals()`?

- **`==`**:
  - Порівнює **посилання на об’єкти**, тобто перевіряє, чи вказують дві змінні на один і той самий об’єкт у пам'яті.
  - Використовується для примітивних типів даних.

- **`equals()`**:
  - Використовується для порівняння **значень об’єктів**.
  - Для класу `String` метод `equals()` порівнює посимвольно значення рядків.

#### Приклад:
```java
String str1 = new String("hello");
String str2 = new String("hello");

System.out.println(str1 == str2);       // false (різні об'єкти в пам'яті)
System.out.println(str1.equals(str2)); // true (значення однакові)
```

---

### 4. Для чого потрібні класи `StringBuilder` та `StringBuffer`?

- **`StringBuilder`** і **`StringBuffer`** — класи для створення та модифікації змінюваних рядків.

#### Відмінності між ними:
- **`StringBuilder`**:
  - Використовується в однопотокових додатках.
  - Швидший, оскільки не синхронізований.

- **`StringBuffer`**:
  - Підходить для багатопотокових додатків.
  - Синхронізований, що робить його безпечним у багатопотоковому середовищі, але повільнішим.

#### Приклад використання:
```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb); // "Hello World"
```

---

### 5. Яким чином простіше всього прибрати пробіли на початку та кінці об’єкта `String`?

Найпростіший спосіб — використання методу `trim()`:
```java
String str = "   Hello World   ";
String trimmed = str.trim();
System.out.println(trimmed); // "Hello World"
```

Якщо потрібне видалення всіх пробілів (у тому числі зайвих між словами), можна використати `replaceAll()`:
```java
String str = "   Hello   World   ";
String result = str.replaceAll("\\s+", " ").trim();
System.out.println(result); // "Hello World"
```
