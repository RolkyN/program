/*  statvals calcule quelques valeurs statistiques.  */

#include <stdio.h>                                   /*  pour scanf, printf  */
#include <conio.h>                                          /*  pour getche  */

main()
{
   long val;                                              /*  valeur saisie  */
   long max;                                                    /*  maximum  */
   long maxeven;                                 /*  plus grand nombre pair  */
   int even_ok = 0;            /*  flag : y a-t-il au fait un nombre pair ?  */
   long min;                                                    /*  minimum  */
   long minodd;                                /*  plus petit nombre impair  */
   int odd_ok = 0;           /*  flag : y a-t-il au fait un nombre impair ?  */
   long s = 0;                                        /*  somme des nombres  */
   int n = 0;                                  /*  nombre de nombres saisis  */

   do
      {
         do                              /*  interception de saisie erronée  */
            {
               if (!n)                          /*  1ère saisie (n égale 0)  */
                  {
                     printf("Maximum, Minimum, Somme et Moyenne de"
                            " nombres entiers positifs.\n");
                     printf("Entrez des valeurs positives. Fin par -1.\n\n");
                  }
               printf("Nombre no %d : ", n+1);
               scanf("%ld", &val);
             } while (val < -1);             /*  on n'admet que des nombres */
                                                /*  positifs ou -1  */

   /*  calcul du maximum  */

         if (!n)               /*  1ère valeur  saisie (avec n égal à 0)  */
            max = val;              /*  pour initialiser max, on utilise  */
         else
            if (max < val)              /*  la plus grande valeur saisie  */
               max = val;                      /*  ranger dans max  */

  /*  calcul du minimum  */

         if (!n)                                 /*  1ère valeur  saisie  */
            min = val;              /*  pour initialiser min, on utilise  */
         else
             if (min > val && val >= 0)         /*  la plus petite valeur
                                                       saisie (mais pas -1)  */
         min = val;                           /*  ranger dans min  */

/*  calcul du plus grand nombre pair  */

         if (! even_ok)                 /*  si pas de nombre pair encore  */
            {
               if (val % 2 == 0)                      /*  si nombre pair  */
                  {
                    maxeven = val;     /*  initialiser maxeven avec lui  */
                    even_ok = 1;               /*  il y a un nombre pair  */
                  }
            }
         else                        /*  s'il y a déjà un nombre pair  */
           if (maxeven < val && (val % 2 == 0))
               maxeven = val;   /*  ranger le plus grand dans maxeven  */

/*  calcul du plus petit nombre impair  */

         if (! odd_ok)               /*  si aucun nombre impair encore  */
            {
              if (val % 2 && val >= 0)             /*  avec le premier
                                                             nombre impair  */
                 {
                   minodd = val;              /*  initialiser minodd  */
                   odd_ok = 1;           /*  il y a un nombre impair  */
                 }
            }
         else                       /*  s'il y a déjà un nombre impair  */
            if (val >= 0 && minodd > val && (val % 2))
               minodd = val;                         /*  ranger le plus */
                                         /* petit (mais pas -1) dans minodd  */

/*  former la somme pour la moyenne et compter les valeurs saisies  */
         if (val >= 0)       /*  ne pas traiter le caractère de fin -1  */
            {
               s += val;                               /*  additionner  */
               n++;                    /*  compter les valeurs saisies  */

            }
        } while (val != -1);              /*  fin du do while supérieur  */

      /*  afficher des valeurs  */

   printf("Nombre de caractères saisis : %d\n", n);

   if (n > 0)                           /*  si on a saisi des valeurs  */
      {
         printf("Maximum : %ld\n", max);
         if(even_ok)              /*  y avait-il des valeurs paires ?  */
             printf("Plus grand nombre pair : %ld\n", maxeven);
         else
             printf("Il n'y a pas eu de nombre pair.\n");
         printf("Minimum : %ld\n", min);
         if(odd_ok)             /*  y avait-il des valeurs impaires ?  */
             printf("Plus petit nombre impair : %ld\n", minodd);
         else
             printf("Il n'y a pas eu de nombre impair.\n");
         printf("Somme des valeurs saisies : %ld\n", s);
         printf("Moyenne : %f\n", (double) s/n);         /*  conversion  */
      }

   else
         printf("Aucune valeur n'a été saisie.\n");
}                                                  /*  fin du main  */

