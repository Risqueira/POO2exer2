# POO2exer2

# atividade 6

# 7. (Agregação – Playlist e Músicas)
Uma playlist do Spotify contém várias músicas.
 As músicas podem existir fora da playlist.
 Modele Playlist e Musica.
 Crie um método tocarTodas() que percorre e toca (imprime na tela) cada
música da playlist.
```java
package spotfypoo;

public class Musica {
    public String nome;
    public Musica(String nome){
        this.nome=nome;
    }
}
```
```java
package spotfypoo;

import java.util.ArrayList;

public class Playist {

    public String nome;
    public ArrayList<Musica> musicas;

    public Playist() {
        musicas = new ArrayList<>();
    }

    public Playist(String nome) {
        this.nome = nome;
       
    }

    public void incluirMusica(Musica m) {
        musicas.add(m);
        System.out.println("Salvo!!");
    }

    public String tocarTodas() {
        
       String ms = "Musicas\n";
        if(!musicas.isEmpty()){
           for(int i = 0; i<musicas.size();i++){
               ms+= musicas.get(i).nome+"\n";
           }
           
       }else{
            ms = "Lista vazia!!";
        }
        return ms;
    }
}
```
```java

package spotfypoo;

/**
 * @author Henrique 08/09/2025
 */
public class Spotfypoo {

    public static void main(String[] args) {
        
        Musica msc1= new Musica("Feel good inc");
        Musica msc2= new Musica("Trem das onzes");
        Playist muscs = new Playist();
        muscs.nome = "Loves";
        muscs.incluirMusica(msc1);
        muscs.incluirMusica(msc2);
        System.out.println("PlayList:"+muscs.nome+"\n");
        System.out.println(muscs.tocarTodas());
        
       
    }
    
}
```
# 8. (Associação – Cliente e Conta Bancária)
Um cliente possui uma conta bancária, mas a conta continua existindo mesmo sem o
cliente (ex.: conta empresarial).
 Modele Cliente e ContaBancaria.
 Implemente o método depositar() na conta e simule um cliente usando-o.

```java
package clientecontabancaria;

/**
 *
 * @author Henrique 09/09/2025
 */
public class ClienteContaBancaria {

    public static void main(String[] args) {
        Cliente cliente1 = new Cliente("Joao Silva", "123.123.123.00");

        ContaBancaria conta1 = new ContaBancaria(1001, 500, cliente1);

        conta1.depositar(500.0);
        conta1.exibirDados();

    }

}
```
```java
package clientecontabancaria;

public class Cliente {

    private String nome;
    private String cpf;

    public Cliente() {
    }

    public Cliente(String nome, String cpf) {
        this.nome = nome;
        this.cpf = cpf;
    }

    public String getNome() {
        return nome;
    }

    public String getCpf() {
        return cpf;
    }
}

```
```java
package clientecontabancaria;

public class ContaBancaria {

    private int numero;
    private double saldo;
    private Cliente cliente; //associaçao

    public ContaBancaria() {
    }

    public ContaBancaria(int numero, double saldo, Cliente cliente) {
        this.numero = numero;
        this.saldo = 0.0;
        this.cliente = cliente;
    }

    public void depositar(double valor) {
        if (valor > 0) {
            saldo = saldo + valor;
            System.out.println("Deposito de R$" + valor + " realizado com sucesso.");
        } else {
            System.out.println("Valor invalido para deposito.");
        }
    }

    public void exibirDados() {
        System.out.println("Conta:" + numero);
        System.out.println("Saldo R$" + saldo);
        if (cliente != null) {
            System.out.println("Titular: " + cliente.getNome() + " | CPF: " + cliente.getCpf());
        } else {
            System.out.println("Conta sem titular");
        }
    }
}
```


# 9. (Classe Abstrata – Transporte)
Crie a classe abstrata Transporte com atributo capacidade e método abstrato
calcularTempoViagem(distancia).

 Implemente Onibus e Bicicleta.
 Simule quanto tempo cada transporte levaria para percorrer 100 km.

```java
package poo9transporte;

/**
 *
 * @author Henrique 09/09/2025
 */
public class POO9Transporte {

    public static void main(String[] args) {
        double distancia=100.0; //Km
        
        Onibus onibus= new Onibus(50, 80.0); //Onibus com 80Km/h
        Bicicleta bike= new Bicicleta(1, 20.0); //Bicicleta com 20km/h
        
        System.out.println("Distancia: "+distancia + " km");
        
        System.out.println("Onibus ("+onibus.getCapacidade()+ " Passageiros)"
        + onibus.calcularTempoViagem(distancia)+ "horas");
        
        System.out.println("Bicicleta (" + bike.getCapacidade() + " passageiro): "
                + bike.calcularTempoViagem(distancia) + " horas");
    
    }

}

```
```java
package poo9transporte;

public abstract class Transporte {

    protected int capacidade;

    public Transporte() {
    }

    public Transporte(int capacidade) {
        this.capacidade = capacidade;
    }

    // método abstrato: cada transporte calcula o tempo de um jeito
    public abstract double calcularTempoViagem(double distancia);

    public int getCapacidade() {
        return capacidade;

    }
}

```
```java
package poo9transporte;

public class Onibus extends Transporte {

    private double velocidadeMedia; //Km/h

    public Onibus() {
    }

    public Onibus(int capacidade, double velocidadeMedia) {
        super(capacidade);
        this.velocidadeMedia = velocidadeMedia;
    }

    @Override
    public double calcularTempoViagem(double distancia) {
        return distancia / velocidadeMedia; //calculo de quanto tempo em horas
    }

}

```
```java
package poo9transporte;

public class Bicicleta extends Transporte {

    private double velocidadeMedia; //Km/h

    public Bicicleta() {
    }

    public Bicicleta(double velocidadeMedia) {
        this.velocidadeMedia = velocidadeMedia;
    }

    public Bicicleta(int capacidade, double velocidadeMedia) {
        super(capacidade);
        this.velocidadeMedia = velocidadeMedia;
    }
    
     @Override
    public double calcularTempoViagem(double distancia) {
        return distancia / velocidadeMedia;
    }

}
```

