#include <iostream>
#include <iomanip>
using namespace std;

class Time
{
private:
    int hours, minutes, seconds;

public:
    
    Time()
    {
        hours = 0;
        minutes = 0;
        seconds = 0;
    }

    
    Time(int h, int m, int s)
    {
        int total = h * 3600 + m * 60 + s;

        hours = total / 3600;
        minutes = (total % 3600) / 60;
        seconds = total % 60;
    }

   
    Time operator+(Time t)
    {
        int total1 = hours * 3600 + minutes * 60 + seconds;
        int total2 = t.hours * 3600 + t.minutes * 60 + t.seconds;

        int sum = total1 + total2;

        return Time(0, 0, sum);
    }

    
    void display()
    {
        cout << setfill('0') << setw(2) << hours << ":"
             << setw(2) << minutes << ":"
             << setw(2) << seconds << endl;
    }
};

int main()
{
    int h1, m1, s1, h2, m2, s2;
    int choice;

    do
    {
        cout << "\n===== TIME CALCULATOR =====";
        cout << "\n1. Add Two Time Durations";
        cout << "\n2. Demonstrate Default Constructor";
        cout << "\n3. Exit";
        cout << "\nEnter your choice: ";
        cin >> choice;

        switch (choice)
        {
        case 1:
        {
            cout << "\nEnter first time (hours minutes seconds): ";
            cin >> h1 >> m1 >> s1;

            cout << "Enter second time (hours minutes seconds): ";
            cin >> h2 >> m2 >> s2;

            Time t1(h1, m1, s1);
            Time t2(h2, m2, s2);

            Time t3 = t1 + t2;

            cout << "\nFirst Time: ";
            t1.display();

            cout << "Second Time: ";
            t2.display();

            cout << "Total Time: ";
            t3.display();

            break;
        }

        case 2:
        {
            Time t;
            cout << "\nDefault Constructor Output: ";
            t.display();

            break;
        }

        case 3:
            cout << "\nExiting Time Calculator...";
            break;

        default:
            cout << "\nInvalid Choice!";
        }

    } while (choice != 3);

    return 0;
}
