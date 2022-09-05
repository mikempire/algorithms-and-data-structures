# Алгоритмы и структуры данных в javascript

## Алгоритм линейного поиска в массиве(Linear Search):

```javascript
const array = [1, 4, 5, 8, 5, 1, 2, 7, 5, 2, 11];

let count = 0;

function linearSearch(array, item) {
  for (let i = 0; i < array.length; i++) {
    // count - количество итераций
    count += 1;
    if (array[i] === item) {
      // Возвращаем индекс элемента при нахождении
      return i;
    }
  }
  // Возвращаем null если элемент не найден
  return null;
}
```

## Бинарный поиск (Binary Search):

```javascript
const array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15];
let count = 0;

// Реализация с помощью цикла.
// Суть: Находим средний элемент массива, если он равен искомогу, то возращаем его индекс.
// Если больше, то орезаем правую часть, а если меньше, то левую.
function binarySearch(array, item) {
  // Позиция первого элемента
  let start = 0;
  // Позиция последнего элемента
  let end = array.length;
  // Позиция среднего элемента в массиве
  let middle;
  // Флаг, который показывает найден ли элемент в массиве
  let found = false;
  // Позиция найденого элемента. Если элемент не найден, то возвращаем -1
  let position = -1;
  // Цикл работатет до тех пор либо пока не найден элемент, либо пока стартовая и конечная позиция не поровнялись.
  while (found === false && start <= end) {
    // Кол-во итераций
    count += 1;

    // Внутри цикла высчитываем позицию центрального элемента
    middle = Math.floor((start + end) / 2);
    // Если он равен искомому элементу, то возвращаем позицию элемента
    if (array[middle] === item) {
      found = true;
      position = middle;
      return position;
    }
    // Если нужный элемент меньше центрального, то тогда нужна левая часть массива, поэтму отсекаем правую.
    if (item < array[middle]) {
      end = middle - 1;
    } else {
      // Если больше, то обрезаем всю левую часть массива
      start = middle + 1;
    }
  }
  return position;
}
```

## Сортировка выбором(Selection Sort):

```javascript
const arr = [
  0, 3, 2, 5, 6, 8, 1, 9, 4, 2, 1, 2, 9, 6, 4, 1, 7, -1, -5, 23, 6, 2, 35, 6, 3,
  32,
];
let count = 0;

// Суть: Есть массив неупорядоченных элементов. Находим в цикле минимальный элемент,
// затем меняем местами с первым элементом, затем опять пробегаемся по массиву и находим минимальное значение,
// но меняем его уже со вторым элементом, затем с 3,4 итд пока не будет отсортирован весь массив.
function selectionSort(array) {
  // Этот цикл просто идет по всем элементам
  for (let i = 0; i < array.length; i++) {
    let indexMin = i;
    // Во вложенном цикле ищется минимальный элемент на данную итерацию
    for (let j = i + 1; j < array.length; j++) {
      if (array[j] < array[indexMin]) {
        indexMin = j;
      }
      count += 1;
    }

    // Меняем местами элементы
    let tmp = array[i];
    array[i] = array[indexMin];
    array[indexMin] = tmp;
  }

  // Возвращаем отсортированный массив
  return array;
}

// Кол-во итераций 325. Длина массива 26. Таким образом O(1/2*n*n),
// но коэффициенты в оценке сложности алгоритма не учавствуют. Поэтому будет O(n*n)
console.log(selectionSort(arr));
console.log(arr.length);
console.log("count = ", count);
```

## Пузыкрьковая сортировка(Bubble Sort):

```javascript
const arr = [
  0, 3, 2, 5, 6, 8, 23, 9, 4, 2, 1, 2, 9, 6, 4, 1, 7, -1, -5, 23, 6, 2, 35, 6,
  3, 32, 9, 4, 2, 1, 2, 9, 6, 4, 1, 7, -1, -5, 23, 9, 4, 2, 1, 2, 9, 6, 4, 1, 7,
  -1, -5, 23,
];
let count = 0;

// Суть: в двойном цикле пробегаемся по всему массиву и сравниваем попарно лежащие элементы.
// Если следующий элемент массива меньше чем предыдуший, то мы меняем их местами.
// Получается "всплытие" самый большой элемент с каждой итерацией потихоньку всплывает наверх.
function bubbleSort(array) {
  for (let i = 0; i < array.length; i++) {
    for (let j = 0; j < array.length; j++) {
      if (array[j + 1] < array[j]) {
        let tmp = array[j];
        array[j] = array[j + 1];
        array[j + 1] = tmp;
      }
      count += 1;
    }
  }
  return array;
}

console.log("length", arr.length);
console.log(bubbleSort(arr)); // O(n*n)
console.log("count = ", count);
```
