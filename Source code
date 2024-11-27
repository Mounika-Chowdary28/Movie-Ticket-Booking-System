#include<iostream>
#include<string>
#include<limits>
#include<ctime>
#include<cstdlib>
#include<set> //Include set for unique seat tracking
using namespace std;
//Color codes
const string RESET="\033[0m";        //Reset to default color
const string RED="\033[31m";         //Red
const string GREEN="\033[32m";       //Green
const string BLUE="\033[34m";        //Blue
const string YELLOW="\033[33m";      //Yellow
const string WHITE="\033[37m";       //White
const string BRIGHT_GREEN="\033[1;32m"; //Bright Green
// Class definition for ticket
class Ticket{
public:
    string name;
    string contactNo;
    int seatNumber; //Added seat number to the Ticket class
};
//Class definition for card
class Card:public Ticket{
public:
    string address;
    string emailId;
};
//Function prototypes
void pay(int,bool &paymentSuccessful,int &ticketPrice);
void cardRegistration();
void menu();
void clearScreen();
int getRandomSeat(set<int>&occupiedSeats); // Function prototype
// Function to clear the console screen 
void clearScreen(){
    system("CLS");
}
// Function to generate a random unique seat number
int getRandomSeat(set<int>&occupiedSeats){
    int seatNumber;
    do{
        seatNumber=rand()%100+1;//Random number between 1 and 100
    }while(occupiedSeats.find(seatNumber)!=occupiedSeats.end());
    return seatNumber;
}
void menu(){
    clearScreen();
    cout<<YELLOW<<"\n\t\t\t ----------------------------------";
    cout<<"\n\t\t\t\t     MOVIE BUZZ";
    cout<<"\n\t\t\t ----------------------------------";
    cout<<BRIGHT_GREEN<<"\n\t\t\t\t Welcome Customer!"<<RESET;
    cout<<RED<<"\n\n\t\t\t\t <1> Movie Timings";
    cout<<"\n\t\t\t\t <2> Contact Us";
    cout<<"\n\t\t\t\t <3> DTCard Registration";
    cout<<"\n\t\t\t\t <4> Exit \n\n"<<RESET;
    cout<<WHITE<<"\t\t\t\tEnter Your Choice: "<<RESET;
}
// Function to handle ticket purchase
void handleTicketPurchase(int x,string name,string contactNo,string showTime){
    set<int>occupiedSeats; //Set to track occupied seat numbers
    cout<<GREEN <<"\n\n\t\t\t\t TICKET DETAILS ARE : "<<RESET<<"\n";
    cout<<"\n\t\t\t\t Name: "<<name;
    cout<<"\n\t\t\t\t Contact No: "<<contactNo;
    cout<< "\n\t\t\t\t Show Timings: "<<showTime;
    for (int i=0;i<x;++i){
        Ticket t;
        t.seatNumber=getRandomSeat(occupiedSeats);//Get unique seat number
        occupiedSeats.insert(t.seatNumber); //Track the occupied seat
        cout<<"\n\t\t\t\t Seat Number: "<<t.seatNumber; //Show assigned seat
    }
    cout<<GREEN<<"\n\n\t\t\t\t ENJOY YOUR MOVIE\n"<<RESET;
}
//Main function
int main(){
    int choice,movie,b,x;
    char ans;
    bool paymentSuccessful=false;  //Add this flag to check payment status
    int ticketPrice=0; // Variable to hold ticket price
    do{
        menu();
        while(!(cin>>choice)||(choice<1||choice>4)){
            cout<<RED<<"Invalid selection - Please input 1 to 4 only."<<RESET<<"\n";
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(),'\n');
        }
        switch(choice){
            case 1: {
                clearScreen();
                cout<<BLUE<<"\n\n\t\t\t\t Movies :";
                cout<<"\n\t\t\t\t 1. AMARAN";
                cout<<"\n\t\t\t\t 2. DEVARA";
                cout<<"\n\t\t\t\t 3. LUCKY BHASKAR";
                cout<<"\n\t\t\t\t 4. KALKI 2898 AD";
                cout<<"\n\t\t\t\t 5. SARIPODHAA SANIVAARAM\n";
                cout<<RESET<<"\n\t\t\t\tEnter Your Choice: ";
                cin>>movie;
                cout<<BLUE<<"\n\n\t\t\t\t The Timings for the selected show are:";
                cout<<"\n\t\t\t\t 1. 08:00 AM";
                cout<<"\n\t\t\t\t 2. 1:00 PM";
                cout<<"\n\t\t\t\t 3. 3:30 PM";
                cout<<"\n\t\t\t\t 4. 6:00 PM";
                cout<<"\n\t\t\t\t 5. 9:00 PM";
                cout<<"\n\t\t\t\t 6. 01:00 AM\n";
                cout<<RESET<<"\n\n\t\t\t\t Please select the timings: ";
                cin>>b;
                string showTime;
                switch(b){
                    case 1:showTime="08:00 AM"; 
					break;
                    case 2:showTime="1:00 PM";
					break;
                    case 3:showTime="3:30 PM"; 
					break;
                    case 4:showTime="6:00 PM"; 
					break;
                    case 5:showTime="9:00 PM"; 
					break;
                    case 6:showTime="01:00 AM"; 
					break;
                    default:showTime="Invalid input"; 
					break;
                }
                cout<<"\n\t\t\t\t Enter the number of tickets you want to purchase: ";
                cin>>x;
				string name,contactNo;//Enter the common name and contact number for all tickets
                cout<<"\n\t\t\t\t Enter your name: ";
                cin>>name;
                cout<<"\n\t\t\t\t Enter your contact number: ";
                cin>>contactNo;
                while(contactNo.length()!=10){
                    cout<<RED<<"\t\t\t\tPlease enter a valid mobile number: "<<RESET;
                    cin>>contactNo;
                }
                //Call the pay function and capture whether it was successful
                pay(x,paymentSuccessful,ticketPrice);
                if(paymentSuccessful){  //Only print the ticket if the payment was successful
                    handleTicketPurchase(x,name,contactNo,showTime); //Handle ticket purchase
                }
                break;
            }
            case 2:
                clearScreen();
                cout<<YELLOW<<"For further information about movies you can download our Application or contact us at 01234567896523"<<RESET;
                break;
            case 3:
                clearScreen();
                cardRegistration();
                break;
            case 4:
                clearScreen();
                cout<<GREEN<<"\n\t\t\t\tTHANK YOU AND VISIT AGAIN!\n\n\t\t\t\t"<<RESET;
                exit(0);
                break;
        }
        cout<<"\n\n\t\t\t\t Do you want to choose another option (y/n)? ";
        cin>>ans;
    }while(ans=='y');
    return 0;
}
// Function Declaration for Card Registration
void cardRegistration(){
    Card v;
    cout<<YELLOW<<"\t\t\t\tWelcome to register for card facility in our cinemas"<<RESET;
    cout<<"\n\t\t\t\t Enter your name: "<<WHITE;
    cin>>v.name;
    cout<<RESET<<"\t\t\t\tEnter your mobile number: "<<WHITE;
    cin>>v.contactNo;
    while(v.contactNo.length()!=10){
        cout<<RED<<"\t\t\t\tPlease enter a valid mobile number: "<<RESET;
        cin>>v.contactNo;
    }
    // Validate email input to ensure it contains '@'
    cout<<WHITE<<"\t\t\t\tEnter the mail id: "<<RESET;
    cin>>v.emailId;
    while(v.emailId.find('@')==string::npos){
        cout<<RED<<"\t\t\t\tInvalid email. Please enter a valid email : "<<RESET;
        cin>>v.emailId;
    }
    int ID;
    srand(static_cast<unsigned int>(time(0)));
    ID=rand()%400000+4000000;
    cout<<BRIGHT_GREEN<<"\t\t\t\tYour new card number is :- "<<ID<<RESET;
    cout<<"\n\t\t\t\tName: "<<v.name<< "\n\t\t\t\tMobile No.: "<<v.contactNo<<"\n\t\t\t\tMail ID: "<<v.emailId<<"\n\t\t\t\tCard Number: "<<ID<< "\n";
    cout<<GREEN<<"\n\t\t\t\tThank you for the registration for the card.\n"<<RESET;
}
// Payment system for the interface
void pay(int a,bool&paymentSuccessful,int &ticketPrice){
    int amt;
    cout<<GREEN<<"\t\t\t\tThank you for selecting the show.\n"<<RESET;
	cout<<YELLOW<<"\t\t\t\tNow we request you to select your type of seating \n"<<RESET;
	cout<<"\t\t\t\t 1. Normal Class \n\t\t\t\t OR \n\n\t\t\t\t 2. Gold Class :-  ";
    int c;
    cin>>c;
    while(c!=1&&c!=2){
        cout<<RED<<"\t\t\t\tInvalid selection - Please input 1 or 2 only."<<RESET<<"\n";
        cin>>c;
    }
    if(c==1){
        cout<<"\n\n\t\t\t\tYou selected Normal Class \n\n\t\t\t\t";
        amt=a*200;
        ticketPrice=200;
    } 
	else{
        cout<<"\n\n\t\t\t\tYou selected Gold Class \n\n\t\t\t\t";
        amt=a*700;
        ticketPrice=700;
    }
    cout<<"\n\t\t\t\tWant to pay by Card (y/n): ";
    char rep;
    cin>>rep;
    cout<<"\n\t\t\t\tTotal Amount to Pay: "<<amt<<"\n";
    if(rep=='y'||rep=='Y'){
        // Card payment details
        cout<<"\t\t\t\tName of the card holder: ";
        string cardHolderName;
        cin>>cardHolderName;
        cout<<"\n\t\t\t\tEnter the card number (Max 12 digits): ";
        string cardNumber;
        cin>>cardNumber;
        if(cardNumber.length()>12){
            cout<<RED<<"\t\t\t\tInvalid Card Number. Payment failed. Try again later."<<RESET<<"\n";
            paymentSuccessful=false;
            return;
        }
        cout<<"\t\t\t\tExpiry (MM/YYYY): ";
        string expiry;
        cin>>expiry;
        if(expiry.length()==7&&expiry[2]=='/'){
            int expirymm=atoi(expiry.substr(0,2).c_str());
            int expiryyy=atoi(expiry.substr(3,4).c_str());
            time_t t=time(0);
            tm*now=localtime(&t);
            int currentYear=now->tm_year+1900;
            int currentMonth=now->tm_mon+1;
            if(expirymm<1||expirymm>12||(expiryyy<currentYear||(expiryyy==currentYear&&expirymm<currentMonth))){
                cout<<RED<<"\t\t\t\tThe card has expired or has an invalid date. Try again later."<<RESET<<"\n";
                paymentSuccessful=false;
                return;
            }
            cout<<"\t\t\t\tEnter the CVV/CVV2 (3 digits): ";
            string cvv;
            cin>>cvv;
        if(cvv.length()!=3){
          cout<<RED<<"\t\t\t\tInvalid CVV. Payment failed. Try again later."<<RESET<<"\n";
           paymentSuccessful=false;
            return;
           }
            cout<<GREEN<<"\t\t\t\tPayment processed successfully!"<<RESET<<"\n";
            paymentSuccessful=true;
        } 
		else{
            cout<<RED<<"\t\t\t\tInvalid expiry date format. Use MM/YYYY."<<RESET<<"\n";
            paymentSuccessful=false;
            return;
        }
    } 
	else{
        cout<<YELLOW<<"\t\t\t\tProceeding without card payment. You can pay at the counter."<<RESET<<"\n";
        paymentSuccessful=true; //Allow ticket printing for offline payment
    }
}
