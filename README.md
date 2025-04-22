Explicações claras sobre o uso de *Generic Methods* e *Bounded Type Parameters*:

---

# 📦 Max Product Finder

Este projeto Java lê um arquivo CSV contendo produtos e seus respectivos preços, e determina qual é o produto mais caro.
Utilizando conceitos de **métodos genéricos** e **parâmetros de tipo limitados (bounded type parameters)**.

## 🧠 Conceitos principais

- **Programação Genérica (Generics)**
- **Bounded Type Parameters**
- **Interface Comparable**
- **Leitura de arquivos CSV**
- **Tratamento de exceções**
- **Boas práticas com orientação a objetos**

---

## 📂 Estrutura do Projeto

```bash
src/
├── application/
│   └── Program.java
├── entities/
│   └── Product.java
└── services/
    └── CalculationService.java
```

---

## 🔍 Funcionamento

O programa:

1. Lê os dados de um arquivo CSV com o caminho especificado (`ProductName,Price`);
2. Armazena os produtos em uma lista (`List<Product>`);
3. Utiliza o método genérico `max()` para encontrar o produto mais caro da lista;
4. Imprime o resultado no console.

---

## 💡 Generic Methods & Bounded Type Parameters

O destaque deste projeto está no uso de **métodos genéricos com restrição de tipo**:

```java
public static <T extends Comparable<T>> T max(List<T> list)
```

### 🧾 Explicação

- `<T extends Comparable<T>>`: define um **parâmetro de tipo genérico T**, que **deve implementar** a interface `Comparable<T>`.
- Isso garante que qualquer objeto passado para esse método possa ser **comparado** com os outros da mesma lista usando `compareTo()`.

### ✅ Vantagens

- **Reutilizável**: o método `max` funciona com qualquer tipo de objeto que implemente `Comparable`, não apenas com `Product`.
- **Seguro em tempo de compilação**: evita erros ao tentar comparar objetos que não suportam ordenação.

### 💬 Exemplo com `Product`

A classe `Product` implementa `Comparable<Product>`, o que permite que seus objetos sejam comparados por preço:

```java
@Override
public int compareTo(Product other) {
    return price.compareTo(other.getPrice());
}
```

---

## 📁 Exemplo de CSV

```csv
TV,1000.00
Notebook,1500.00
Tablet,400.00
```

---

## ▶️ Execução

- Certifique-se de que o caminho do arquivo CSV está correto no código:

```java
String path = "C:\\Temp\\Product.CSV";
```

- Compile e execute:

```bash
javac application/Program.java
java application.Program
```

---

## 🧪 Exemplo de Saída

```
Most expensive: Notebook, 1500.00
```

---

## 📌 Requisitos

- Java 8+
- IDE como Eclipse ou IntelliJ (opcional)
- Arquivo CSV no formato correto

---

## 📘 Referências

- [Java Generics](https://docs.oracle.com/javase/tutorial/java/generics/)
- [Comparable Interface](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html)

---
