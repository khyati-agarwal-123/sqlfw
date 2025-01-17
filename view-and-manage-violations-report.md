##  View and Manage Violations Report {#GUID-530B9F4B-5271-4A6A-B1C6-ECC6465896F5} 

Describes actions that can be take on reports and how to create custom reports. 

###  Modifying Columns in a Violations Report {#GUID-73C8D961-FC7F-423D-B58D-AC6D95BF3A27} 

To add or remove columns in the report, do the following: 

  1. View a predefined or custom violations report. 
  2. Click on the  Actions  drop down menu. 
  3. Click  Manage columns  . 

The Manage columns window is displayed. 

  4. Select columns that you want displayed in the report. 
  5. Deselect columns that you want to hide in the report. 
  6. Click  Save changes  . 



###  Basic Filtering in a Violations Report {#GUID-BFAADD72-F1C1-4F51-9B39-9327E156607D} 

To apply basic filters in the report, do the following: 

  1. View a custom or predefined violations report. 
  2. Click  Another filter  . 
  3. Select a filter type, operator, and enter a value. All columns that are available in the 

report are available as filter types. 

  4. Click  Apply  . 
  5. Repeat steps two through four to apply additional filters. 



To remove a filter, click the X beside the filter row. 

To filter the report based on a total category (for example, Violations blocked), click the total. The list of violations in the table at the bottom of the report is automatically updated. To remove the filter, click the total again. 

> **note:** Only some totals in your report are single-click filters. 

###  Advanced Filtering in a Violations Report {#GUID-A8807F24-1BF3-4DAB-9A00-1E3DD9BD7200} 

Advanced filtering of violations can provide flexibility in the way that data is analyzed and reviewed, by allowing organizations to specify complex conditions and multiple criteria that must be met in order for data to be included or excluded from the analysis. 

To apply advanced filters in the report, do the following: 

  1. View a predefined or custom violations report. 
  2. Click  Show Advanced SCIM Query Builder  . 
  3. Use the provided filter builder and dropdowns to type in your filter(s). Advanced filtering uses System for Cross-Domain Identity Management (SCIM) syntax and supported operators include: 
     * ` co ` : matches resources with an attribute that contains a given string 
     * ` eq ` : matches resources with an attribute that is equal to a given value (not case sensitive) 
     * ` eq_cs ` : matches resources with an attribute that is equal to a given value (case sensitive) 
     * ` ew ` : matches resources with an attribute that ends with a given string 
     * ` ge ` : matches resources with an attribute that is greater than or equal to a given value 
     * ` gt ` : matches resources with an attribute that is greater than a given value 
     * ` in ` : matches resources with an attribute that is equal to any of given values in list 
     * ` le ` : matches resources with an attribute that is less than or equal to a given value 
     * ` lt ` : matches resources with an attribute that is less than a given value 
     * ` ne ` : matches resources with an attribute that is not equal to a given value 
     * ` not_in ` : matches resources with an attribute that is not equal to any of given values in list 
     * ` pr ` : matches resources with an attribute if it has a given value 
     * ` sw ` : matches resources with an attribute that starts with a given string 

Operators can be grouped using parentheses to specify the order. 

Filters can also be combined using logical operators such as ` and ` and ` or ` . 

> **note:** If you have any basic filters currently applied they will appear in the query builder as well. 

  4. Click  Apply  . 



To clear the query builder, click  Clear  . This will clear any basic filters applied as well. 

Example 2-1 Context violations and SQL violations that are allowed advanced filter 
    
    
```
(violationAction eq "ALLOWED")  and ((violationCause eq "context violation") or (violationCause  eq "SQL violation"))
```

Example 2-2 SQL violations on a specific target database advanced filter 
    
    
```
(targetName eq "HRApps") and (violationCause eq "SQL violation")
```

Example 2-3 Actions taken on two specific databases since a specifc time advanced filter 
    

```
(operationTime ge "2023-09-11T00:39:43.295Z") and ((targetName eq "HRApps") or (targetName eq "TF_AUTOMATION"))
```

###  Tips for Using the Filter Builder to Create Advanced Filters {#GUID-92279D98-D764-48E0-9E3E-7CD78BD345AC} 

  * Pressing the escape key while in advanced filtering mode will clear the whole query. 
  * Pressing the space key will display the drop down with the list of available attributes or operators. 
  * Pressing the space key after entering a value like ` targetname (demo_tgt) ` will enclose the string with quotes: ` ("demo_tgt") ` . 
  * Pressing enter will close the drop down listing the operators and attribute names. 
  * If a value like SQL Firewall policy name has spaces in it, typing space will enclose the first word within quotes, ` "policy name" ` . You will have to move the cursor back to the enclosed string and continue typing the rest of the string value. 
  * If you build a filter in advanced filtering that can't be displayed in basic filters, you can't switch back to basic filtering mode. For example, advanced filters with the or condition can't be displayed in basic filtering. 
  * A custom report with basic filter can be updated with advanced filter and saved. 



