# Shop
/*Develop an Inventory class for a retail warehouse. Create a restock() method that is
overloaded to handle different incoming shipment types: one version takes a String item
name and an int quantity, another takes a String category name and an int percentage to
increase all items in that group, and a third takes an array of String names for a bulk
&quot;variety pack&quot; update. Show how the inventory object manages its stock levels using
these varied input methods*/

#include <iostream>
#include <string>
using namespace std;
class inventory
{
private:
    string item[5]={"Rice","Water","Milk","Juice","Chips"};
    int stock[5]={90,80,50,70,50};
public:
    void restock(string name,int quantity)
    {
        for(int i=0;i<5;i++)
        {
            if(item[i]==name)
            {
                stock[i]=stock[i]+quantity;
                cout<<"Item Name: "<<name<<endl;
                cout<<"Amount: "<<quantity<<endl;
            }
        }

    }
    void restock(string category,float per)
    {

        cout<<"Category Name: "<<category<<endl;
        for(int i=0;i<5;i++)
        {
            int increase;
            increase=stock[i]*per/100.00;
            stock[i]=stock[i]+increase;
        }
    }
    void restock(string arr[],int n)
    {
        for(int i=0;i<5;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(item[i]==arr[j])
                {
                    stock[i]=stock[i]+10;
                    cout << arr[j]
                         << " increased by 10 units."
                         << endl;
                }
            }
        }
    }
    void showInventory()
    {
        cout << "\nCurrent Inventory:\n";

        for (int i = 0; i < 5; i++)
        {
            cout << item[i]
                 << " : "
                 << stock[i]
                 << endl;
        }
    }
};
int main()
{
    inventory c;
    c.showInventory();
    c.restock("Rice",20);
    c.restock("grosoury",10.0f);
    string strarr[]={"Chips","Milk","Water"};
    c.restock(strarr,3);
    c.showInventory();

}
