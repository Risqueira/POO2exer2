# POO2exer2

# atividade 6

# atividade 7
7. (Agregação – Playlist e Músicas)
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
