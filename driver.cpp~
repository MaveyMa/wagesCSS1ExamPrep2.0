// Name: Mavey Ma
// Created: Nov. 5, 2015
// Wages CSS1 Test Prep
/* Given data.txt, calculate wages and output to wages.txt
There is a 5% food tax and a 8% state tax.
If they worked more than 40 hours, pay time and a half the regular pay.
*/

#include <iostream> //cout
#include <fstream> //ifstream, ofstream
#include <string> //data type string
#include <cstdlib> //exit(1)
#include <iomanip> //setf, setw, ios::fixed::showpoint::left, precision
using namespace std;

void overtime(int hoursWorked, double& wageEarned);
void foodTax(double& wageEarned);
void stateTax(double& wageEarned);

int main()
{
    ifstream fin;
    ofstream fout;
    fin.open("data.txt");
    fout.open("wages.txt");
    string first, last;
    int hours;
    double wage;
    
    if (fin.fail() || fout.fail())
    {
        cout << "ERROR: CANNOT OPEN FILE(S).\n";
        exit(1);
    }//END FAIL CHECK
    
    while (fin >> first >> last >> hours >> wage)
    {
        fout.setf(ios::fixed);
        fout.setf(ios::showpoint);
        fout.precision(2);
        fout.setf(ios::left);
        
        overtime(hours, wage);
        foodTax(wage);
        stateTax(wage);
        
        fout << setw(10) << first
             << setw(10) << last
             << setw(5) << hours
             << setw(10) << wage << endl;
    }//END WHILE 
    fin.close();
    fout.close();
    return 0;
}//END MAIN

void overtime(int hoursWorked, double& wageEarned)
{
    double overtimeRate = 1.5, regHrRate;
    int hoursOvertime;
    if (hoursWorked > 40)
    {
        hoursOvertime = hoursWorked - 40;
        regHrRate = wageEarned / (hoursWorked - hoursOvertime);
        wageEarned = (40 * regHrRate) + (hoursOvertime * overtimeRate);
    }
    else
    {
        regHrRate = wageEarned / hoursWorked;
        wageEarned = hoursWorked * regHrRate;
    }  
}//END OVERTIME

void foodTax(double& wageEarned)
{
    double tax = 0.05;
    double deduct = wageEarned * tax;
    wageEarned -= deduct;
}//END FOOD TAX

void stateTax(double& wageEarned)
{
    double tax = 0.08;
    double deduct = wageEarned * tax;
    wageEarned -= deduct;
}//END STATE TAX
