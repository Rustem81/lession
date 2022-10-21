
# Improving Application Performance and Responsiveness

## Performing Operations Asynchronously

### Using the Task Parallel Library to Invoke APM Operations

#### Preparation Steps

1. Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.
2. Navigate to **[Repository Root]\Labs\MultitaskingLab\Starter\Starter**, and then open the **APMTasks.sln** file.
    > **Note:** If any Security warning dialog box appears, clear **Ask me for every project in this solution** check box and then click **OK**.

#### Steps

1. On the **Build** menu, click **Build Solution**.
2. On the **Debug** menu, click **Start Without Debugging**.
3. In the text box, type **http://www.fourthcoffee.com**, and then click **Check URL**.  
   Notice that the label displays the message **The URL returned the following status code: OK**.
4. Close the **MainWindow** window.
5. In **Solution Explorer**, expand **MainWindow.xaml**, and then double-click **MainWindow.xaml.cs**.
6. Review the code in the **MainWindow** class:
    - Notice that the **btnCheckUrl_Click** method creates an **HttpWebRequest** object and then calls the **BeginGetResponse** method.
    - Notice that the **BeginGetResponse** method specifies the **ResponseCallback** method as an asynchronous callback method.
    - Notice that the **ResponseCallback** method calls the **HttpWebResponse.EndGetResponse** method to get the result of the web request and then updates the UI.
7. Delete the **ResponseCallback** method.
8. Modify the **btnCheckUrl_Click** method declaration to include the **async** modifier as follows:
    ```cs
    private async void btnCheckUrl_Click(object sender, RoutedEventArgs e)
    ```
9. In the **btnCheckUrl_Click** method, delete the following line of code:
    ```cs
    request.BeginGetResponse(new AsyncCallback(ResponseCallback), request);
    ```
10. Add the following code in place of the line you just deleted:
    ```cs
    HttpWebResponse response = await Task<WebResponse>.Factory.FromAsync(request.BeginGetResponse, request.EndGetResponse, request) as HttpWebResponse;
    lblResult.Content = String.Format("The URL returned the following status code: {0}", response.StatusCode);
    ```
11. Notice that the **MainWindow** class is now far more simple and concise.
12. On the **Debug** menu, click **Start Without Debugging**.
13. In the text box, type **http://www.fourthcoffee.com**, and then click **Check URL**.
14. Notice that the label displays the message **The URL returned the following status code: OK**.
15. Notice that the application works in exactly the same way as before.
16. Close the **MainWindow** window, and then close Visual Studio.

## Synchronizing Concurrent Access to Data

### Using Lock Statements

#### Preparation Steps

1. Ensure that you have cloned the directory it contains the code segments for this course's labs and demos.
2. Navigate to **[Repository Root]\Labs\MultitaskingLab\Starter\Starter**, and then open the **Locking.sln** file.
    > **Note:** If any Security warning dialog box appears, clear **Ask me for every project in this solution** check box and then click **OK**.

#### Steps

1. In **Solution Explorer**, double-click **Coffee.cs**.
2. Review the **Coffee** class, paying particular attention to the **MakeCoffees** method.
3. Notice how the **MakeCoffees** method uses a **lock** statement to prevent concurrent access to the critical code.
4. In **Solution Explorer**, double-click **Program.cs**.
5. In the **Program** class, review the **Main** method.
6. Notice how the **Main** method uses a **Parallel.For** loop to simultaneously place 100 orders for between one and 100 coffees.
7. On the **Build** menu, click **Build Solution**.
8. On the **Debug** menu, click **Start Debugging**.
9. Review the console window output and notice that the application keeps track of stock levels effectively.
10. To close the console window, press Enter.
11. In the **Coffee** class, comment out the following line of code:
    ```cs
    lock (coffeeLock)
    ```
12. On the **Debug** menu, click **Start Debugging**.
13. Notice that the application throws an exception with the message **Stock cannot be negative!**
14. This is due to concurrent access to the critical code section in the **MakeCoffees** method.
15. On the **Debug** menu, click **Stop Debugging**.
16. Close Visual Studio.