

# Party invitation
___


### Description
___
This project will use the basic  ***MVC***  functionality by building a simple data entry application. The goal is to demonstrate the ***MVC*** framework in action.
When you create an ASP.NET project, the ***Visual Studio*** environment provides several options for the initial content that the project requires. The idea is to simplify the process and apply recommended practices for common tools and tasks. This support is provided through templates used to create controllers and views, which are created using boilerplate code to render lists of data objects, edit model properties, and more.
___
<img src="https://github.com/Allseeingeye99/PartyInvites/blob/master/20.gif" width="500" height="300">

### Technologies
___
- ASP.NET MVC 5
- JavaScript
- JQuery
- Bootstrap

### Presetting
___
Use of four fixed assets:

- Home page displaying information about the party;

- A form that can be used to respond to an invitation (***repondez s'il vous plait - RSVP***);

- Validation for the ***RSVP*** form, which will display a thank you page;

- Tool for sending forms ***RSVP*** by email to the party organizer.
### Installation
___
NuGet [link](https://www.nuget.org/)

### Styling the RsvpForm View
____
The Bootstrap library defines classes that can be used to style forms.
The Bootstrap classes in this example create a header bar to give the layout structure. To style the form, use the form-group class, which styles the element that contains the label and the associated input or select element.
The following shows how these classes were applied:

    @model PartyInvites.Models.GuestResponse

    @{
    Layout = null;
    }

    <!DOCTYPE html>

    <html>
    <head>
        <meta name="viewport" content="width=device-width" />
        <title>RsvpForm</title>
        <link rel="stylesheet" type="text/css" href="~/Content/Styles.css" />
        <link href="~/Content/bootstrap.css" rel="stylesheet" />
        <link href="~/Content/bootstrap-theme.css" rel="stylesheet" />
    </head>
    <body>
    <div class="panel-success">
        <div class="panel-heading text-center">
            <h4>Form RSVP</h4>
        </div>
        <div class="panel-body">
            @using (Html.BeginForm())
            {
                @Html.ValidationSummary()
                <div class="form-group">
                    <label>Your name:</label>
                    @Html.TextBoxFor(x => x.Name, new { @class = "form-control" })
                </div>
                <div class="form-group">
                    <label>Your email:</label>
                    @Html.TextBoxFor(x => x.Email, new { @class = "form-control" })
                </div>
                <div class="form-group">
                    <label>Your phone number:</label>
                    @Html.TextBoxFor(x => x.Phone, new { @class = "form-control" })
                </div>
                <div class="form-group">
                    <label>Will you come?</label>
                        @Html.DropDownListFor(x => x.WillAttend, new[] {
                            new SelectListItem() { Text = "Yes of course I will", Value = Boolean.TrueString},
                            new SelectListItem() { Text = "No i can't come", Value = Boolean.FalseString}
                        }, "Select option", new { @class = "form-control" })
                </div>
                <div class="text-center">
                    <input type="submit" value="Submit Form RSVP" class="btn btn-success" />
                </div>
            }
        </div>
    </div>
    </body>
    </html>

___
