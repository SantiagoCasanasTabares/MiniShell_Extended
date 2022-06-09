#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>
#include <assert.h>
#include "leercadena.h"
#include <sys/types.h>
#include <signal.h>

#define MAX 100

int main(int argc, char* argv[]) 
{
  char **comando;
  char command[256];
  pid_t pid_aux;
  int **vector_hijos;
  int background = 0;
  //char* kill ="kill -9 ";
  int pidtokill;
  
  while (1) {
    int i;
    printf(">");
    leer_de_teclado(MAX, command);
    if(strcmp(command, "salir") == 0) break;
    comando = de_cadena_a_vector(command);
    i = 0;
    while(comando[i] != NULL){
      i++;
    }
    
    if (strcmp(comando[i-1], "&")==0) {
        comando[i-1] = NULL;
        background = 1;
    }

    int rc = fork();
    assert(rc >= 0);
    if (rc == 0){
          if(strcmp(comando[0], "tareas") == 0){
            printf("%ls\n", vector_hijos[0]);
            }
          execvp(comando[0], comando);
      }else if (rc>0 && background ==1) {
          pid_aux = rc;
          &vector_hijos[pid_aux];
          background = 0;
          continue;
      }else{
         /*if(strcmp(comando[0], "tareas") == 0){
            printf("%ls\n", vector_hijos[0]);
         }else */if (strcmp(comando[0], "detener") == 0){
           printf("Introduzca % y luego el PID del proceso a detener: ");
            scanf("%d",&pid_aux);
            kill(pid_aux, 9);
           }       
          wait(NULL);
        }
    }  
  return 0;
 
}
