# estimativa-log

Módulo de log usado pelo [Estimativa de Projeto de Software](https://github.com/Tetzdesen/EstimativaDeProjetoDeSoftware), trabalho final de Projeto de Sistemas de Software (UFES).

Grava as operações do sistema (criação, alteração, exclusão, compartilhamento e exportação de projetos) em **CSV**, com campos separados por `;`, ou em **JSON**. Cada formato é um adaptador da interface `Logger`, e a troca pode ser feita com o programa rodando.

## Como usar

No `pom.xml`:

```xml
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>

<dependency>
    <groupId>com.github.Tetzdesen</groupId>
    <artifactId>estimativa-log</artifactId>
    <version>1.0.0</version>
</dependency>
```

No código:

```java
Logger log = LoggerFactory.criar(FormatoLog.CSV, Path.of("logs/estimativa"));
log.registrar(LogRegistro.sucesso("criação", "App de Delivery", "Mariana"));
// criação: App de Delivery, (02/11/2026, 14:30:00, e Mariana)

log.registrar(LogRegistro.falha("exclusão", "App de Delivery", "Mariana", "banco indisponível"));
// Ocorreu a falha banco indisponível ao realizar a exclusão do projeto App de Delivery, (02/11/2026, 14:30:00, e Mariana).
```

O arquivo recebe a extensão do formato (`logs/estimativa.csv` ou `logs/estimativa.json`).

## Testes

```bash
mvn test
```