For more information about SCIM, see the protocol documentation at [ https://www.rfceditor.org/rfc/rfc7644 ](https://www.rfceditor.org/rfc/rfc7644) . 

For more information about filtering in SCIM, see the filtering section of the protocol documentation at [ https://www.rfc-editor.org/rfc/rfc7644#section-3.4.2.2 ](https://www.rfc-editor.org/rfc/rfc7644#section-3.4.2.2) . 

###  Create a Custom Violations Report {#GUID-D3DFE198-6B82-4BA4-84EA-5D3FF22A36E0} 

You can create a custom report from any violations report, including the predefined AllViolations report. The details saved to the custom reports are those that you are currentlyviewing on screen. You may want to create a custom report if you want to preserve thefilters and columns displayed in a report that you are viewing online. You may alsowant to store your custom reports in specific compartments. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. Under  Related resources  , click  Violation reports  . 
  3. Click a report name and modify it as needed. If there aren't any custom reports saved, click the All violations report and make changes to it. 
  4. Click  Create custom report  . 

The Create custom report dialog box is displayed. 

  5. Enter a name for your custom report. 
  6. (Optional) Enter a description for your custom report. 
  7. Select the compartment to where you want to save your custom report. 
  8. Click  Create custom report  , and wait for a message that tells you the custom report is created. 
  9. (Optional) To open and view your custom report, click the  click here  link. 
  10. (Optional) To return to the report displayed on the screen, click  Close  . 



###  Update a Custom Violations Report {#GUID-E867651A-A286-4D44-A8B2-FE1939A7AD45} 

  1. Under  Security center  , click  SQL Firewall  . 
  2. Under  Related resources  , click  Violation reports  . 
  3. Click  Custom reports  tab. 
  4. Click a custom report name. 
  5. Modify the report as needed. 
  6. Click  Save Report  . 

The custom report is updated. 




###  Delete a Custom Violations Report {#GUID-D1E2594B-BB41-4231-A781-08B4FEAA6CA9} 

When you delete a custom violations report, the report is permanently deleted and cannot berecovered. You cannot delete the predefined All violations report. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. Under  Related resources  , click  Violation reports  . 
  3. Click  Custom reports  tab. 
  4. Click a custom report name. 
  5. Click  Delete report  . 

A Delete report dialog box is displayed, asking you to confirm the deletion. 

  6. Click  Delete report  . 



###  Create or Manage a Schedule for a Violations Report {#GUID-F5C979F8-1FC5-4403-B61A-F1944BE0B7E0} 

You can create a schedule for a predefined or custom violation report to generate a PDF or XLS report. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. Under  Related resource  , click  Violation reports  . 

The  Violation reports  page is displayed, showing you a list of violation reports. 

  3. To view a predefined violation report, on the  Predefined reports  tab, in the  Report name  column, click the report name that you want to view. 

The predefined report is displayed. 

  4. To view a custom violation report, click the  Custom report  tab. In the  Report name  column, click the name of your custom report. 

Your custom report is displayed. 

  5. Click  Manage report schedule  . 

The  Manage report schedule  panel is displayed, pre-loaded with either the default or modified schedule. 

  6. (Optional) In the  Schedule report name  box, enter a name for the PDF or XLS report. 
  7. Select a compartment to store the reports generated by the schedule. 
  8. For  Report format  , select either a  PDF  or  XLS  output. 
  9. Select a  Schedule frequency  . 
     * If you select weekly, select the day of the week in the  Every  field. 
     * If you select monthly, select the day of the month in the  Day  field. 
  10. In  Time (in UTC)  , select a schedule time. 
  11. In  Events time span  , select the time span for the violation records. 

For example, selecting Last months and entering 14 pulls violations from the last 14 months from the time the report is run. 

  12. (Optional) Specify a row limit. If unspecified, the default row limit is 200 rows. 
  13. Click  Save Schedule  . 

You can access the generated PDF/XLS reports on the  Violation report history  page. 




###  View and Manage Violation Report History {#GUID-E2234E5D-BE7B-4016-8AB6-0D42872A839A} 

The  Violation report history  page lists all the PDF/XLS violations reports that are automatically generated via a schedule or on-demand by users. On this page, you can view the list of reports generated during the past three months, details about those reports, and download reports. Oracle Data Safe stores these reports for up to three months. 

  1. Under  Security center  , click  SQL Firewall  . 
  2. Under  Related resources  , click  Violation report history  . 

The Violation report history table is displayed. It contains the following information: 

     * Name  \- The name of the violation report 
     * State  \- Either  Active  or  Updating  , shows if the report is currently accessible or if it is being updated 
     * Report definition  \- Specifies the name of the report that provides data for this scheduled or generated report 
     * Generated time  \- The time the report was created 
     * Report type  \- Generated or Scheduled. Where generated reports are on-demand reports produced outside of the scheduling system and scheduled reports are those produced by the scheduling system 
     * File format  \- PDF or XLS 
     * Download report  \- Option to download the report 
  3. (Optional) Under  Filters  , narrow down the report history page based on the  Report definition  ,  Report type  ,  File format  , and  Time period  . 
  4. Click on any report name to see further details including OCID and compartment information. 


