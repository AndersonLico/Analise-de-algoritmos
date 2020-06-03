import java.util.Scanner; //Para criar campo de digitação
import java.io.IOException;	

public class quicksort {

	public static void main(String[] args) throws IOException {

		Scanner entrada = new Scanner(System.in);
 
	int quantidade;
	System.out.println("Digite a quantidade");
	quantidade =entrada.nextInt();
	int [] vetor = new int[quantidade];
	
	for (int i = 0; i < vetor.length; i++) {
		vetor[i] = (int) (Math.random()*quantidade);
	}
	
	long tempoinicial = System.currentTimeMillis();
	
	quickSort(vetor,0,vetor.length-1);
	
	long tempoFinal = System.currentTimeMillis();
	// exibir tempos
	System.out.println("Executando em : " +(tempoFinal - tempoinicial)+ "ms");
	
	// exibir Vetor ordenado
	mostrarVetor(vetor);
	System.out.println("Executando em : " +(tempoFinal - tempoinicial)+ "ms");
	
	}	
	private static void quickSort(int[] vetor, int inicio, int fim) {
		if (inicio < fim) {
			int posicaoPivo = separar(vetor, inicio, fim);
			quickSort(vetor, inicio, posicaoPivo - 1);
			quickSort(vetor, posicaoPivo + 1, fim);
		}
	}
    private static int separar(int[] vetor, int inicio, int fim) {
    	int pivo = vetor[inicio];
    	int i = inicio + 1, f = fim;
    	while (i <=f) {
    		if(vetor[i] <= pivo)
    			   i++;
    		else if (pivo <vetor[f])
    			   f--;
    		else {
    			  int troca = vetor[i];
    			  vetor [i] = vetor[f];
    			  vetor [f] = troca;	
    			  i++;
    			  f--;
    	    }
    
    	}
    	vetor[inicio] = vetor[f];
    	vetor[f] = pivo;
    	return f;
    	
    }	
    private static void mostrarVetor(int[] vetor) {
    	for(int j=0; j<vetor.length; j++) {
    		System.out.println(vetor[j]+", ");
    	}
    }
}
