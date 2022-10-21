# Creating Reusable Types and Assemblies

## Examining Object Metadata

#### Preparation Steps

Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.

#### Steps

1. Open **Visual Studio**.
2. In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.
3. In the **Open Project** dialog box, browse to the **[Repository Root]\Labs\ReflectionLab\Starter\FourthCoffee.TypeInspector** folder, click **FourthCoffee.TypeInspector.sln**, and then click **Open**.
    > **Note:** If any Security warning dialog box appears, clear **Ask me for every project in this solution** check box and then click **OK**.
4. In Visual Studio, on the **View** menu, click **Task List**.
5. In the **Task List** window, double-click the **TODO: 01: Bring the System.Reflection namespace into scope** task.
6. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    using System.Reflection;
    ```
7. In the **Task List** window, double-click the **TODO: 02: Create an Assembly object** task.
8. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    return Assembly.ReflectionOnlyLoadFrom(path);
    ```
9. In the **Task List** window, double-click the **TODO: 03: Get all the types from the current assembly** task.
10. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    return assembly.GetTypes();
    ```
11. In the **Task List** window, double-click the **TODO: 04: Get a specific type from the current assembly** task.
12. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    return assembly.GetType(typeName);
    ```
13. In the code editor, locate the **RenderMethods** method, and then review the use of the **IsPublic**, **IsStatic**, **ReturnType**, and **Name** properties of the **MethodInfo** class.
14. Locate the **RenderProperties** method, and then review the use of the **DeclaringType** and **Name** properties of the **PropertyInfo** class.
15. On the **Build** menu, click **Build Solution**.
16. On the **Debug** menu, click **Start Without Debugging**.
17. In the **Fourth Coffee Type Inspector** application, click **Load Assembly**.
18. In the **Open** dialog box, browse to the **[Repository Root]\Labs\ReflectionLab\Starter\FourthCoffee.TypeInspector\FourthCoffee.Core\bin\Debug** folder, click **FourthCoffee.Core.dll**, and then click **Open**. The **Types** list now contains a list of all of the types that the assembly exposes.
19. In the **Types** list, click **FourthCoffee.Core.Encryptor**, and then click **Inspect Type**. The **Members** list now shows all of the methods that the type exposes.
20. Close **Fourth Coffee Type Inspector**.
21. In Visual Studio, close the solution.

## Creating and Using Custom Attributes

#### Preparation Steps

Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.

#### Steps

1. Open **Visual Studio**.
2. In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.
3. In the **Open Project** dialog box, browse to the **[Repository Root]\Labs\ReflectionLab\Starter\FourthCoffee.MetadataExtractor** folder, click **FourthCoffee.MetadataExtractor.sln**, and then click **Open**.
    > **Note:** If any Security warning dialog box appears, clear **Ask me for every project in this solution** check box and then click **OK**.
4. In Visual Studio, on the **View** menu, click **Task List**.
5. In the **Task List** window, double-click the **TODO: 01: Invoke the Type.GetCustomAttribute method** task.
6. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    var typeAttribute = type.GetCustomAttribute<DeveloperInfo>(false);
    ```
7. In the **Task List** window, double-click the **TODO: 02: Invoke the MemberInfo.GetCustomAttribute method** task.
8. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    var memberAttribute = member.GetCustomAttribute<DeveloperInfo>(false);
    ```
9. On the **Build** menu, click **Build Solution**.
10. On the **Debug** menu, click **Start Without Debugging**.
11. In the **Fourth Coffee Metadata Extractor** application, click **Load**. The list box now contains a list of all of the members in the **Encryptor** type and the details from any **DeveloperInfo** attributes that were found.
12. Close **Fourth Coffee Metadata Extractor**.
13. In Visual Studio, close the solution.

## Versioning, Signing, and Deploying Assemblies

#### Preparation Steps

Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.

#### Steps

1. Open **Visual Studio**.
2. In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.
3. In the **Open Project** dialog box, browse to the **[Repository Root]\AllFiles\\Mod12\Democode\Starter\FourthCoffee.Core** folder, click **FourthCoffee.Core.sln**, and then click **Open**.
    > **Note:** If any Security warning dialog box appears, clear **Ask me for every project in this solution** check box and then click **OK**.
4. Open **Windows Menu** and type **Developer Command Prompt for VS**, right click on the app
    then select **Run as adiministrator**.
5. Paste the following command and then press **Enter**:
    ```cs
    cd [Repository Root]\Labs\ReflectionLab\Starter\FourthCoffee.Core\FourthCoffee.Core
    ```
6. Paste the following command and then press **Enter**:
    ```cs
    generateKeyFile.cmd
    ```
7. Switch to Visual Studio.
8. In **Solution Explorer**, right-click **FourthCoffee.Core**, and then click **Properties**.
9. On the **Signing** tab, select **Sign the assembly**.
10. In the **Choose a strong name key file** list, click **Browse**.
11. In the **Select File** dialog box, click **FourthCoffeeKeyFile.snk**, and then click **Open**.
12. On the **Build** menu, click **Build Solution**.
13. Switch to File Explorer.
14. In the **[Repository Root]\Labs\ReflectionLab\Starter\FourthCoffee.Core\FourthCoffee.Core** folder, right-click the **installAssemblyInGac.cmd** file, and then click **Edit**.
    > **Note :** If a Windows protected your PC dialog appears, click **More info** and then click **Run Anyway**.
15. In Notepad, view the **Gacutil** command.
16. Close Notepad, and then close File Explorer.
17. Switch back to **Developer Command Prompt for VS** and then run the **installAssemblyInGac** command. Verify that the command completes successfully.
18. Run the **verifyGacInstall** command, and then ensure that the number of items found equals one.
19. Close the **Administrator: Developer Command Prompt for VS** window.
20. In Visual Studio, close the solution.