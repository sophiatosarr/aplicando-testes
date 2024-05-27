# Aplicando Testes em .NET 5

## Introdução
Este repositório foi criado com o objetivo de demonstrar a aplicação de testes unitários em aplicações baseadas no .NET 5. Os testes foram implementados utilizando os frameworks xUnit, NUnit e MSTest.
Cada seção contém uma descrição detalhada dos testes e exemplos de cenários.

## Testes com xUnit

### Descrição
xUnit é um framework popular para testes unitários no .NET. Ele utiliza os atributos `Theory` e `InlineData` para criar testes parametrizados, o que facilita a criação de múltiplos cenários de teste com diferentes entradas e saídas esperadas.

### Exemplos de Cenários

1. **Conversão de 32°F para Celsius**
   - Entrada: 32°F
   - Saída esperada: 0°C

2. **Conversão de 212°F para Celsius**
   - Entrada: 212°F
   - Saída esperada: 100°C

### Código de Teste

```csharp
public class TemperatureConversionTests
{
    [Theory]
    [InlineData(32, 0)]
    [InlineData(212, 100)]
    public void ConvertFahrenheitToCelsius(double fahrenheit, double expectedCelsius)
    {
        // Arrange
        var converter = new TemperatureConverter();

        // Act
        var actualCelsius = converter.ConvertFahrenheitToCelsius(fahrenheit);

        // Assert
        Assert.Equal(expectedCelsius, actualCelsius);
    }
} 

```

## Testes com NUnit

### Descrição
NUnit é outro framework amplamente utilizado para testes unitários no .NET. Ele usa o atributo `TestCase` para definir testes parametrizados, permitindo especificar múltiplos conjuntos de entradas e saídas esperadas diretamente nos métodos de teste.

### Exemplos de Cenários

- **Conversão de 32°F para Celsius**
  - Entrada: 32°F
  - Saída esperada: 0°C

- **Conversão de 212°F para Celsius**
  - Entrada: 212°F
  - Saída esperada: 100°C

### Código de Teste

```csharp
public class TemperatureConversionTests
{
    [TestCase(32, 0)]
    [TestCase(212, 100)]
    public void ConvertFahrenheitToCelsius(double fahrenheit, double expectedCelsius)
    {
        // Arrange
        var converter = new TemperatureConverter();

        // Act
        var actualCelsius = converter.ConvertFahrenheitToCelsius(fahrenheit);

        // Assert
        Assert.AreEqual(expectedCelsius, actualCelsius);
    }
}
```


## Testes com MSTest

### Descrição
MSTest é o framework de testes oficial da Microsoft para o .NET. Ele utiliza os atributos `DataTestMethod` e `DataRow` para criar testes parametrizados, permitindo a definição de múltiplos casos de teste com diferentes entradas e saídas esperadas.

### Exemplos de Cenários

- **Conversão de 32°F para Celsius**
  - Entrada: 32°F
  - Saída esperada: 0°C

- **Conversão de 212°F para Celsius**
  - Entrada: 212°F
  - Saída esperada: 100°C

### Código de Teste

```csharp
[TestClass]
public class TemperatureConversionTests
{
    [DataTestMethod]
    [DataRow(32, 0)]
    [DataRow(212, 100)]
    public void ConvertFahrenheitToCelsius(double fahrenheit, double expectedCelsius)
    {
        // Arrange
        var converter = new TemperatureConverter();

        // Act
        var actualCelsius = converter.ConvertFahrenheitToCelsius(fahrenheit);

        // Assert
        Assert.AreEqual(expectedCelsius, actualCelsius);
    }
}
```
