# Java проект (сумма двух чисел)

## Maven + junit (Параметризованный тест)

```sh
mvn package
```

Дерево

```sh
├── pom.xml
├── README.md
├── src
    ├── main
    │   └── java
    │       └── calculator
    │           └── Calculator.java
    └── test
        └── java
            └── calculator
                └── CalculatorTest.java
```

 Calculator.java

```java
package calculator;
public class Calculator {

	public int add(int a, int b) {
		return a + b;
	}

}
```

CalculatorTest.java

```java
package calculator;

import static org.junit.jupiter.api.Assertions.assertEquals;

import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.CsvSource;

class CalculatorTests {

	@Test
	@DisplayName("1 + 1 = 2")
	void addsTwoNumbers() {
		Calculator calculator = new Calculator();
		assertEquals(2, calculator.add(1, 1), "1 + 1 should equal 2");
	}

	@ParameterizedTest(name = "{0} + {1} = {2}")
	@CsvSource({
			"0,    1,   1",
			"1,    2,   3",
			"49,  51, 100",
			"1,  100, 101"
	})
	void add(int first, int second, int expectedResult) {
		Calculator calculator = new Calculator();
		assertEquals(expectedResult, calculator.add(first, second),
				() -> first + " + " + second + " should equal " + expectedResult);
	}
}
```java
