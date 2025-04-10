# Код стайл ТОСК iOS

### Правила

Марки в классах и структурах
``` Swift
final class SomeClass {
    // MARK: - Types
    ...
    
    // MARK: - Overridden Properties
    ...
    
    // MARK: - Private Properties
    ...
    
    // MARK: - Initializer
    ...
    
    // MARK: - Overridden Methods
    ...
}
```

Экшоны, приватные, публичные методы и методы наследуемых классов выносятся в экстеншоны (марки за областью видимости класса/структуры обособляются тире: - ... -)

Правильный порядок экстеншенов с марками:

``` Swift
// MARK: - UITableViewDelegate -
extension SomeClass: UITableViewDelegate {
    ...
}

// MARK: - Public Methods -
extension SomeClass {
    ...
}

// MARK: - Actions -
@objc private extension SomeClass {
    ...
}

// MARK: - Private Methods -
private extension SomeClass {
    ...
}
```

Все классы помечаются как ```final``` (если нет нужды делать его наследуемым)

``` Swift
final class SomeClass {
    ...
}
```

Модификатор для пременных:

``` Swift
// Публичная переменная
let someValue: Int = 0

// Публичная переменная с доступом к значению
private(set) var someProperty: UIColor?

// Приватная переменная
private let someString: String = ""
```

Переменные по приоритету должны быть ```private let``` если нет необходимости их изменять или открывать к ним доступ из дургих классов

Модификаторы методов:

``` Swift
// Публчный метод
func somePublicMethod() {
    ...
}

// Приватный метод
private func somePrivateMethod() {
    ...
}
```

Пример работы с UI:

``` Swift
import SnapKit

private let titleLabel = UILabel()
private let iconImageView = UIImageView()

func setupUI() {
    addSubviews()
    setupConstraints()
    setupLabel()
    setupIconImage()
}

func addSubviews() {
    addSubview(titleLabel)
    addSubview(iconImageView)
}

func setupConstraints() {
    titleLabel.snp.makeConstraints {
        ...
    }
    
    iconImageView.snp.makeConstraints {
        ...
    }
}


private func setupLabel() {
    titleLabel.text = "..."
    titleLabel.font = .systemFont(ofSize: 10)
    titleLabel.adjustsFontSizeToFitWidth = true
    titleLabel.minimumScaleFactor = 0.5
    ...
}

private func setupIconImage() {
    iconImageView.image = ...
}
```

Настройка для отслеживания максимальной ширины для кода:

____Xcode -> Settings... -> Text Editing -> Editing -> Reformat code at column - 120____

Пример переноса если код выходит за 120 символов:

``` Swift
guard
    let propertie,
    let value,
    let text
else {
    return
}

init(
    text: String,
    image: UIImage?,
    value: CGFloat
) {
    ...
}
```

Required init 

``` Swift
@available(*, unavailable)
required init?(coder: NSCoder) { nil }
```




