Памятка по синтаксису `Go` в примерах.

---

Подборка полезных и бесплатных ресурсов для изучения [Go](https://go.dev/learn) на русском языке:

- [Эффективный Go](https://github.com/Konstantin8105/Effective_Go_RU) - перевод официальной документации [Effective Go](https://go.dev/doc/effective_go) (не завершен и устарел).
- [Эффективный Go](https://github.com/0x0FACED/effective-go-ru) - перевод от сентября 2024 года.
- [Go в примерах](https://github.com/region23/gobyexample.ru) - исходный код для сборки статического сайта [Go в примерах](https://gobyexample.ru) (форк [gobyexample](https://github.com/mmcgrana/gobyexample)).
- [Введение в программирование на Go](https://github.com/maxpoletaev/golang-book) ([веб-версия](http://golang-book.ru)) - перевод книги [An Introduction to Programming in Go](https://www.golang-book.com).
- [Маленькая книга о Go](https://github.com/sefus/the-little-go-book/blob/master/ru/go.md) - перевод [The Little Go Book](https://github.com/karlseguin/the-little-go-book).
- [Паттерны параллельного программирования Go](https://github.com/Konstantin8105/Go-pipelines).
- [Курс по изучению Golang для начинающих](https://golangify.com/go/kurs-izucheniya-golang-dlya-nachinayuschih).
- [Обучение программированию на языке Go](https://code-basics.com/ru/languages/go) в тренажере (онлайн компилятор).
- [Руководство по языку Go](https://metanit.com/go/tutorial) от *Metanit*.
- [Шпаргалка по Go](https://opensource.archium.org/index.php?title=Langauge_RU) (перевод с Немецкого языка).
- [GUI на Golang на GTK+ 3](https://github.com/jhekasoft/articles/blob/master/01_golang_gtk3/main.md).
- [Гайды Uber по написанию кода на Go](https://github.com/sau00/uber-go-guide-ru) - русский перевод [оригинального репозитория](https://github.com/uber-go/guide).
- [Разработка веб-сервисов на Golang](https://github.com/tyz910/golang-webservices?tab=readme-ov-file) - курс по Go от *Mail.Ru* на платформе Coursera.
- [Основы Go](https://start.practicum.yandex/go-basics) - бесплатный курс от *Яндекс Практикум*.
- [Основы Go](https://ru.hexlet.io/courses/go-basics) - бесплатный курс от *Хек Слет* (34 урока, 97 тестов и 37 упражнений в тренажере).
- Бесплатные курсы от *Stepik* с получением сертификата:
- - [Go - первое знакомство](https://stepik.org/course/100208/promo) - 42 урока, 110 тестов, 45 задач (20к учащихся, рейтинг: 4.9).
- - [PRO Go. Основы программирования](https://stepik.org/course/158385/promo) - 38 урока, 121 тестов, 191 задач (13к учащихся, рейтинг: 4.8).
- - [Программирование на Golang](https://stepik.org/course/54403/promo) - 35 урока, 64 тестов, 94 задач (65к учащихся, рейтинг: 4.7).
- Быстрые шпаргалки:
- - [Go Cheat Sheets](https://cheatsheets.zip/go) от [Reference](https://github.com/Fechin/reference).
- - [Go Cheat Sheets](https://devhints.io/go) от [Devhints](https://github.com/rstacruz/cheatsheets).
- - [Изучите Go за Y минут](https://learnxinyminutes.com/docs/ru-ru/go-ru) от [Learn X in Y minutes](https://github.com/adambard/learnxinyminutes-docs).
<!-- - - [Go Cheat Sheet Ru](https://github.com/Lifailon/golang-cheat-sheet-ru) - перевод оригинального [репозитория](https://github.com/a8m/golang-cheat-sheet) на русский язык. -->

Вы можете использовать [онлайн компилятор](https://go.dev/play) на официальном сайте для запуска блоков кода, а также пройти [интерактивный тур](https://go.dev/tour/welcome/1).

---

Навигация:

- [Переменные и типы данных](#переменные-и-типы-данных)
- [Массивы и слайсы](#массивы-и-слайсы)
- [Функции](#функции)
- [Условия и циклы](#условия-и-циклы)
- [Обработка ошибок](#обработка-ошибок)
- [Горутины](#горутины)
- [Каналы и селекторы](#каналы-и-селекторы)
- [Регулярные выражения](#регулярные-выражения)
- [Математические вычисления](#математические-вычисления)
- [HTTP](#http)
- [OS](#os)

---

### Переменные и типы данных

```go
package main

import "fmt"

func main() {
    var a int = 10          // целое число
    var b float64 = 3.14    // дробное число
    var c string = "GoLang" // строка
    var d bool = true       // логический тип
    var e bool = false
    // Вывод значений
    fmt.Println("int:", a, "float:", b, "string:", c, "bool:", d, "and", e)
    // Автоматическое опредиление типа данных
    f := 42
    fmt.Println("Short declaration: " + f)
}
```

### Массивы и слайсы

```go
package main

import "fmt"

func main() {
    // Массив фиксированного размера с 5-ю элементами, все элементы инициализируются значением 0 (по умолчанию для типа int)
    var arr [5]int
    // Присвоить значения указанным элементам массива по индексу
    arr[0] = 1
    arr[1] = 2
    fmt.Println("Array:", arr)
    
    // Слайсы (массивы переменной длины)
    slice := []int{1, 2, 3, 4, 5}
    // Добавить новое значение в массив с помощью функции append
    slice = append(slice, 6)
    // Удалить элемент с индексом 5
    index := 4
    // Создается 2 слайса с начала до указанного индекса и срез с следующего элемента после индекса (+1) до конца слайса
    slice = append(slice[:index], slice[index+1:]...)
    fmt.Println("Slice:", slice) // [1, 2, 3, 4, 6]
    // Вывести срез слайсов по индексу с 1 и до 4 (по 3, не включая 4) элемент
    fmt.Println(slice[1:4]) // [2, 3, 4]
    // Очистить слайс (удалить все элементы)
    slice = slice[:0] // []
    fmt.Println(len(slice) == 0) // true
    // Объединение двух слайсов
    slice1 := []int{1, 2}
    slice2 := []int{3, 4}
    combined := append(slice1, slice2...)
    fmt.Println(combined) // [1, 2, 3, 4]

    // Слайс с заданной вместимостью:
    makeSlice := make([]int, 5, 10)
    fmt.Println(makeSlice) // [0 0 0 0 0]
    fmt.Println(cap(makeSlice)) // 10

    // Создаем пустую карту (map) с ключами типа string и значениями типа int
    m := make(map[string]int)
    m["Day"] = 30       // добавляем элемент с ключом "Day" и значением 30
    m["Day"] = 31       // обновляем  значение для ключа
    m["Month"] = 12
    fmt.Println(m) // map[Day:31 Month:12]
    // Создать карту с заданными значениями
    m2 := map[string]int{
        "Day": 31,
        "Month": 12,
    }
    // Читаем значение
    value := m2["Day"]
    fmt.Println(value) // 31
    // Если ключа нет в карте, то получаем нулевое значение для типа значения
    value, exists := m["Year"]
    fmt.Println(value, exists) // 0 false
    // Удалить элемент
    delete(m, "Day")
    fmt.Println(m) // map[Month:12]
}
```

### Функции

```go
package main

import "fmt"

// Функция сложения двух чисел
func add(a int, b int) int {
    return a + b
}

// Функция с несколькими возвращаемыми значениями
func divide(a, b int) (int, int) {
    return a / b, a % b // деление и вычисления остатка от деления двух целых чисел
}

func main() {
    sum := add(2, 2)
    fmt.Println("Сумма:", sum)

    quotient, remainder := divide(10, 3)
    fmt.Println("Результат:", quotient, "Остаток:", remainder) // Результат: 3 Остаток: 1
}
```

### Условия и циклы

```go
package main

import "fmt"

// Функция, возвращающая название месяца через условную конструкцию switch
func getMonthName(month int) string {
    switch month {
    case 1:
        return "January"
    case 2:
        return "February"
    case 3:
        return "March"
    case 4:
        return "April"
    case 5:
        return "May"
    case 6:
        return "June"
    case 7:
        return "July"
    case 8:
        return "August"
    case 9:
        return "September"
    case 10:
        return "October"
    case 11:
        return "November"
    case 12:
        return "December"
    default:
        return "Invalid month (range: 1-12)"
    }
}

// Второй вариант функции через классическое условие по индеку массива
func getMonthName2(month int) string {
    months := []string{"", "January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"}
    if month >= 1 && month <= 12 {
        return months[month]
    }
    return "Invalid month"
}

func main() {
    // Классический цикл из 13-ти итераций
    for i := 1; i <= 13; i++ {
        fmt.Printf("Month %d: %s\n", i, getMonthName(i))
    }

    // Увеличение индекса итерации в теле цикла
    j := 1
    for j <= 13 {
        fmt.Printf("Month %d: %s\n", j, getMonthName(j))
        j++
    }

    // Бесконечный цикл
    months := []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12}
    k := 0
    for {
        // Пропускаем итерацию, если 6-й месяц (5-й индекс)
        if k == 5 {
            k++ // переход к следующей итерации
            continue
        }
        // Выходим из цикла, если индекс больше или равен длине массива
        if k >= len(months) {
            break
        }
        fmt.Printf("Month %d: %s\n", months[k], getMonthName(months[k]))
        k++
    }

    // Конструкция range используется для перебора всех элементов в коллекциях (массивы, слайсы, карты и каналы)
    for _, month := range months {
        fmt.Printf("Month %d: %s\n", month, getMonthName(month))
    }

    // Индекс может использоваться для карты (map) как ключ
    m := map[string]int{"a": 1, "b": 2, "c": 3}
    for index, value := range m {
        fmt.Println("Key:", index, "Value:", value)
    }

    // Перебор строки по символам
    s := "string"
    for index, char := range s {
        fmt.Println("Index:", index, "Char:", string(char))
    }

    // Перебор канала
    ch := make(chan int, 3)
    ch <- 1
    ch <- 2
    ch <- 3
    close(ch)
    for val := range ch {
        fmt.Println(val)
    }
}
```

### Обработка ошибок

```go
package main

import (
    "errors"
    "fmt"
)

func divide(a, b int) (int, error) {
    if b == 0 {
        // Создаем объект типа error с текстовым описанием ошибки
        return 0, errors.New("division by zero")
    }
    // Возвращаем ошибку или пустое значение как второй результат функции
    return a / b, nil
}

func main() {
    result, err := divide(10, 0)
    if err != nil {
        fmt.Println("Error:", err)
    } else {
        fmt.Println("Result:", result)
    }
}
```

### Горутины

```go
package main

import (
    "fmt"
    "time"
)

func goRun() {
    // Симуляция работы
    time.Sleep(2 * time.Second)
    fmt.Println("Выполнение горутины завершено")
}

func main() {
    // Запуск горутины
    go goRun()
     // Основная функция продолжает работать параллельно
    fmt.Println("Запуск выполнения основной функции и ожидание завершения горутины")
    // Ждем завершения выполнения горутины
    time.Sleep(3 * time.Second)
}
```

### Каналы и селекторы

```go
package main

import (
    "fmt"
    "time"
    "sync"
)

func goRun(ch chan string) {
    time.Sleep(2 * time.Second)
    // Возвращяем сообщене о выполнение в канал
    ch <- "Первая горутина завершена за 2 секунды"
}

func goRunThree(ch chan string) {
    time.Sleep(3 * time.Second)
    ch <- "Вторая горутина завершена за 3 секунды"
}

func printMessage(msg string, wg *sync.WaitGroup) {
    // Уменьшает счётчик в WaitGroup, когда горутина завершена
    defer wg.Done()
    fmt.Println(msg)
}

func main() {
    // Создаем канал
    ch := make(chan string)
    // Запускаем горутину
    go goRun(ch)
    fmt.Println("Ожидаем завершения горутины в канале")
    // Блокируем main, пока не получим сообщение от горутины
    result := <-ch
    // После получения вывода, программа продолжает выполнение
    fmt.Println(result)

    // Создаем два канала и запускаем две горутины
    ch1 := make(chan string)
    ch2 := make(chan string)
    go goRun(ch1)
    go goRunThree(ch2)
    fmt.Println("Ожидаем завершения первой выполненной горутины")
    // Используем select для ожидания данных с двух каналов и выбора первого завершенного канала
    select {
    case msg1 := <-ch1:
        fmt.Println("Ответ:", msg1)
    case msg2 := <-ch2:
        fmt.Println("Ответ:", msg2)
    }
    
    // Создаем группу ожидания для синхронизации выполнения нескольких горутин
    var wg sync.WaitGroup
    fmt.Println("Ожидаем выполнения всех запущенных горутин")
    // Указать количество горутин, за которыми нужно следить
    wg.Add(2)
    go printMessage("Результат первой горутины", &wg)
    go printMessage("Результат второй горутины", &wg)
    // Ожидаем завершения всех горутин
    wg.Wait()
    fmt.Println("Все горутины завершили свою работу")
}
```

### Регулярные выражения

Основные элементы синтаксиса регулярных выражений:

- `.`       — любой символ, кроме символа новой строки.
- `*`       — 0 или более повторений.
- `+`       — 1 или более повторений.
- `{n}`     — точно `n` повторений (например, `a{3}`, соответствует: `"aaa"`).
- `{n,}`    — минимум `n` повторений (например, `a{2,}`, соответствует: `"aa"`, `"aaa"` и т.д.).
- `{n,m}`   — от n до m повторений (например, `a{2,4}`, соответствует: `"aa"`, `"aaa"`, `"aaaa"`).
- `?`       — 0 или 1 повторений.
- `^`       — начало строки.
- `$`       — конец строки.
- `[]`      — группа символов (например, `[a-z]`).
- `\s`      — любой пробельный символ (пробел, табуляция, новая строка и другие пробельные символы).
- `\d`      — любая цифра (эквивалентно `[0-9]`).
- `\D`      — любой символ, который не является цифрой (эквивалентно `[^0-9]`).
- `\w `     — любой буквенно-цифровой символ (буквы, цифры и символ подчеркивания, эквивалентно `[a-zA-Z0-9_]`).
- `\W`      — любой символ, не являющийся буквенно-цифровым (эквивалентно `[^a-zA-Z0-9_]`).
- `\b`      — граница целого слова (например, `\bword\b`, соответствует только целому словосочетанию `"word"`, и не подхоит слово `"wordy"`).
- `(?i)`    — делает регулярное выражение нечувствительным к регистру (игнорирует большие и маленькие буквы).
- `\`       — экранирует специальные символы.
- `()`      — группа захвата.
- `|`       — логическое ИЛИ (например, `a|b`).
- `(?=...)`   — позитивный просмотр вперёд (positive lookahead), проверяет, что за текущей позицией идет то, что описано в скобках.
- `\d(?=\s)`  — находит цифры, за которыми идет пробел (но сам пробел не входит в результат).
- `(?!...)`   — негативный просмотр вперёд (negative lookahead), проверяет, что за текущей позицией не идет то, что описано в скобках.
- `\d(?!\s)`  — находит цифры, за которыми не идет пробел.
- `(?<=...)`  — позитивный просмотр назад (positive lookbehind), проверяет, что перед текущей позицией находится то, что описано в скобках.
- `(?<=@)\w+` — находит слово, стоящее после символа `"@"` (например доменное имя, в адресах электронной почты).
- `(?<!...)`  — негативный просмотр назад (negative lookbehind), проверяет, что перед текущей позицией не находится то, что описано в скобках.
- `(?<!@)\w+` — находит слово, перед которым не стоит символ `"@"`.

Основные функции пакета `regexp`:

- `regexp.MatchString` — проверяет, соответствует ли строка регулярному выражению.

```go
package main

import (
	"fmt"
	"regexp"
)

func main() {
    pattern := `^[a-z]+$`
	str := "string"
    matched, err := regexp.MatchString(pattern, str)
	if err != nil {
		fmt.Println("Ошибка в регулярном выражении:", err)
		return
	}
	fmt.Printf("Строка '%s' соответствует регулярному выражению '%s' (результат: %v)", str, pattern, matched)
}
```

- `regexp.Compile` — компилирует регулярное выражение и возвращает объект типа `*regexp.Regexp`, если выражение корректное, или возвращается ошибка.

```go
package main

import (
    "fmt"
    "regexp"
)

func main() {
    // Компилируем регулярное выражение
    r, err := regexp.Compile(`\d+`)
    if err != nil {
        fmt.Println("Ошибка компиляции регулярного выражения:", err)
        return
    }
    // Применяем регулярное выражение к строке
    fmt.Println(r.FindString("123 abc 456")) // 123
}
```

- `regexp.FindAllString` — находит все подстроки в строке, которые соответствуют регулярному выражению, и возвращает их в виде среза строк.

```go
package main

import (
    "fmt"
    "regexp"
)

func main() {
    r, err := regexp.Compile(`\d+`)
    if err != nil {
        fmt.Println("Ошибка компиляции регулярного выражения:", err)
        return
    }
    matches := r.FindAllString("123abc456", -1)
    fmt.Println(matches) // [123 456]
}
```

- `regexp.ReplaceAllString` — заменяет все соответствующие части строки.

```go
package main

import (
    "fmt"
    "regexp"
)

func main() {
    pattern := `\d+`
    str := "Диапазон от 1 до 10"
    // Заменяем все цифры на "X"
    r, err := regexp.Compile(pattern)
    if err != nil {
        fmt.Println("Ошибка компиляции регулярного выражения:", err)
        return
    }
    result := r.ReplaceAllString(str, "X")
    fmt.Println(result)
}
```

- Группы захвата

```go
package main

import (
    "fmt"
    "regexp"
)

func main() {
    // Регулярное выражение с группой захвата для даты в формате "dd.mm.yyyy"
    pattern := `(\d{2}).(\d{2}).(\d{4})`
    r, err := regexp.Compile(pattern)
    if err != nil {
        fmt.Println("Ошибка компиляции регулярного выражения:", err)
        return
    }
    // Поиск и извлечение данных
    result := r.FindStringSubmatch("01.12.2024")
    if len(result) > 0 {
        fmt.Println("День:", result[1])
        fmt.Println("Месяц:", result[2])
        fmt.Println("Год:", result[3])
    }
}
```

- Извлечение логина и домена из почтовых адресов

```go
package main

import (
    "fmt"
    "regexp"
)

func main() {
    pattern := `([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+\.[a-zA-Z]{2,})`
    str := "contact@example.com, support@example.net"
    r, err := regexp.Compile(pattern)
    if err != nil {
        fmt.Println("Ошибка компиляции регулярного выражения:", err)
        return
    }
    matches := r.FindAllStringSubmatch(str, -1)
    for _, match := range matches {
        fmt.Printf("Логин: %s, Домен: %s\n", match[1], match[2])
    }
}
```

### Математические вычисления

```go
package main

import (
	"fmt"
	"math"
)

func customCeil(numerator int, denominator int) int {
    result := numerator / denominator
    if numerator%denominator != 0 {
        result++
    }
    return result
}

func main() {
    fmt.Println("Возвращает наименьшее значение из двух чисел 9 и 10:", math.Min(9, 10)) // 9
    fmt.Println("Возвращает наибольшее значение из двух чисел 9 и 10:", math.Max(9, 10)) // 10
    fmt.Println("Округляет число в меньшую сторону 10 / 3:", math.Floor(10/3)) // 3
    fmt.Println("Округляет число в большую сторону 10 / 3:", math.Ceil(10.0/3))
    fmt.Println("Округляет число в большую сторону 10 / 3:", customCeil(10, 3)) // 4
    fmt.Println("Отбрасывает дробную часть числа (не округляет) 4,9:", math.Trunc(4.9)) // 4
    fmt.Println("Округляет число до ближайшего целого в большую сторону от 4,5:", math.Round(4.5)) // 5
    fmt.Println("Округляет число до ближайшего целого в меньшую сторону от 4,5:", math.Round(4.45)) // 4
    fmt.Println("Возвращает абсолютное значение числа -7:", math.Abs(-7)) // 7
    fmt.Println("Возводит число 2 в степень 3:", math.Pow(2, 3)) // 8
    fmt.Println("Вычисляет квадратный корень числа 16:", math.Sqrt(16)) // 4
}
```

### HTTP

HTTP запрос к GitHub API для получения последней версии релиза указаного репозитория.

```go
package main

import (
	"encoding/json"
	"fmt"
	"log"
	"net/http"
)

// Структура для ответа от GitHub API
type GitHubRelease struct {
	TagName string `json:"tag_name"`
}

func main() {
	// URL для получения информации о последней версии релиза
    repos := "Lifailon/lazyjournal"
	url := fmt.Sprintf("https://api.github.com/repos/%s/releases/latest", repos)
	// Выполнение GET-запроса
	resp, err := http.Get(url)
	if err != nil {
		log.Fatal("Ошибка при выполнении запроса:", err)
	}
	defer resp.Body.Close()
	// Проверка на успешный ответ
	if resp.StatusCode != http.StatusOK {
		log.Fatalf("Ошибка HTTP: %s", resp.Status)
	}
	// Декодирование JSON-ответа в заданную структуру
	var release GitHubRelease
	err = json.NewDecoder(resp.Body).Decode(&release)
	if err != nil {
		log.Fatal("Ошибка при декодировании JSON:", err)
	}
	// Вывод последней версии
	fmt.Println("Latest version:", release.TagName)
}
```

### OS

Проверка доступности всех хостов в указанной подсети (асинхронный ICMP опрос).

```go
package main

import (
	"fmt"
	"os"
	"os/exec"
	"strings"
	"sync"
)

func pingHost(ip string, wg *sync.WaitGroup) {
	defer wg.Done()
	// Запускаем команду ping
	cmd := exec.Command("ping", "-n", "1", ip)
	output, err := cmd.CombinedOutput()
	if err != nil {
		return
	}
	// Обрабатываем вывод команды
	if strings.Contains(string(output), "TTL=") {
		fmt.Printf("%s - доступен\n", ip)
	}
}

func main() {
	if len(os.Args) < 2 {
		fmt.Println("Использование: go run main.go <подсеть>")
		return
	}
	// Извлекаем аргумент
	subnet := os.Args[1]
	// Убираем последний октет
	ipBase := subnet[:len(subnet)-1]
	var wg sync.WaitGroup
	for i := 1; i <= 254; i++ {
		ip := fmt.Sprintf("%s%d", ipBase, i)
		wg.Add(1)
		// Запускаем асинхронный пинг
		go pingHost(ip, &wg)
	}
	// Ждем завершения всех горутин
	wg.Wait()
}
```

`go run main.go 192.168.3.0`
