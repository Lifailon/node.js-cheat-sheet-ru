Памятка по синтаксису `Go` в примерах.

---

Полезные ресурсы для изучения [Go](https://go.dev/learn) на русском языке:

- [Эффективный Go](https://github.com/0x0FACED/effective-go-ru) - перевод официальной документации [Effective Go](https://go.dev/doc/effective_go) от сентября 2024 года.
- [Эффективный Go](https://github.com/Konstantin8105/Effective_Go_RU) - перевод не завершен и устарел.
- [Go в примерах](https://github.com/region23/gobyexample.ru) - исходный код для сборки статического сайта [Go в примерах](https://gobyexample.ru).
- [Введение в программирование на Go](https://github.com/maxpoletaev/golang-book) ([веб-версия](http://golang-book.ru)) - перевод книги [An Introduction to Programming in Go](https://www.golang-book.com).
- [Маленькая книга о Go](https://github.com/sefus/the-little-go-book/blob/master/ru/go.md) - перевод [The Little Go Book](https://github.com/karlseguin/the-little-go-book).
- [Паттерны параллельного программирования Go](https://github.com/Konstantin8105/Go-pipelines).
- [Гайды Uber по написанию кода на Go](https://github.com/sau00/uber-go-guide-ru) - русский перевод [оригинального репозитория](https://github.com/uber-go/guide).
- [Разработка веб-сервисов на Golang](https://github.com/tyz910/golang-webservices?tab=readme-ov-file) - курс по Go от Mail.Ru на платформе Coursera.
- [Шпаргалка по Go](https://opensource.archium.org/index.php?title=Langauge_RU) - перевод с Немецкого языка.
- [GUI на Golang на GTK+ 3](https://github.com/jhekasoft/articles/blob/master/01_golang_gtk3/main.md).

---

Навигация:

- [Переменные и типы данных](#переменные-и-типы-данных)
- [Массивы и объекты](#массивы-и-объекты)
- [Функции](#функции)
- [Условия и циклы](#условия-и-циклы)
- [Обработка ошибок](#обработка-ошибок)
- [Асинхронные операции](#асинхронные-операции)
- [Регулярные выражения](#регулярные-выражения)

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

### Массивы и объекты

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
    index := 5
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
    return a / b, a % b // обычное деление и вычисления остатка от деления двух целых чисел
}

func main() {
    sum := add(2, 2)
    fmt.Println("Sum:", sum)

    quotient, remainder := divide(10, 3)
    fmt.Println("Quotient:", quotient, "Remainder:", remainder)
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
    for index, month := range months {
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

### Асинхронные операции

```go

```

### Регулярные выражения

```go

```