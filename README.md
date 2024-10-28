#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
	
	//Initialization
    char first_name[50],last_name[50], f_name[50], dest[100], id[10], phone_number[10], email[50];
    char cnic[14], pass_number[10], age_type[10], class_type_str[20],seat_type_str[20];
    int dist_price = 0, correct = 0, validity = 0, seat_type, class_type, launch = 0, age, no_passengers, flight_type,date,month,year,td,total_amount,weight,luggage,new_weight;
    int business_price = 20000, first_price = 30000, economic_price = 10000, launch_price = 5000, cash, choice, choice2,correct1=0, rec_cash, ret_cash, login, balance, balance1;

    //Want to login as Employee or User
   
    printf("Login in (Press 1 for Employee & Press 2 for User) : ");
    scanf("%d", &login);
    
    if (login == 1) {
        printf("Enter your Employee ID : ");
        scanf(" %s", id);
        if (strcmp(id, "k24-3086") == 0 || strcmp(id, "k24-3062") == 0 || 
            strcmp(id, "k24-3069") == 0 || strcmp(id, "k24-3068") == 0) {
            printf("Login Successfully\n");
        } else {
            printf("Invalid Employee ID.\n");
            return 1; // Exit program if login fails
        }
    } else {
    	
    	
    	//Asking number of passenger to ask their details
    	printf("Enter number of passengers: ");
        scanf("%d", &no_passengers);
        
        printf("Flight Type (Press 1 = National & Press 2 = International): ");
        scanf("%d", &flight_type);
        
        for(int i=1;i<=no_passengers;i++){
		
        printf("Enter your First name pass %d: ",i);
        scanf("%s", first_name); 
        printf("\n");
        
        printf("Enter your Last name pass %d: ",i);
        scanf("%s", last_name); 
        printf("\n");
        
        printf("Enter Father Name pass %d: ",i); 
        scanf(" %[^\n]", f_name);
        printf("\n");
    
        printf("Enter your Age pass %d: ",i);
        scanf("%d", &age); 
        printf("\n");
        if (age >= 0 && age <= 10) {
        	//to store (strcpy) Children in the age between 0 till 10
            strcpy(age_type, "Children");
        } else {
            strcpy(age_type, "Adult");
        }
        
        do {
            printf("Enter your Phone Number pass %d: +92 ",i);
            scanf("%s", phone_number);
            printf("\n");
            
            if (strlen(phone_number) == 10) {
            	//To tell that number should have 1o characters (strlen)
                printf("Phone number is valid.\n");
                correct = 1;
            } else {
                printf("Phone Number is invalid. It must contain exactly 10 digits.\n");
            }
        } while (correct == 0);

        do {
            printf("Enter your CNIC number pass %d (13 digits): ",i);
            scanf("%s", cnic);
            printf("\n");
            if (strlen(cnic) == 13) {
                printf("CNIC is valid.\n");
                correct1 = 1;
            } else {
                printf("CNIC is invalid. It must contain exactly 13 digits.\n");
            }
        } while (correct1 == 0);
    
        printf("Enter your Email pass%d: ",i);
        scanf(" %s", email);
        printf("\n");
    

    
        if (flight_type == 1) {
            printf("Proceeding\n");
        } else {
            int valid_passport = 0;
            do {
                printf("Enter your Passport Number pass %d (e.g., AA1234567): ",i);
                scanf(" %s", pass_number);
                printf("\n");
                
                if (strlen(pass_number) == 9 && 
                    isalpha(pass_number[0]) && isalpha(pass_number[1]) && 
                    isdigit(pass_number[2]) && isdigit(pass_number[3]) &&
                    isdigit(pass_number[4]) && isdigit(pass_number[5]) &&
                    isdigit(pass_number[6]) && isdigit(pass_number[7]) &&
                    isdigit(pass_number[8])) {
                    printf("Valid Passport Number.\n");
                    printf("\n");
                    valid_passport = 1;
                } else {
                    printf("Invalid Passport Number. Format must be: AA1234567\n");
                    printf("\n");
                }
            } while (!valid_passport);
        }
        printf("Enter your luggage Weight in Kgs \n for domestic flight Weight in Kgs <= 10kg\n for international flight Weight in Kgs <=20kg\n Extra luggage 3000/- per Kg : ");
        scanf("%d",&weight);
        
        if(flight_type == 1){
        	if(weight <=10){
        		luggage=0;
			}else{
				new_weight= weight-10;
				luggage=1;
			}
		}else{
			if(weight<=20){
				luggage = 0;
			}else{
				new_weight= weight-20;
				luggage = 1;
			}
		}
        
    }
        // Input for Destination
        printf("Enter your Destination: ");
        scanf("%s", dest);

        // Determine distance price based on destination
        if (strcmp(dest, "India") == 0 || strcmp(dest, "INDIA") == 0) {
            dist_price = 50000;
        } else {
            dist_price = 40000;  // Default for other destinations
        }


 //date validation

            printf("Enter your travelling date : ");
            scanf("%d",&date);
            printf("Enter your travelling month : ");
            scanf("%d",&month);
            printf("Enter your travelling year : ");
            scanf("%d",&year);

   if(month == 2){
		if(year%4 == 0){
			td=29;
		   if(date <=29){
			printf("Valid date");
			printf("\n");

		    }else{
			printf("Invalid date");
			printf("\n");
		}}else{
			td=28;
			if(date <=28){
				printf("Valid date");
				printf("\n");
			
			}else{
				printf("Invalid date");
				printf("\n");
			}
		}
	}else if(month == 4 || month==6 || month==9 ||month== 11 ){
		td=30;
		if(date<=30){
			printf("Valid date");
			printf("\n");

		}else{
			printf("Invalid date");
			printf("\n");
		}
	}else{
		td=31;
		if(date<=31){
			printf("Valid date");
			printf("\n");


		}else{
			printf("Invalid date");
			printf("\n");
		}
	}


        // Input for Seat Type
        do{
		printf("Enter your Class type (1 = Economic, 2 = Business, 3 = First Class)\n Economic = 10000/-\n Business = 20000/-\n First Class = 30000/-: ");
        scanf("%d", &class_type);
        printf("\n");
        if(class_type >=1 && class_type <= 3){
        	printf("Proceeding ..... \n");
        	correct = 1;
		}else{
			printf("Wrong entry");
			printf("\n");
			correct = 0;
		}}while(correct == 0);
		
        if(class_type == 1){
        	strcpy(class_type_str,"Economy Class");
		}else if(class_type == 2){
        	strcpy(class_type_str,"Bussiness Class");
        }else{
        	strcpy(class_type_str,"First Class");
		}
        do{
		printf("Enter your Seat type (Press 1 = Window Seat & Press 2 = Normal Seat): "); 
        scanf("%d", &seat_type);
        printf("\n");
         if(seat_type ==1 || seat_type == 2){
        	printf("Proceeding ..... \n");
        	correct = 1;
		}else{
			printf("Wrong entry");
			correct = 0;
		}}while(correct == 0);
		
	    if(seat_type == 1){
        	strcpy(seat_type_str,"Window Seat");

        }else{
        	strcpy(seat_type_str,"Normnal Seat");
		}

        // Determine seat type and cost
        if (class_type == 2) {
            printf("You have got a free lounge area over your ticket.\n");
            printf("\n");
            launch = 1;  // Lounge access included
            cash = dist_price + business_price;
            if(luggage == 0){
            
			        	total_amount = cash*no_passengers;
            	
//                   if(strcmp(age_type ,"Children")==0){
//            	        total_amount = (cash-cash*0.1)*no_passengers;
//		           	}else{
//			        	total_amount = cash*no_passengers;
//			        }
			}else{
				total_amount = (cash*no_passengers)+(new_weight*3000);
//				    if(strcmp(age_type , "Children")==0){
//                       	total_amount = ((cash-cash*0.1)*no_passengers)+(new_weight*3000);
//		          	}else{
//			           	total_amount = (cash*no_passengers)+(new_weight*3000);
//			}
		}
            strcpy(class_type_str, "Business");
        } else if (class_type == 3) {
            printf("You have got a free lounge area over your ticket.\n");
            launch = 1;
            cash = dist_price + first_price;
            if(luggage == 0){
            	total_amount = cash*no_passengers;
//			        if(strcmp(age_type , "Children")==0){
//            	        total_amount = (cash-cash*0.1)*no_passengers;
//			        }else{
//				        total_amount = cash*no_passengers;
//			        }
	        }else{  
	        total_amount = (cash*no_passengers)+(new_weight*3000);
//			        if(strcmp(age_type , "Children")==0){
//                       	total_amount = ((cash-cash*0.1)*no_passengers)+(new_weight*3000);
//		          	}else{
//			           	total_amount = (cash*no_passengers)+(new_weight*3000);
				
			}
            strcpy(class_type_str, "First Class");
        } else {
            printf("Do you want a lounge area in your ticket (Y/N)?\n lounge area charges = 5000/-: ");
            scanf(" %c", &choice);
            if (choice == 'Y' || choice == 'y') {
//                launch = 1;
                cash = dist_price + economic_price + launch_price;
                if(luggage == 0){
                	total_amount = cash*no_passengers;
//				        if(strcmp(age_type , "Children")==0){
//                           	total_amount = (cash-cash*0.1)*no_passengers;
//		              	}else{
//			               	total_amount = cash*no_passengers;
//			            }
			    }else{	
			    total_amount = (cash*no_passengers)+(new_weight*3000);
//			            if(strcmp(age_type , "Children")==0){
//                           	total_amount = ((cash-cash*0.1)*no_passengers)+(new_weight*3000);
//		            	}else{
//			            	total_amount = (cash*no_passengers)+(new_weight*3000);
//                        }
			    }
			}else{
            	
                cash = dist_price + economic_price;
                if(luggage == 0){
                	total_amount = cash*no_passengers;
				
//                    if(strcmp(age_type , "Children")==0){
//            	        total_amount =(cash-cash*0.1)*no_passengers;
//			        }else{
//			           	total_amount = cash*no_passengers;
//			        }
            }else{
            	total_amount = (cash*no_passengers)+(new_weight*3000);
//            	     if(strcmp(age_type , "Children")==0){
//                       	total_amount = ((cash-cash*0.1)*no_passengers)+(new_weight*3000);
//		          	}else{
//			           	total_amount = (cash*no_passengers)+(new_weight*3000);
//		           	}
			}
            strcpy(class_type_str, "Economic");
        }}

        // Display final price
        printf("Your final price for all the expenses is: %d\n", total_amount);

        // Mode of Payment
        printf("How would you like to pay? (1 = Cash, 2 = Debit Card, 3 = Online payment): ");
        scanf("%d", &choice2);
        printf("\n");

        if (choice2 == 1) {
            printf("Please submit the cash: ");
            scanf("%d", &rec_cash);
            printf("\n");
            

            if (rec_cash == total_amount) {
                printf("Payment received successfully.\n");
                printf("\n");
            } else if (rec_cash > total_amount) {
                ret_cash = rec_cash - total_amount;
                printf("Payment received successfully.\nYour change is %d.\n", ret_cash);
                printf("\n");
            } else {
                printf("Insufficient cash. Process failed.\n");
                printf("\n");
            }
        } else if (choice2 == 2) {
            printf("Enter the balance of your Debit card: ");
            printf("\n");
            scanf("%d", &balance);
            if (balance >= total_amount) {
                printf("Payment received successfully.\n");
                printf("\n");
            } else {
                printf("Insufficient balance. Process failed.\n");
                printf("\n");
            }
        } else {
            printf("Kindly pay the amount on this Account Number 12345678901233\n");
            printf("\n");
            printf("Enter the balance of your Account: ");
            printf("\n");
            scanf("%d", &balance1);
            if (balance1 >= total_amount) {
                printf("Payment received successfully.\n");
                printf("\n");
            } else {
                printf("Insufficient balance. Process failed.\n");
                printf("\n");
            }
        }

        // Ticket Summary
        for(int i = 1;i<= no_passengers;i++){
        	
        	printf("Passenger %d",i);
        	printf("\n");
        	
		
        printf("\nYour ticket details:\n");
        printf("\n");
        printf("Date: %d/%d/%d", date,month,year);
        printf("\n");
        printf("Destination: %s\n", dest);
        printf("\n");
        printf("Name: %s\n", first_name);
        printf("\n");
        printf("CNIC: %s\n", cnic);  
        printf("\n");
        printf("Class Type: %s\n", class_type_str);
        printf("\n");
        printf("Saet Type : %s\n",seat_type_str);
        printf("\n");
        printf("Total Price: %d\n",total_amount );
        printf("\n");
    }}
    return 0;
}
