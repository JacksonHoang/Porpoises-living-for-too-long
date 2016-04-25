# Porpoises-living-for-too-long
The Immortal Porpoises question is proposed by the ACM Regional Collegiate Programming Contest.
/*
  *   The question states that these porpoise pairs live forever and it takes one year for a pair to reach adulthood to procreate to make a pair of porpoise babies. We will start with one pair of newborn porpoises. They will be ready to procreate at the end of the second year. When the porpoise pairs reach one billion or more, one billion pairs will disappear. Some years the population disappears completely. When this happens, in the next year a single pair appears. 
	*   The programming job is to determine the number of immortal porpoise pairs alive at the end of a given number of years. The years will go up only to 248,so we do not need to go past that year. The input will be a single integer  P, (1  P  1000), which is the data sets. Each data set includes a single line of input of two values separated by a space. The first value is an integer K which is the data set number. The second value is  Y, (1  Y  248), is the number of years the porpoises have been alive. 
*/

import java.util.*;
public class porpoises 
{
	public static void main (String [] args)
	{
		Random rn= new Random();
		int dataSets = rn.nextInt(10);
		dataSets = dataSets+10;
		/*
		 * Unable to figure out how to get to 2^48 years
		 * This is because Arrays only hold up to a little over 2 million array elements
		 * How to get over trillions of elements?
		 */
		int[] a= new int[2000000]; //This array here has 2 million. This number represents the years
		
		// The count is for: # of Porpoises alive... Need a count and year because they must not be intertwined
		//The year in  a[year]  dictates year in array with amount of porpoise
		int count=0;
		for(int year=1; year<((a.length-1)); year++)
		{  
			if(count<=1)
			{
				a[year]=1;
				count++;
			}
			else if (count>1)
			{
				a[year]= ( a[year-1]+ a[year-2]);
				if(a[year]<1000000000){   
					count= ( a[year-1]+ a[year-2]);
				}
				else if(a[year]>=1000000000){	
					a[year]= (a[year]-1000000000);
					count= a[year];
				}
			}
		}

		System.out.println("Random sets: " + dataSets );
		System.out.println("YEAR	POPROISES");
		
		for(int z=0; z<dataSets; z++) //Shall we sort it?
		{
			int randomYears = rn.nextInt(2000000-1); // Random Year selected
			System.out.println(randomYears + "	" + a[randomYears] ); // Prints Year and Porpoises Alive
		}
		
		System.out.println(" "); // Year 44-46 are correct by ACM site
		System.out.println("Year: 44 " + a[44] ); 
		System.out.println("Year: 45 " + a[45] );
		System.out.println("Year: 46 " + a[46] );
		System.out.println("Year: 47 " + a[47] );
		System.out.println("Year: 48 " + a[48] );
		System.out.println("Year: 49 " + a[49] );
	}
}
