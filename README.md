# GAReport
Example creating a simple pdf report with DynaPDFMBS and Xojo

For my projects i otfen need a list report of my data in the databse. DynaPDF has lots of functions and is relativley easy to use. I created this simple module with two classes, a report class and a settings class. In the example app you can see what is needed to crate a list report:

    Var myGReport As GAReport.GReport = New GAReport.GReport

    myGReport.Settings.ReportDBFile = App.dbfile
    myGReport.Settings.ReportSQL = "SELECT FirstName, LastName, Address, City, Email, LastContact FROM Customers ORDER BY LastName;"     
    myGReport.Settings.ColumnTitles = "Firstname,LastName,Address,City,EMail,LastContact"
    myGReport.Settings.ColumnWidths = "60,60,110,70,180,60"
    myGReport.Settings.DateColumn = 5
    myGReport.Settings.ReportTitle = "GA-Report Test"
    
    myGReport.MakeReport("GARTest.pdf", True, HTMLViewer1)

The class needs a db, a corresponding string with a sql statement, strings with columntitles and widths. Optional you can determine a column where a SQLDate is found, the GetData()-routine converts this to a locale date to display. There a few more settings in the class, maybe you don't need a footer, then FT_ON can be set to false. Per default the report is saved on the desktop, change this in GReport.Init().

The example app uses eddieselectronics.sqlite. The report is displayed in a DesktopHTMLViewer if you want, if not delete the parameter HViewer and it is displayed in the system viewer as long as ShowIt is true.


