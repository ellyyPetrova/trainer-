
#include <iostream>


using namespace std;




int main()

{
	
  int num = 15;

  for (int i = 0; i < num; i++)
	
    {
	
      for (int j = 0; j <= i; j++)
	
       {
	
	  cout << "*";

       }
      for (int tab = 0; tab < num + 1 - i; tab++)
			
        cout << " ";
	

	for (int k = i; k < num; k++)
	
         {

            cout << "*";

         }
	
        for (int tab = 0; tab < 2 * i + 2; tab++)

          cout << " ";
	

      for (int p = i; p < num; p++) 
	
        {

          cout << "*";
	
        }
		
      for (int tab = 0; tab < num + 1 - i; tab++)
			
         cout << " ";
		
		

      for (int l = 0; l <= i; l++) 
		
        {
			 
           cout << "*";
		
        }
		
      cout << endl;
	 
     }

	return 0;

}




#include <iostream>
using namespace std;
int main()
{
	long dec, rem, i = 1, sum = 0;
	cout << "Enter the decimal number: ";
	cin >> dec;
	do
	{
		rem = dec % 2;
		sum = sum + (i*rem);
		dec = dec / 2;
		i = i * 10;
	} while (dec>0);
	cout << "" << sum << endl;
	
	return 0;
}





#include <iostream>
using namespace std;

int main()
{
	int in;
	int out = 0;
	int num = 0;
	int sum = 0;
	cin >> in;

	while (in > 0)
	{
		out = out * 10 + in % 10;
		sum += in % 10;
		in = in / 10;
		num++;
	}
	cout << "Numbers: " << num << endl;
	cout << "Sum: " << sum << endl;
	cout << "Out: " << out << endl;

	return 0;
}

