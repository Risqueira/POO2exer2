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
