#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <ctype.h>



int j, i, n, k, x, y, posf, posc, c, auxf, auxc, puedo, contchoq, content, palab, cond;

int main()
{
    
	printf("\nESTABLEZCA LAS CONDICIONES DE LA SOPA DE LETRAS");
	system("color 3");

	printf("\nESTABLEZCA LIMITE DE LA MATRIZ NxN con limite 10<= N <=35: ");
    scanf("%d", &n);
    fflush(stdin);
    while(n<10 || n>35)
    {	
		printf("\nERROR, LIMITE ERRONEO INGRESE VALOR ENTRE 10 Y 35");
        printf("\nESTABLEZCA LIMITE DE LA MATRIZ NxN: \n");
        scanf("%d", &n);
        fflush(stdin);
	}

    int matriz[n][n];

	printf("\nINGRESE CANTIDAD DE PALABRAS ENTRE %d<=K<=%d\n", n/2,n*2);
	scanf("%d", &k);
	fflush(stdin);
    while (k<(n/2) || k>(n*2) && k != 75)
    {
		printf("\nERROR, LIMITE ERRONEO INGRESE VALOR ENTRE %d<=K<=%d", n/2,n*2);
		printf("\nINGRESE CANTIDAD DE PALABRAS A ESCONDER: ");
		scanf("%d", &k);
		fflush(stdin);
	}

    // K representa la cantidad de palabras dentro de la matriz 
    // N representa el tamanno maximo de la palabra

    char palabras[k][n];
    int posiciones[k][4];
	int orientacion[k];
	//	INGRESO DE PALABRAS A LA MATRIZ CON PALABRAS
	printf("\nIngrese palabra %d, de minimo 2 caracteres y maximo %d ", i+1,n);
	printf("\n* solo estan permitidos los caracteres del alfabeto * ");
    for ( i = 0; i < k; i++)
    {
        printf("\nIngrese palabra %d: ", i+1);
        gets(palabras[i]);
        fflush(stdin);

        if(strlen(palabras[i])<2 || strlen(palabras[i])>n)
        {
            printf("\n*ERROR EN EL LIMTE DE CARACTERES MINIMO 2 Y MAXIMO %d CARACTERES* ",n);
            i=i-1;
        }else
		{
			for (j = 0; j < n && palabras[i][j]!='\0'; j++)
			{
				if (palabras[i][j]<65 && palabras[i][j]>=32)
				{
					printf("\nSu palabra %d tiene caracterres no permitidos \n en la posicion %d por favor reingresela \n",i+1,j+1);
					j=n;
					i=i-1;
				}else if (palabras[i][j]>90 && palabras[i][j]<97)
				{
					printf("\nLa palabra %d tiene caracterres raros \n",i+1);
					j=n;
					i=i-1;
				}else if(palabras[i][j]>122 && palabras[i][j]<255)
				{
					printf("\nLa palabra %d tiene caracterres raros \n",i+1);
					j=n;
					i=i-1;
				}else if(palabras[k][j]<123 && palabras[k][j]>96)
				{
					palabras[k][j]=palabras[k][j]-32;
				}   
			}
		}
    }
    

    //CAMBIO DE MINUSCULAS A MAYUSCULAS
    for ( i=0; i<k; i++)
    {
		for ( j=0; j<n; j++)
		{
	        // cambiamos minisculas por mayusulas
			if(palabras[i][j]<123 && palabras[i][j]>96)
            {
                palabras[i][j]=palabras[i][j]-32;
            }
			//printf("[%c]", palabras[i][j]);
		}	
		//printf("\n");
	}
	//printf("\n");

    // llenamos de espacios vacios la sopa
	for ( i = 0; i < n; i++)
	{
		for ( j = 0; j < n; j++)
		{
            // llenas de caracteres
			//matriz[i][j]=rand () %  (90-65+1) + 65;   // Este estÃ¡ entre M y N
            matriz[i][j]=32;
		}
	}
	int op;
	// *opcion 1 filas 
	// * opcion 2 columnas
	srand(time(NULL));
	contchoq = 0;
	/// contchoq es para contar cuantas veces se intento poner en un lugar que estaba ocupado  , la cual tiene un limite de 1000 
	// si contchoq llega a 1000 tomamos que no hay espacio para meter la palabra y la ignoramos
	content = 0;
	//content es un contador de cuantas entraron
	for(i=0; i<k; i++)
	{
		op = rand()%2;
		//OPCION 1 FILAS
		//op=0;
		if(op == 1)
		{	
			//op=0;
			op = rand()%2;
			
			if (op==1)
			{
				// ! normal vertical
				posf = rand()%(n-strlen(palabras[i]));
				posc = rand()%(n);
				puedo = 0;
				j=0;
				for (x = posf; x < strlen(palabras[i])+posf && palabras[i][j]!= '\0' ; x++)
				{
					if( matriz[x][posc] != 32)
					{
						puedo = 1;
						break;
						//! BREAK PARASALIR DEL FOR CUANDO ENCUENTRE UNA LETRA DENTRO DE LA MATRIZ RANDOM
					}
					
				}
				if (puedo == 0)
				{
					c=0;
					j=0;
					posiciones[i][c]=posf;
					c=c+1;
					posiciones[i][c]=posc;
					for (x = posf; x < strlen(palabras[i])+posf && palabras[i][j]!= '\0'; x++)
					{
						matriz[x][posc] = palabras[i][j];
						j = j + 1;
					}	  
					c=c+1;
					posiciones[i][c]= x-1;
					c=c+1;
					posiciones[i][c]=posc;
					content = content + 1;
					orientacion[i]=1;
				}else
				{
					i = i - 1;
					contchoq = contchoq + 1;
					//printf("\nSe chocan en vertical normal yla palabra numero %d y se an chocado %d \n",i+1,contchoq);
				}
				if (contchoq == 1000)
				{
					i = k;
				}

			}else
			{
                //! al reves vertical
				posf = rand()%(n-strlen(palabras[i])+1 ) + strlen(palabras[i]);
				posc = rand()%(n);
				puedo = 0;
				j=0;
				for (x = posf-1;  palabras[i][j]!= '\0'  ; x = x - 1)
				{
					if( matriz[x][posc] != 32)
					{
						puedo = 1;
						break;
						//!BREAK PARASALIR DEL FOR CUANDO ENCUENTRE UNA LETRA DENTRO DE LA MATRIZ RANDOM
					}
					j=j+1;
				}
				if (puedo == 0)
				{
					c = 0;
					j = 0;
					posiciones[i][c]=posf-1;
					c=c+1;
					posiciones[i][c]=posc;
					for (x = posf-1;  palabras[i][j]!= '\0'; x=x-1)
					{
						matriz[x][posc] = palabras[i][j];
						j = j +1;
					}	
					c=c+1;
					posiciones[i][c]= x+1;
					c=c+1;
					posiciones[i][c]=posc;
					content = content + 1;
					orientacion[i]=2;
				}else
				{
					i = i - 1;
					//printf("\nSe chocan la palabra numero %d y se an chocado %d \n",i+1,contchoq);
					contchoq = contchoq + 1;
				}
				if (contchoq == 1000) 
				{
					i = k;
				}
			}
		}else//OPCION 2
		{
			// ! aqui la columnas 
			op = rand()%2;
			//op = 1;
			if (op==0)//normal
			{
				
				posc = rand()%(n-strlen(palabras[i]));
				posf= rand()%(n);	
				puedo = 0;
				j=0;
				for (x = posc; x < strlen(palabras[i])+posc && palabras[i][j]!= '\0'; x++)
				{
					if( matriz[posf][x] != 32)
					{
						puedo = 1;
						break;
						// ! BREAK PARASALIR DEL FOR CUANDO ENCUENTRE UNA LETRA DENTRO DE LA MATRIZ RANDOM
					}
					j=j+1;
				}
				if (puedo==0)
				{
					c = 0;
					j=0;
					posiciones[i][c]=posf;
					c=c+1;
					posiciones[i][c]=posc;
					for (x = posc; x < strlen(palabras[i])+posc && palabras[i][j]!= '\0'; x++)
					{
						matriz[posf][x] = palabras[i][j];
						j = j + 1;
					}	 
					c=c+1;
					posiciones[i][c]= posf;
					c=c+1;
					posiciones[i][c]=x-1; 
					content = content + 1; 
					orientacion[i]=3;
				}else
				{
					i = i - 1;
					contchoq = contchoq + 1;
					//printf("\nSe chocan la palabra en horizontal normal numero %d y se an chocado %d \n",i+1,contchoq);
				}
				if (contchoq == 1000) 
				{
					i = k;
				}
				
			}else 
			{
				// ! aqui horizonte reves 
				posf = rand()%(n);
				posc = rand()%(n-strlen(palabras[i]) + 1) + strlen(palabras[i]);
				puedo = 0;
				j=0;
				for (x = posc-1;  palabras[i][j]!= '\0'; x=x-1)
				{
					if( matriz[posf][x] != 32)
					{
						puedo = 1;
						break;
						// ! BREAK PARASALIR DEL FOR CUANDO ENCUENTRE UNA LETRA DENTRO DE LA MATRIZ RANDOM
					}
					j=j+1;
				}
				if (puedo==0)
				{
					c = 0;
					j = 0;
					auxc=posc-1;
					posiciones[i][c]=posf;
					c=c+1;
					posiciones[i][c]=auxc;

					for (x = posc-1;  palabras[i][j]!= '\0'; x=x-1)
					{
						matriz[posf][x] = palabras[i][j];
						j = j +1;
					}
					c=c+1;
					posiciones[i][c]=posf;
					c=c+1;
					posiciones[i][c]=x+1;
					content = content + 1;
					orientacion[i]=4;
				}else
				{
					i = i - 1;
					contchoq = contchoq + 1;
					//printf("\nSe chocan la palabra en horizontal reves numero %d y se an chocado %d \n",i+1,contchoq);
				}
				if (contchoq == 1000) 
				{
					i = k;
				}
			}		
		}		
	}
/*
	for ( i = 0; i < n; i++)
	{
		for ( j = 0; j < n; j++)
		{
			printf("[%c]",matriz[i][j]);
		}
		printf("\n");
	}
*/

/*
    // AQUI MOSTRAMOS EL INICIO Y FIN DE LAS PALABRAS
    for ( i = 0; i < k; i++)
	{
		for ( j = 0; j < 4; j++)
		{		
            if (j<2)
            {
				printf("[palabra %d tiene posicion inicial %d]\n",i+1,posiciones[i][j]+1);
            }else{
                printf("[palabra %d tiene posicion finales %d]\n",i+1,posiciones[i][j]+1);
            }   
		}
		printf("\n");
	}
*/

	for ( i = 0; i < n; i++)
	{
		for ( j = 0; j < n; j++)
		{
            // * Llenas de caracteres
			if (matriz[i][j]==32)
			{
				matriz[i][j]=rand () %  (90-65+1) + 65;   // Este estÃ¡ entre M y N
			}
		}
	} 

	system("cls");
	printf("\nCOMIENZA EL JUEGO\n");
	for ( i = 0; i < n; i++)
	{
		for ( j = 0; j < n; j++)
		{
            printf("[%c]",matriz[i][j]);
            
			}
			printf("\n");
			
		}
	printf("\n entraron %d palabras\n",content);

	clock_t inicio, fin;
	double tiempo;
	inicio=clock();

	char palab[n];
	int contw = 0;
	int contl = 3;

	do
	{
		int mal = 0;
		printf("\nIngrese palabra encontrada: ");
		gets(palab);
		fflush(stdin);

		for ( i = 0; palab[i] != '\0'; i++)
		{
			palab[i]=toupper(palab[i]);
		}
		




		for ( i = 0; i < content; i++)
		{
			int cond = strcmp(palab, palabras[i]);
			if (cond == 0)
			{
				contw = contw + 1;
				printf("\n FELICIDADES ENCONTRASTE LA PALABRA: %s\n", palabras[i]);
				printf("\n EMPIEZA: (%d,%d) || TERMINA:(%d,%d)", posiciones[i][0]+1,posiciones[i][1]+1, posiciones[i][2]+1,posiciones[i][3]+1);
				switch (orientacion[i])
				{
				case 1:
					printf("\n ESTA EN VERTICAL DE ARRIBA HACIA ABAJO ");
					break;
				
				case 2: 
					printf("\n ESTA EN VERTICAL DE ABAJO HACIA ARRIBA ");
					break;
				case 3:
					printf("\n ESTA EN HORIZONTAL DE IZQUIERDA A DERECHA ");
					break;
				case 4:
					printf("\n ESTA EN HORIZONTAL DE DERECHA A IZQUIERDA ");
					break;
				default:
					printf("no deberias ver esto");
					break;
				}
				printf("\n VIDAS RESTANTES: %d", contl);
				printf("\n PALABRAS RESTANTES: %d", content-contw);
				
				
				for ( j = 0; palabras[i][j] != '\0'; j++) //!CODIGO PARA BORRAR PALABRA YA ENCONTRADA
				{
					palabras[i][j] = 32;
				}
				break;
				
			}else
			{
				mal = mal + 1;
				if (mal == k)
				{
					contl = contl - 1;
					printf("\n PALABRA INCORRECTA\n");
					printf("\n VIDAS RESTANTES: %d", contl);
					printf("\n PALABRAS RESTANTES: %d", content-contw);
				}
			}
		}

		if (contl == 0)
		{
			printf("\nFIN DEL JUEGO\n");
			break;
		}else if(contw == k)
		{
			printf("\nFELICIDADES GANASTE\n");
			break;
		}
		
	} while (1);

	fin=clock();
	tiempo = ((double) (fin-inicio))/CLOCKS_PER_SEC;//CON ESTO SABEMOS EL TIEMPO
	printf("\nTiempo que tardado: %.2f \ns",tiempo);

	system("pause");
	return 0;
}