# 10. (Método Concreto em Classe Abstrata – Animal)
Crie a classe abstrata Animal com:

 Método abstrato emitirSom().

 Método concreto dormir() que imprime &quot;Zzz...&quot;.

 Implemente Cachorro e Gato.

 Teste chamando ambos os métodos em cada animal.

```java
package poo10animal;

/**
 *
 * @author Henrique 09/09/2025
 */
public class POO10Animal {

    public static void main(String[] args) {
        Animal c = new Cachorro("dog");
        Animal g = new Gato("auau");
        c.emitirSom();
        g.emitirSom();
        c.dormir();
        g.dormir();
    }

}
```
```java
package poo10animal;

public abstract class Animal {

    protected String nome;

    public Animal() {
    }

    public Animal(String nome) {
        this.nome = nome;
    }

    public void dormir() { //metodo concreto diz como fazer
        System.out.println(nome + " Zzz...");
    }

    public abstract void emitirSom(); //metodo abstrato nao diz como fazer

}

```
```java
package poo10animal;

public class Cachorro extends Animal{

    public Cachorro() {
    }

    public Cachorro(String nome) {
        super(nome);
    }

    @Override
    public void emitirSom(){
        System.out.println(nome+ " AU AU");
    }
}
```
```java
package poo10animal;

public class Gato extends Animal {

    public Gato() {
    }

    public Gato(String nome) {
        super(nome);
    }
    @Override
    public void emitirSom(){
        System.out.println(nome+ " MIAU MIAU");
    }
}
```

# 11. (Interface – Pagamento)
Crie a interface Pagamento com o método processarPagamento(double valor).

 Implemente em Pix e Boleto.

 No programa principal, simule compras usando diferentes formas de pagamento.

```java
package poo11interface;

/**
 *
 * @author Henrique 10/09/2025
 */
public class POO11interface {

    public static void main(String[] args) {
        
        Pagamento pag1=new Pix("xiruzada123@gmail.com");
        Pagamento pag2= new Boleto("1234,5678,9123,4567");
        
        System.out.println("Pagamentos abaixo:");
        pag1.processarPagamento(250.0);
        pag2.processarPagamento(500.0);
    }

}
```
```java
package poo11interface;

public interface Pagamento {
    public void processarPagamento(double valor);
}
```
```java
package poo11interface;

public class Pix implements Pagamento {
    private String chavePix;

    public Pix(String chavePix) {
        this.chavePix = chavePix;
    }
    
    @Override
    public void processarPagamento(double valor){
        System.out.println("Pagamento R$"+valor +" feito com pix com a chave "+chavePix);
    }
}
```
```java
package poo11interface;

public class Boleto implements Pagamento {

    private String codigoBarras;

    public Boleto(String codigoBarras) {
        this.codigoBarras = codigoBarras;
    }

    @Override
    public void processarPagamento(double valor) {
        System.out.println("Boleto gerado no valor R$" + valor + " . Codigo de barras:" + codigoBarras);
    }
}
```

# 12. (Interface + múltiplas implementações – Drone)
Um drone pode voar e filmar.
 Crie interfaces Voavel e Filmavel.

 Implemente a classe Drone que realiza as duas ações.

 Demonstre o uso chamando ambos os métodos.

```java
package poo11drone;

/**
 *
 * @author Henrique 10/09/2025
 */
public class POO11Drone {

    public static void main(String[] args) {
        Drone drone= new Drone();
        
        drone.voarDrone();
        drone.filmarDrone();
    }
    
}
```
```java
package poo11drone;

public interface Voavel {
    public void voarDrone();
}
```
```java
package poo11drone;

public interface Filmavel {
    public void filmarDrone();
}
```
```java
package poo11drone;

public class Drone implements Voavel, Filmavel {

    @Override
    public void voarDrone() {
        System.out.println("O drone está voando ao infinito e alem");
    }

    @Override
    public void filmarDrone() {
        System.out.println("O drone está filmando em HD");
    }

}
```

# 13. (Composição + Agregação – Escola)
Uma escola é composta por várias salas de aula (se a escola fechar, as salas também
deixam de existir).
Cada sala de aula tem alunos (que podem existir fora da escola).

 Modele as classes Escola, SalaDeAula e Aluno.

 Crie um programa que cadastre alunos em diferentes salas e liste todos da
escola.

```java
package poo14instmusicais;

/**
 *
 * @author Henrique 10/09/2025
 */
public class POO14InstMusicais {

    public static void main(String[] args) {

        IntrumentoMusical v = new Violao();
        IntrumentoMusical b = new Bateria();
        IntrumentoMusical t = new Teclado();

        v.tocar();
        b.tocar();
        t.tocar();
    }

}
```
```java
package poo14instmusicais;

public abstract class IntrumentoMusical {

    public void tocar() {

    }

}
```
```java
package poo14instmusicais;

public class Violao extends IntrumentoMusical {

    @Override
    public void tocar() {
        System.out.println("Tocando violão");
    }
}
```
```java
package poo14instmusicais;

public class Bateria extends IntrumentoMusical {

    @Override
    public void tocar() {
        System.out.println("Tocando bateria");
    }
}
```
```java
package poo14instmusicais;

public class Teclado extends IntrumentoMusical {

    @Override
    public void tocar() {
        System.out.println("Tocando teclado");
    }
}
```
