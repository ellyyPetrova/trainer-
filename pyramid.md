
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



