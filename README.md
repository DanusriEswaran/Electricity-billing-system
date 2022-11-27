# Electricity-billing-system
/*The objective of this electricity billing project is to reduce the manual billing system. It manages all the information about the payments.*/

#include<stdlib.h>
#include<stdio.h>
#include<conio.h>
#include<string.h>
struct custom //structures
{
	int bill;
	int eb_id;
	char name[20];
	int unit;
	int b_id;
	float price;
};

int bill_id() 
  {
  	struct bill
    {
	int num;
    };
   int y;
   struct bill n;
   FILE *fp; //used pointer file to store the bill no automatically
   fp=fopen("bi.bin","rb");
   if(fp==NULL) 
      n.num=0;
      else
      {
      	fread(&n,sizeof(n),1,fp);
      	n.num++;
	  }
	  fclose(fp);
      fp=fopen("bi.bin","wb");
      fwrite(&n,sizeof(n),1,fp);
   fclose(fp);
   return n.num;
  }
  void pay_ment() 
{
	struct custom c;
	int unit;
	printf("\n                     BILL PAYMENT \n                --------------------");
    printf("\n 1.upto 100 units--------------Rs.10/unit \n 2.101-250 units---------------Rs.11/unit");
    printf("\n 3.250-400 units--------------Rs.12/unit \n 4.400+units------------------Rs.13/unit");
	printf("\n enter you eb id: ");
	scanf("%d",&c.eb_id);
	printf("\n enter your name:  ");
	scanf("%s",&c.name);
	printf("\n enter the units consumed:   ");
	scanf("%d",&c.unit);
	unit=c.unit;
	if(unit<=100)
	 c.price=unit*10;
	else if(unit>100&&unit<=250)
	 c.price=unit*11;
	else if(unit>250&&unit<=400)
	 c.price=unit*12;
	else 
	 c.price=unit*13;
	printf("\n total amount:    %.2f",c.price);
	printf("\n\n******************************");
    printf("\n\tELECTRICITY BILL");
    printf("\n*******************************");
    c.b_id=bill_id();
	printf("\n     Your Bill no   : %d",c.b_id);
    printf("\n     Eb id          : %d",c.eb_id);
    printf("\n     Name           : %s",c.name);
    printf("\n     Unit consumed  : %d",c.unit);
    printf("\n     Total amount   : %.2f",c.price);
    printf("\n----------------------------------------------");
   }
int main()
{
	printf("                                       ELECTRICITY BILL CALCULATOR");
	printf("\n                                 *************************************\n\n");
    char username[20];
	char password[20];
	printf("\nplease enter the username:");
	scanf("%s",username);
	printf("please enter the password: ");
	scanf("%s",password);
	if(strcmp(username,"132857")==0)
	{
		if(strcmp(password,"****")==0)
		{
			printf("\nlogin successfull!");
		}
		else
		{
			printf("\n invalid password");
			exit(0);
		}
	}
	else
	{
		printf("\n username is invalid");
		exit(0);
    }
      printf("\n                                           WELCOME");
	  printf("\n                                      ******************");
    int choice=1;
    while(choice!=2)
    {
      printf("\n                                         MAIN MENU  ");	
      printf("\n                                        1. Payment  ");
      printf("\n                                        2.. EXIT ");
      printf("\n Enter your choice :   ");
      scanf("%d",&choice);
       switch(choice)
        {
          case 1: pay_ment();
                  break;    
          case 2: break;	  	  
          default:
		  {
          	printf("\n\n  Invalid Choice...!");
          	printf("\n\n Press any key to continue..");
          	getch();
	     } 	          	  	
        }
     } 	
 }
