
# Module: Integrating with Unmanaged Code

## Lesson: Creating and using Dynamic Objects

### Lab: Interoperation with Microsoft Word

#### Preparation Steps

1. Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.

2. Navigate to **[Repository Root]\Labs\InteropLab\Starter\FourthCoffee.ExceptionLogger**, and then open the **FourthCoffee.ExceptionLogger.sln** file.
    > **Note:** If any Security warning dialog box appears, clear **Ask me for every project in this solution** check box and then click **OK**.

#### Demonstration Steps

1. In **Solution Explorer**, right-click the **FourthCoffee.ExceptionLogger** project, and then click **Add** and then click **Reference**.
2. In the **Reference Manager – FourthCoffee.ExceptionLogger** dialog box, perform the following steps, and then click **OK**:
    - Expand **COM**, and then click **Type Libraries**.
    - In the **Search** text box, type **Word**.
    - In the assembly list, select **Microsoft Word [Version Number] Object Library**, and then select the **Microsoft Word [Version Number] Object Library** check box.
    > **Note :** [Version Number] can be greater than 14.
3. In Visual Studio, on the **View** menu, click **Task List**.
4. In the **Task List** window, double-click the **TODO: 01: Bring the Microsoft.Office.Interop.Word namespace into scope.** task.
5. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    using Microsoft.Office.Interop.Word;
    ```
6. Double-click the **TODO: 02: Declare a global object to encapsulate Microsoft Word** task.
7. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    dynamic _word;
    ```
8. Double-click the **TODO: 03: Instantiate the _word object** task.
9. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    this._word = new Application();
    ```
10. Double-click the **TODO: 04: Create a blank Word document** task.
11. In the code editor, click in the blank line below the comment, and then type the following code:
    ```cs
    this._word.Documents.Add().Activate();
    ```
12. In the code editor, look at the following helper methods that wrap the Word COM API:
    - The **GetEndOfDocument** method places the cursor at the end of the document. The **-1** converts the **End** property to a 0-based index value. Without the **-1**, the CLR will throw an **IndexOutOfRange** exception.
    - The **AppendText** method adds text to the end of the document, in the bold and/or italic style.
    - The **InsertCarriageReturn** method inserts a carriage return at the end of the document.
    - The **Save** method deletes any file with the same name and then saves the current Word document.
13. Double-click the **App.config** file inside the **FourthCoffee.ExceptionLogger** project and change the **[Repository Root]** to your repository destination.
14. On the **Build** menu, click **Build Solution**.
15. On the **Debug** menu, click **Start Without Debugging**.
16. In the **Exception Logger** application, click **Export**.
17. In the **Export Successful** dialog box, click **OK**.
18. Close the **Exception Logger** application.
19. Open File Explorer and browse to the **[Repository Root]\Labs\InteropLab\Data\Exceptions\Exceptions** folder.
20. Double-click **Exceptions.docx**, and then view the combined exception report in the Word document.
21. Close Microsoft Word.
22. Close File Explorer.
23. Close Visual Studio.