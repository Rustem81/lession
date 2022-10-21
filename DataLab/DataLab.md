
# Accessing a Database

## Creating and Using Entity Data Models

#### Preparation Steps

1. Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.

#### Steps

1. Navigate to the **[Repository Root]\Labs\DataLab\Databases** folder, and then double-click **SetupFourthCoffeeDB.cmd**.
    >**Note:** If a Windows protected your PC dialog appears, click **More info** and then click **Run Anyway**.
2. Locate **[Repository Root]\Labs\DataLab\Databases** folder again, right-click **FourthCoffee.sql**, point to **Open With**, click **Microsoft Visual Studio Version Selector**, then click **Open**.
3. Review the SQL query.
4. On the **File** menu, click **Close**.
5. On the **File** menu, point to **New**, and then click **Project**.
6. In the **New Project** dialog box, expand **Templates**, click **Visual C\#**, and then in the **Template** list, click **Console App(.NET Framework)**.
7. In the **Name** text box, type **FourthCoffee.Employees**, in the **Location** text box, type **[Repository Root]\Labs\DataLab\Demo1\Starter**, and then click **OK**.
8. In **Solution Explorer**, right-click **FourthCoffee.Employees**, point to **Add**, and then click **New Item**.
9. In the **Add New Item – FourthCoffee.Employees** dialog box, click **ADO.NET Entity Data Model**, in the **Name** text box, type **FourthCoffeeEmployeesModel**, and then click **Add**.
10. In **Entity Data Model Wizard**, on the **Choose Model Contents** page, click **EF Designer from database**, and then click **Next**.
11. On the **Choose Your Data Connection** page, click **New Connection**.
12. On the **Choose Data Source page**, Select **Microsoft SQL Server** and then click **OK**.
13. In the **Server name** text box, type **(localdb)\MSSQLLocalDB**, in the **Select or enter a database name** list, click **FourthCoffee**, and then click **OK**.
14. In **Entity Data Model Wizard**, on the **Choose Your Data Connection** page, click **Next**.
15. In the **Choose Your Version** page, choose **Entity Framework 6.x** and then click **Next**.
16. On the **Choose Your Database Objects and Settings** page, expand **Tables**, expand **dbo**, select **Branches**, **Employees**, and **JobTitles**, and then click **Finish**.
17. If a **Security Warning** dialog box appears, select **Do not show this message again**, and then click **OK**.
18. On the **Build** menu, click **Build Solution**.
19. Review the three entities that have been generated and the associations between them.
20. Right-click the designer surface, and then click **Mapping Details**.
21. In the **Designer** pane, click **Employee**.
22. In the **Mapping Details** pane, review the mappings between the entity and the data source.
23. In **Solution Explorer**, expand **FourthCoffeeEmployeesModel.edmx**, expand **FourthCoffeeEmployeesModel.Context.tt**, and then double-click **FourthCoffeeEmployeesModel.Context.cs**.
24. In the code editor, review the code in the **FourthCoffeeEntities** partial class.
25. In **Solution Explorer**, expand **FourthCoffeeEmployeesModel.tt**, and then double-click **Employee.cs**.
26. Review the **Employee** partial class and the properties that have been generated.
27. Leave the solution open so that you can refer to it in the following topics.

### Reading and Modifying Data in an EDM

#### Preparation Steps

Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.

#### Steps

1. Open **Visual Studio**.
2. In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.
3. In the **Open File** dialog box to, browse to the **[Repository Root]\Labs\DataLab\Demo2\FourthCoffee.Employees**, and then open the **FourthCoffee.Employees.sln** file.
    >**Note :** If any Security warning dialog box appears, clear **Ask me for every project in this solution** check box and then click **OK**.
4. In **Solution Explorer**, expand **FourthCoffee.Employees**, and then double-click **Program.cs**.
5. Review the definition of the **DBContext** variable.
6. Review the code in the **PrintEmployeesList** method that uses the **DBContext** variable to access the data in the EDM.
7. Review the code in the **Main** method that uses the **First** extension method to retrieve an employee and then modifies that employee’s **LastName** property.
8. On the **Build** menu, click **Build Solution**.
9. On the **Debug** menu, click **Start Without Debugging**.
10. Verify that the employees list is displayed, and then press Enter.
11. Verify that the employee named **Diane Prescott** is now named **Diane Forsyth** and then press Enter.
12. To close the application, press Enter.

## Querying Data by Using LINQ

#### Preparation Steps

Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.

#### Steps

1. Open **Visual Studio**.
2. In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.
3. In the **Open Project** dialog box, browse to the **[Repository Root]\Labs\DataLab\Demo3\FourthCoffee.Employees** folder, click **FourthCoffee.Employees.sln**, and then click **Open**.
    >**Note :** If any Security warning dialog box appears, clear **Ask me for every project in this solution** check box and then click **OK**.
4. In **Solution Explorer**, expand **FourthCoffee.Employees**, and then double-click **Program.cs**.
5. Review the LINQ code in each of the methods.
6. On the **Build** menu, click **Build Solution**.
7. On the **Debug** menu, click **Start Without Debugging**.
8. In the console window, review the output of the **QueryingData** method, and then press Enter.
9. Repeat step 8 for each of the following methods:
   - **FilteringDataByRow**
   - **FilteringDataByColumn**
10. To close the application, press Enter.
11. In Visual Studio, on the **File** menu, click **Close Solution**.

### Querying Data by Using Anonymous Types

#### Preparation Steps

Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.

#### Steps

1. Open **Visual Studio**.
2. In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.
3. In the **Open Project** dialog box, browse to the **[Repository Root]\Labs\DataLab\Demo4\FourthCoffee.Employees** folder, click **FourthCoffee.Employees.sln**, and then click **Open**.
    >**Note :** If any Security warning dialog box appears, clear **Ask me for every project in this solution** check box and then click **OK**.
4. In **Solution Explorer**, expand **FourthCoffee.Employees**, and then double-click **Program.cs**.
5. Review the LINQ code in each of the methods.
6. On the **Build** menu, click **Build Solution**.
7. On the **Debug** menu, click **Start Without Debugging**.
8. In the console window, review the output of the **UsingAnonymousTypes** method, and then press Enter.
9. Repeat step 8 for each of the following methods:
   - **GroupingData**
   - **AggregatingData**
   - **NavigatingData**
10. To close the application, press Enter.
11. In Visual Studio, on the **File** menu, click **Close Solution**.