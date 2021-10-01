 # Classes e Structs 01 - Intro
 
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
 
 **- IMPORTANTE** Structs são **Value Types** e são passados por cópia, enquanto classes são **Reference Types** e são passado por referência, o que significa que structs não usam o contador de referência. Veja o Exemplo abaixo. 

==> Você pode criar uma estrutura (struct) PontoR2 com atributos x e y inteiros? 

==> Você pode criar uma classe (class) quadrado com um ponto superior a esquerada (topLeft) do tipo PontoR2 e mais um atributo para descreve o lado do quadrado? 

 
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


# Refêrencia vs Valor
Em **Swift** Classes e Closures são Reference Types (tipos que trabalham com referência), todo o resto é Value Type (tpos que trabalham como valores), inclusive as struts são Value Type. Structs possuem inicializadores autogerados com todas as propriedades ou seja um construtor que recebe todos os atributos. 



### Veja um exemplo de como funciona um Value Type. 

==> Aqui temos uma prova que struts são Value Types. Você pode criar uma prova para arrays? 

```swift runnable

struct PontoR2 {
  var x : Int = 0
  var y : Int = 0
}

print("Inicialização de p1 e p2")
var p1 = PontoR2(x:10, y:10) // Inicializador autogerado para iniciar x e y
print("p1.x=\(p1.x)")

var p2 = PontoR2(x:20, y:20)
print("p2.x=\(p2.x)")

p1 = p2 //aqui é feita um cópia de valores p1 para p2
print("Depois da Cópia")
print("p1.x=\(p1.x)")
print("p2.x=\(p2.x)")

p2.x=30 //Veja que isso não interfere em p1
print("Depois da atribuição a p2")
print("p1.x=\(p1.x)")
print("p2.x=\(p2.x)")

```
**- IMPORTANTE** Assim fica claro o que é um Value Type. Ou seja quando ocorre atribuições em um elemento da estrutura (p1=p2) nada acontece com o elemento que recebeu a cópia (nesse caso alterações em p2 não interferem em p1).



### Veja um exemplo de como funciona um Reference Type.  
==> Você pode fazer um exemplo usando sua classe quadrado? 


```swift runnable

class Flor {
    var cor : String = "brnaca"
    
    init (cor : String) {
        self.cor = cor
    }
    
    func show () {
        print (self.cor)
    }
    
}

print ("Inicialização")
var lirio = Flor (cor: "banca")
var azaleia = Flor (cor: "rosa")
lirio.show()
azaleia.show()

print ("Lírio agora aponta para azaleia (ref para azaleia)")
lirio = azaleia
lirio.show()
azaleia.show()

print ("Modificação e azaleia afeta lírio")
azaleia.cor = "violeta"
lirio.show()
azaleia.show()

```

**- IMPORTANTE** Assim fica claro o que é um Reference Type. Ou seja quando ocorre atribuições em um objeto de uma classe (lirio = azaleia) esse objeto (lirio) recebe uma referência para o obejto (azaleia) e não uma cópia. Assim, alterações em azaleia irão refletir em lírio.


### Veja mais um exemplo de como funciona um Value e Reference Types.  
==> Você pode fazer modificações no exemplo de modo a incluir comentários do que está acontecendo? 

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

let hd = Resolution(width: 1920, height: 1080)
var cinema = hd
cinema.width = 2048
print(hd.width)

let videoMode = VideoMode()
let anotherMode = videoMode
anotherMode.frameRate = 24.0
print(videoMode.frameRate)
```

###Quando usar structs:
 * Quando queremos encapsular dados relativamente simples
 * Quando Propriedades do modelo também são **Value Types**
 * Quando o modelo não precisa herdar nenhuma propriedade ou comportamentos de modelos existentes ( Pode ser alcançado através de protocolos também )
 * Quando os dados encapsulados devem ser copiados e não referenciados.

==> Veja o exemplo e crie o seu próprio. Faça um comentário do porquê justificando a escolha da struct e não class para seu exemplo. 

```swift runnable

struct PointR3 {
    var x: Double
    var y: Double
    var z: Double
}

```