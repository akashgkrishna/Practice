# Practice

package check;

import org.testng.Assert;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.Test;


public class CalculatorTest {

    Calculator calculator;

    @BeforeMethod
    public void setUp(){
        calculator = new Calculator();
    }


    //To test addition function
    @Test (dataProvider = "additionData", dataProviderClass = DataProviderExample.class)
    private void testAdditionOfTwoNumbers(int a, int b, int result){
        //Act
        int addition = calculator.add(a, b);

        //Assert
        Assert.assertEquals(addition, result);
    }




    //To test Subtraction function
    @Test(groups ={"simple-problem"})
    private void testSubtractionOfTwoNumbers(){
        //Arrange
        int number1 = 3;
        int number2 = 2;

        //Act
        //Calculator calculator = new Calculator();
        int subtraction = calculator.subtract(number1, number2);

        //Assert
        Assert.assertEquals(subtraction, 1);
    }

    //To test multiply function
    @Test(groups ={"simple-problem"})
    private void testMultiplicationOfTwoNumbers(){
        //Arrange
        int number1 = 1;
        int number2 = 2;

        //Act
        // Calculator calculator = new Calculator();
        int multiplier = calculator.multiply(number1, number2);

        //Assert
        Assert.assertEquals(multiplier, 2);
    }

    //To test percentage function
//    @Test
//    private void testPercentageOfTwoNumbers(){
//        //Arrange
//        int number1 = 10;
//        int number2 = 20;
//
//        //Act
//        //Calculator calculator = new Calculator();
//        double checkPercentage = calculator.percentage(number1, number2);
//
//        //Assert
//        Assert.assertEquals(checkPercentage, 50);
//    }


    //enabled will ignore @Test method if it is set to false, by default it is true
//    @Test (enabled = false)
//    private void testPercentageCalculation(){
//        int number = 3;
//        int total = 10;
//
//        double value = calculator.percentage(number, total);
//
//        Assert.assertEquals(value, 40);
//    }


    //timeOut will skip certain test if it takes more than given time in timeOut
    //it also marks the test as fail if it takes more than the defined time, even if the test will be successful.
    //timeout is given in milliseconds 1000ms = 1sec
    //By default test run in alphabetical order, setting priority make that as priority and run according to that
    @Test (priority = 1, groups ={"hard-problem"}) //setting timeOut for 0.2sec and priority as 1
    private void testPercentageCalculation() throws InterruptedException {// exception due to sleep()
        int number = 3;
        int total = 10;

        Calculator calculator = new Calculator();
        double value = calculator.percentage(number, total);

        //to make the test take longer to complete were making it sleep for 5sec
        Thread.sleep(500);
        Assert.assertEquals(value, 30);
    }

    //To test square function
    @Test(groups ={"hard-problem"})
    private void testSquareOfNumber(){
        //Arrange
        int number = 10;


        //Act
        // Calculator calculator = new Calculator();
        double square = calculator.square(number);

        //Assert
        Assert.assertEquals(square, 100);
    }


    @AfterMethod
    private void tearDown(){
        System.out.println("End of test");
    }



}
