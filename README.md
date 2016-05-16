# Lab-Task
#include<iostream>
#include<cstdlib>
#include<windows.h>

using namespace std;

class ATM
{
	private:
		int code,cash;
	
	public:
		int accountno;
		int Cashview(void);
		void enter_code_cash(int Code,int Cash);
		int entercode(int Code);
		void withdraw(int Cash);
		void paybills(int Cash);
		void transfer(int Accountno,int Cash);
		void query(int Code,int Cash);
};

int ATM::Cashview()
{
	return cash;
}

void ATM::paybills(int Cash)
{
	cout<<endl<<"Your amount is being deducted for bill payment.........."<<endl;
	Sleep(2000);
	cout<<"Your bils have been paid"<<endl<<"Remaining amount in account:"<<cash-Cash<<endl<<endl;
}

void ATM::query(int Code,int Cash)
{
	cout<<endl<<"Amount present in your account ("<<code<<")is "<<cash<<endl;
	cout<<"Last transferred amount is "<<Cash<<" to account no "<<Code<<endl<<endl;
}

void ATM::enter_code_cash(int Code,int Cash)
{
	code=Code;
	cash=Cash;
}

int ATM::entercode(int Code)
{
	if(Code==code)
	{
		cout<<"Correct code entered"<<endl<<endl;
		return 1;
	}
	else
	{
		cout<<"Incorrect code"<<endl<<endl;
		return 0;
	}
}

void ATM::transfer(int Accountno,int Cash)
{
	cout<<"Amount is being transferred to account no "<<Accountno<<"..............\n"<<endl<<endl;
	Sleep(2000);
	cash=cash-Cash;
}

void ATM::withdraw(int Cash)
{
	cout<<"Amount is being sent to you............"<<endl;
	Sleep(2000);
	cout<<"Amount has been sent to you"<<endl<<"Your amount is "<<Cash<<endl<<"Remaining amount: "<<cash-Cash<<endl<<endl;
	cash=cash-Cash;
}

int main(void)
{
	ATM faseeh,zain;
	int accountno,cash;
	while(1)
	{
		int choice;
		cout<<"What would you like to do?"<<endl;
		cout<<"To enter code, enter 1"<<endl;
		cout<<"To withdraw money, enter 2"<<endl;
		cout<<"To transfer money, via account no, enter 3"<<endl;
		cout<<"To pay bills, enter 4"<<endl;
		cout<<"To get your card, and to exit the program, enter 5"<<endl;
		cout<<"Your choice:";
		cin>>choice;
		if(choice==1)
		{
			cout<<endl<<"Please enter your code (without spaces):";
			cin>>accountno;
			cout<<"Please enter the cash amount(without comma and spaces):";
			cin>>cash;
			faseeh.enter_code_cash(accountno,cash);
			cout<<endl;
		}
		if(choice==2&&faseeh.Cashview()!=0&&faseeh.Cashview()>0)
		{
			while(1)
			{
				cout<<endl<<"Please enter the code(for withdrawal, same code as you entered):";
				cin>>accountno;
				int correct=faseeh.entercode(accountno);
				if(correct==1)
				{
					int cash;
					cout<<endl<<"Please enter the amount to be wuthdrawn:";
					cin>>cash;
					faseeh.withdraw(cash);
					break;
				}
				else
				{
					continue;
				}
			}
		}
		else
		{
			cout<<endl<<"Your amount is not present in account"<<endl;
		}
		if(choice==3&&faseeh.Cashview()!=0&&faseeh.Cashview()>0)
		{
			cout<<endl<<"Please enter the number of the account(in which the amount is to be transferred,it must be eight digits):";
			cin>>zain.accountno;
			cout<<"Please enter the amount to be transferred:";
			int transferamount;
			cin>>transferamount;
			zain.enter_code_cash(accountno,transferamount);
			faseeh.transfer(zain.accountno,transferamount);
			faseeh.query(zain.accountno,transferamount);
		}
		else
		{
			cout<<endl<<"Your amount is not present in account"<<endl;
		}
		if(choice==4&&faseeh.Cashview()!=0&&faseeh.Cashview()>0)
		{
			int cash;
			cout<<endl<<"Please enter the amount of the bill/bills (total without spaces):";
			cin>>cash;
			faseeh.paybills(cash);
		}
		else
		{
			cout<<endl<<"Your amount is not present in account"<<endl<<endl;
		}
		if(choice==5)
		{
			cout<<endl<<"Thank you for coming"<<endl;
			break;
		}
	}
}
