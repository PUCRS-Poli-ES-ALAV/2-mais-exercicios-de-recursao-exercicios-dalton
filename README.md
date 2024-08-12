# Exercícios de recursão adicional

Modele as recursões, e depois implemente cada um dos algorítmos modelados.
Faça uma classe contendo os métodos implementados. Coloque a modelagem como comentário antes de cada método.

Como trabalharemos: programando em pares no nosso encontro síncrono (Pair Programming) ou seja, uma máquina/código, dois desenvolvedores cooperando, alternando os papéis de piloto e co-piloto (a cada 10-15 minutos, por exemplo). Após o encontro, continuem desnvolvendo cooperativamente, utilizando o repositório no github para compartilhar o trabalho sendo desenvolvido.

Extra: terminados estes exercícios, modele e implemente (se ainda não concluiu) os exercícios de re-aquecimento.


Os exercícios:

1. Modele e implemente um método recursivo que calcule o fatorial de um número n passado como parâmetro.

1. Modele e implemente um método recursivo que calcule o somatório de um número n (passado como parâmetro) até 0.

1. Modele e implemente um método recursivo que calcule o n-ésimo número da sequência de fibonacci.

1. Modele e implemente um método recursivo que calcule o somatório dos números inteiros entre os números k e j, passados como parâmetro.

1. Modele e implemente um método recursivo que recebe um String em retorna true se este String for um palíndrome, false caso contrário.
    ``` 
         boolean isPal(String s) 
    ```
1. Modele e implemente um método recursivo que recebe um inteiro zero ou positivo e retorna um String com o número em binário.
    ``` 
         String convBase2(int n) 
    ``` 
1. Modele e implemente um método recursivo que calcule o somatório dos números contidos em um ArrayList de inteiros, passado como parâmetro.

1. Modele e implemente um método recursivo para encontrar o maior elemento de um ArrayList.
    ``` 
         int findBiggest(ArrayList<Integer> ar) 
    ``` 

1. Implemente um método recursivo para determinar se um string ocorre dentro de outro.
	  ``` 
         boolean findSubStr(String str, String match)
	  ``` 
1. Faça um método recursivo que determina o número de dígitos de um inteiro.
	  ``` 
         int nroDigit(int n)
	  ``` 
1. Implemente um métodos que recebe um String e retorna um ArrayList com todas as permutações deste String.
	  ``` 
         ArrayList<String> permutations(String s)
	  ``` 

import java.util.ArrayList;

public class Aula { 
    public static void main(String[] args) { 
        String binario = convBase2(10);
        System.out.println(binario); 
    }
}

// Calcule o fatorial de um número n passado como parâmetro
public static int fatorial(int n) { 
    // Assinatura
    // Método
    if (n == 1)
        return 1;
    if (n <= 0)
        throw new IllegalArgumentException("Número inválido");
    return n * fatorial(n - 1);
}

// Calcule o somatório de um número n até 0.
public static int somatorio(int n) {
    if (n == 0)
        return n;
    return n + somatorio(n - 1);
}

// Calcule o n-ésimo número da sequência de fibonacci
public static int fibonacci(int n) {
    if (n == 0)
        return 0;
    if (n == 1)
        return 1;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Calcule o somatório dos número inteiros entre os números k e j, passados como
// parâmetro.
public static int somatorioKJ(int k, int j) {
    if (k == j)
        return j;
    if (k < j)
        return k + somatorioKJ(k + 1, j);
    return somatorioKJ(j, k);
}

// Recebe um string e retorna true se este string for um palíndrome, false caso
// contrário
public static boolean isPal(String s) {
    if (s.length() == 0)
        return false;
    if (s.length() <= 1)
        return true;

    char init = s.charAt(0);
    char last = s.charAt(s.length() - 1);
    if (last != init)
        return false;

    return isPal(s.substring(1, s.length() - 1));

}


public static String convBase2(int n){
    if(n < 0) return null;
    if(n == 0) return "0";
    if(n == 1) return "1";


    return convBase2(n/2) + (n%2);

}

ou:

    public static String convBase2(int n){
        if(n == 0)
            return "0";
        else if (n == 1)
            return "1";
        else
            return convBase2(n/2).concat(convBase2(n%2));
    }


//Modele e implemente um método recursivo 
//que calcule o somatório dos números contidos em um 
//ArrayList de inteiros, passado como parâmetro.
public static int somaArray(ArrayList n){
if(n.isEmpty()) return 0;

int last = n.get(n.size() - 1);

n.remove(n.size() - 1);

return last + somaArray(n);
}

ou:

    public static int somaArray(int[] array){
        if (array.length == 0)
            return 0;
        return somaArrayAux(array, 0, 0);
    }

    private static int somaArrayAux(int[] array, int pos, int sum){
        if(pos<array.length){
            sum += array[pos];
            pos++;
            return somaArrayAux(array, pos, sum);
        }

        return sum;
    }

public static int findBiggest(ArrayList<Integer> ar){
    if(ar.isEmpty()) return 0;
    if(ar.size()==1) return ar.get(0);

    if(ar.get(ar.size()) <= ar.get(ar.size()-1)){
    ar.remove(ar.size());
    }else ar.remove(ar.size()-1);

 return findBiggest(ar);

}

public static boolean findSubStr(String str, String match){
    

}


