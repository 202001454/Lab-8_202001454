# <pre>                  IT314 - Software Engineering </pre>

#### Name       : Deep Kanani
#### Student ID  : 202001454
#### Date       : 21/04/2023

----

## Objective:
    The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.
    
----
1. Creating eclipse project named 'Lab8_202001454' and a package named 'myPackage' inside src folder in it.
2. Creating a class for a Boa with the given code snippet in the lab manual.
```
public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}
	
	//returns true if this Boa constructor is healthy
	public boolean isHealthy(){
		return this.favoriteFood.equals("granola bars");
	}
	
	//returns true if the length of this Boa constructor is
	//less than the given cage length
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength;
	}
}	
```
![2](https://user-images.githubusercontent.com/75676330/233604289-fbc77431-9989-4ce5-827a-d269877691d8.jpg)

3. Creating JUnit test file named 'BoaTest'.  

![3](https://user-images.githubusercontent.com/75676330/233604332-c82a073f-30c9-4f7f-88ec-359e5fd6ada0.jpg)

4. Initializing ken and jen as private Boa's.
```
import static org.junit.Assert.*;
import org.junit.After;
import org.junit.Assert;
import org.junit.Before;
import org.junit.Test;
public class BoaTest {
	
	private Boa jen, ken;
	
	@Before
	public void setUp() throws Exception {
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa("Kenneth", 3, "granola bars");
	}
}
```
![4](https://user-images.githubusercontent.com/75676330/233604378-af4d3c1a-86c3-4208-9637-ce739be27ded.jpg)

5. Implementing test cases for **isHealthy()** and **fitsInCage()** functions.
```
import static org.junit.Assert.*;
import org.junit.After;
import org.junit.Assert;
import org.junit.Before;
import org.junit.Test;
public class BoaTest {
	
	private Boa jen, ken;
	
	@Before
	public void setUp() throws Exception {
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa("Kenneth", 3, "granola bars");
	}
	@After
	public void tearDown() throws Exception {
	}
	@Test
	public void testIsHealthy() {
		// IsHealthy testing for jen
		Assert.assertFalse(jen.isHealthy());
		
		// IsHealthy testing for ken
		Assert.assertTrue(ken.isHealthy());
	}
	
	@Test
	public void testFitsInCage() {
		// FitsInCage testing for jen
		Assert.assertFalse(jen.fitsInCage(1));
		Assert.assertFalse(jen.fitsInCage(2));
		Assert.assertTrue(jen.fitsInCage(3));
		
		// FitsInCage testing for ken
		Assert.assertFalse(ken.fitsInCage(2));
		Assert.assertFalse(ken.fitsInCage(3));
		Assert.assertTrue(ken.fitsInCage(4));
	}
}
```
![5](https://user-images.githubusercontent.com/75676330/233604402-d2f493fd-ee30-4069-92a4-ffdf66a7c0ad.jpg)

For testing thee fitsInCage() function, there is no need to write tests for both jen and ken objects as the function is same for both and the output of test cases depends only whether the given lenght is greater than,less than or equal to actual length of object.The behaviour will be similar in both cases.

6. Running the tes cases. All test cases are passed and there is no red bars in the output. Both 2 test cases are passed.

![6](https://user-images.githubusercontent.com/75676330/233604433-6b10ba9b-f080-441b-8985-a4f2c9ac7c62.jpg)

7. Adding a new method to the Boa class with name lenghtInInches() to get the length in inches.
```
//returns the length of the Boa in inches
public int lenghtInInches() {
  return this.length * 12;
}
```
![7](https://user-images.githubusercontent.com/75676330/233604466-f30c0e11-a524-496e-bb60-c60009dbd3c4.jpg)

As the length of the Boa is given in feet, to convert it into inches, We simply multiply length with 12 and return the value.

8. Adding another test case and running all 3 test cases together.
```
@Test
public void testLengthInInches() {
  // Length in inches of Boa-Jen should be 2*12=24
  assertEquals(24, jen.lenghtInInches());
        
  // Length in inches of Boa-Ken should be 3*12=36
  assertEquals(36, ken.lenghtInInches());
}
```
![8](https://user-images.githubusercontent.com/75676330/233604527-aad455d6-cfc9-43b4-b99c-bacdd47f5396.jpg)

As a result, test cases have been created for the specified Boa class, and the necessary Junit test cases have been used to test all three methods.
