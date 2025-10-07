# BubbleSort_component

## Реализация компонента сортировки пузырьком в Eco OS

1. Общая постановка задачи
Необходимо создать новый компонент для Eco OS, который реализует алгоритм сортировки пузырьком для различных типов данных. Компонент должен предоставлять интерфейс с методами для сортировки массивов разных типов (int32_t, int64_t, float, double).

2. Реализуемый алгоритм сортировки пузырьком

2.1 Описание алгоритма
Алгоритм сортировки пузырьком - это простой алгоритм сортировки, который многократно проходит через массив, сравнивает соседние элементы и меняет их местами, если они находятся в неправильном порядке. Этот процесс повторяется до тех пор, пока массив не будет полностью отсортирован.

2.2 Основные шаги алгоритма:

* Инициализация: Начинаем с первого элемента массива

* Сравнение соседних элементов: Сравниваем текущий элемент со следующим

* Обмен элементов: Если текущий элемент больше следующего, меняем их местами

* Проход по массиву: Повторяем шаги 2-3 для всех элементов

* Проверка оптимизации: Если за проход не было ни одного обмена, массив отсортирован

* Повторение: Повторяем шаги 1-5 для оставшейся части массива

2.3 Псевдокод алгоритма:

для i от 0 до n-2:
    swapped = ложь
    для j от 0 до n-i-2:
        если array[j] > array[j+1]:
            поменять местами array[j] и array[j+1]
            swapped = истина
    если не swapped:
        прервать цикл

3. Асимптотическая сложность

Временная сложность:
* Худший случай: O(n²) - когда массив отсортирован в обратном порядке

* Лучший случай: O(n) - когда массив уже отсортирован

*Средний случай: O(n²)

*Сложность по памяти: O(1) - алгоритм использует только постоянное количество дополнительной памяти

4. Реализация компонента

typedef struct IEcoLab1VTbl {
    /* IEcoUnknown */
    int16_t (ECOCALLMETHOD *QueryInterface)(/* in */ IEcoLab1Ptr_t me, /* in */ const UGUID* riid, /* out */ voidptr_t* ppv);
    uint32_t (ECOCALLMETHOD *AddRef)(/* in */ IEcoLab1Ptr_t me);
    uint32_t (ECOCALLMETHOD *Release)(/* in */ IEcoLab1Ptr_t me);

    /* IEcoLab1 - методы сортировки пузырьком */
    int16_t (ECOCALLMETHOD *BubbleSortInt32)(/* in */ IEcoLab1Ptr_t me, /* in */ int32_t* array, /* in */ uint32_t size);
    int16_t (ECOCALLMETHOD *BubbleSortInt64)(/* in */ IEcoLab1Ptr_t me, /* in */ int64_t* array, /* in */ uint32_t size);
    int16_t (ECOCALLMETHOD *BubbleSortFloat)(/* in */ IEcoLab1Ptr_t me, /* in */ float* array, /* in */ uint32_t size);
    int16_t (ECOCALLMETHOD *BubbleSortDouble)(/* in */ IEcoLab1Ptr_t me, /* in */ double* array, /* in */ uint32_t size);
    int16_t (ECOCALLMETHOD *MyFunction)(/* in */ IEcoLab1Ptr_t me, /* in */ char_t* Name, /* out */ char_t** CopyName);

} IEcoLab1VTbl, *IEcoLab1VTblPtr;

interface IEcoLab1 {
    struct IEcoLab1VTbl *pVTbl;
} IEcoLab1;
