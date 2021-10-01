  # Classes e Structs - Intro
 
 Classes e Structs são estruturas flexíveis que constituem o código do nosso programa, você pode definir propriedades e métodos que adicionam funcionalidades as suas classes e estruturas.
 
 No **Swift** não há necessidade de criar arquivos de interface e implementação separados (como em C++), classes e structs são definidas em um único arquivo (semelhante a Java).
 
 ### O que classes e estrutura possuem em comum? 
 
 * Definem propriedades
 * Definem métodos
 * Definem construtores
 * Podem ser extendidos para expandir funcionalidades
 * Podem assinar protocolos (protocolos exigem a existência de métodos)
 
 ### Qual o Diferencial de Classes em relação às estruturas?
 * Herança
 * Deinitializers permitem que instancias liberem recursos
 * Type Casting permite que você avalie e interprete o tipo de uma instância de classe em tempo de execução
 * Mais de uma referência para a instância de uma classe
 
 ** - IMPORTANTE** Structs são **Value Types** e são passados por cópia, enquanto classes são **Reference Types** e são passado por referência, o que significa que structs não usam o contador de referência. Veja o Exemplo:
 
```swift runnable

struct Resolution {
    var width = 0
    var height = 0
}

class VideoMode {
    var resolution = Resolution()
    var frameRate = 0.0
    var name: String?
}

```