# Библиотека Heroes Task Library

Heroes Task Library — это библиотека на языке Java, предназначенная для интеграции с проектом Heroes. Она реализует четыре ключевых интерфейса, обеспечивающих игровой функционал, включая генерацию армии, симуляцию боя, выбор подходящих для атаки юнитов и поиск кратчайшего пути.

## Структура проекта
- **Цель библиотеки**: Реализация игровой механики для проекта Heroes.
- **JAR-файл**: Скомпилированный файл библиотеки доступен в каталоге `out/artifacts`.

## Реализованные интерфейсы и их сложность

### 1. **GeneratePreset**
- **Метод**: `Army generate(List<Unit> unitList, int maxPoints)`
- **Назначение**: Создаёт оптимальную армию компьютера на основе эффективности по стоимости и атакующим характеристикам.
- **Сложность**:
  - Сортировка юнитов: \( O(n \log n) \), где \( n \) — количество типов юнитов.
  - Генерация армии: \( O(n \cdot m) \), где \( m \) — максимальное количество юнитов одного типа.
  - Итоговая сложность: \( O(n \log n + n \cdot m) \).

### 2. **SimulateBattle**
- **Метод**: `void simulate(Army playerArmy, Army computerArmy)`
- **Назначение**: Симулирует бой между армией игрока и компьютера, выполняя атаки и управление ходами.
- **Сложность**:
  - Фильтрация живых юнитов: \( O(n) \) за раунд.
  - Сортировка юнитов по атаке: \( O(n \log n) \) за раунд.
  - Выполнение атак: \( O(n) \) за раунд.
  - Общее количество раундов: пропорционально \( n \).
  - Итоговая сложность: \( O(n^2 \log n) \).

### 3. **SuitableForAttackUnitsFinder**
- **Метод**: `List<Unit> getSuitableUnits(List<List<Unit>> unitsByRow, boolean isLeftArmyTarget)`
- **Назначение**: Определяет, какие юниты противника подходят для атаки, исключая заблокированные.
- **Сложность**:
  - Проход по рядам: \( O(1) \) (всего 3 фиксированных ряда).
  - Проверка юнитов в каждом ряду: \( O(n) \), где \( n \) — количество юнитов в ряду.
  - Итоговая сложность: \( O(n) \).

### 4. **UnitTargetPathFinder**
- **Метод**: `List<Edge> getTargetPath(Unit attackUnit, Unit targetUnit, List<Unit> existingUnitList)`
- **Назначение**: Находит кратчайший путь между атакующим и атакуемым юнитами с использованием алгоритма Дейкстры.
- **Сложность**:
  - Инициализация данных: \( O(WIDTH 	imes HEIGHT) \), где WIDTH = 27, HEIGHT = 21.
  - Поиск пути (алгоритм Дейкстры): \( O((WIDTH 	imes HEIGHT) \cdot \log(WIDTH 	imes HEIGHT)) \).
  - Построение пути: \( O(WIDTH 	imes HEIGHT) \).
  - Итоговая сложность: \( O((WIDTH 	imes HEIGHT) \cdot \log(WIDTH 	imes HEIGHT)) \).

## Использование
1. Подключите файл `out/artifacts/HeroesTaskLib.jar` к проекту Heroes.
2. Используйте предоставленные методы для реализации логики игры.

## Участие
Для предложений по улучшению библиотеки или сообщений об ошибках свяжитесь с разработчиком или создайте заявку в основном репозитории.

