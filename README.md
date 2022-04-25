# Theatre-CMS-Summary

## Introduction
For my final Live Project with The Tech Academy, I worked on an interactive website for managing the content and productions for a theatre company. The website was built using ASP.NET MVC and the Entity Framework. The project was ran with Daily Standups and code retrospective meeting each Friday. The website is meant to be a content management service for users that aren't tech savvy and would like to easily manage what is displaying on their website. The portion I worked on was creating an entity model so that the cast members can be saved to the database. One challenge I came across and overcame was adding the ability for the user to upload an image, save it in the database, and display in the table.

## CRUD Functionality
Using Entity Framework, I scaffolded the CRUD pages for the model. Users are able to fill out a form to save the information of a cast member. The members are displayed on a table on the Index page.

### Create
Cast members are created and saved using the form in the Create page. Users have the ability to upload an image along with the form. This function is the beginning of the form and has the first input field. The form was styled with a combination of Bootstrap and CSS.

```
@using (Html.BeginForm("Create","TheatreMembers", FormMethod.Post, new { enctype = "multipart/form-data" })) 
{
    @Html.AntiForgeryToken()
<div class="form-horizontal TheatreMember-Create--FormContainer">
    <h2 class="TheatreMember-Create--FormTitle">Create Theatre Member</h2>
    <hr />
    @Html.ValidationSummary(true, "", new { @class = "text-danger" })
    <div class="form-group">
        @Html.LabelFor(model => model.Name, htmlAttributes: new { @class = "control-label col-md-2" })
        <div class="col-md-12">
            @Html.EditorFor(model => model.Name, new { htmlAttributes = new { @class = "form-control TheatreMember-Create--InputField", placeholder = "Enter your name" } })
            @Html.ValidationMessageFor(model => model.Name, "", new { @class = "text-danger" })
        </div>
    </div>
```
![Input Form](https://github.com/Borregito22/Theatre-CMS-Summary/blob/main/Screenshots/181149.png?raw=true)
![Input Form](https://github.com/Borregito22/Theatre-CMS-Summary/blob/main/Screenshots/181319.png?raw=true)

### Read
The table that displays the cast members has matching headers to the form. I also added a column that displays the image that was saved for the cast member.

```
<table class="table">
    <tr>
        <th>
            @Html.DisplayNameFor(model => model.Name)
        </th>
```
```
@foreach (var item in Model)
    {
        <tr>
            <td>
                @Html.DisplayFor(modelItem => item.Name)
            </td>
            <td>
                <img src="data:image/jpg;base64,@Convert.ToBase64String(item.Photo)" height="100px" width="100px" />
            </td>
```

![Input Form](https://github.com/Borregito22/Theatre-CMS-Summary/blob/main/Screenshots/181533.png?raw=true)

### Update and Delete
 The last column of the table gives the ability for the user to edit, delete, or view the details of each item. If a user decides to delete an entry from the table, they will be directed to a new page to confirm deletion.

 ![Input Form](https://github.com/Borregito22/Theatre-CMS-Summary/blob/main/Screenshots/184648.png?raw=true)

## Skills Acquired
* Working within Visual Studio
* Learned how to work with the Entity Framework and ASP.NET
* Utilizing Razor
* Working on a website that utilizes MVC
* Learning about and using BinaryReader to convert an image to bytes
* Using SQL Server Object Explorer to make sure the table was built correctly in the database