
class Mochilanascostas{
	
public static int calcula (int capacidade, int []pesos, int []valores){
int n = pesos.length;
    int [][] k = new int[n+1][capacidade+1];
      for (int i = 0; i<=n; i++){
        for (int v = 0; v <=capacidade; v++){
          if ((i == 0)|| (v==0))
            k[i][v] = 0;
            else
            if(pesos[i-1]<=v)
                k[i][v] = Math.max(valores[i-1] + k[i-1][v-pesos[i-1]], k[i-1][v]);
            else
                k[i][v] = k [i-1][v];
}
        }
        for (int i = 0; i <= n; i++){
            for (int v = 0; v<=capacidade; v++)
                System.out.printf(" %d \n",k[i][v]);
            System.out.println();
        
}
return k[n][capacidade];
}
public static void main (String []args){
	
	long tempoinicial = System.currentTimeMillis(); //inicia a contagem do tempo
    
int[]valores = {60, 90, 50, 80, 130, 70, 90, 80, 120, 160};
int [] pesos = {10,20,30,15,25,35,12,22,32,40};
int capacidade = 100;
System.out.printf("Valor Maximo dos itens na mochila R$ = %d\n", calcula (capacidade, pesos, valores));

long tempofinal = System.currentTimeMillis(); //finaliza a contagem do tempo

System.out.println("Tempo de execução" + (tempoinicial-tempofinal) + "ms");
}

}
