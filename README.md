![license](https://img.shields.io/badge/license-Mit-green?style=plastic)
![build](https://img.shields.io/badge/build-passing-1CB265?style=plastic&logo=appveyor)
![GitHub](https://img.shields.io/badge/.Net-passing-318CE7?style=plastic&logo=github)
![Bootstrap](https://img.shields.io/badge/Bootstrap-3.4.1-9457EB?style=plastic&logo=Bootstrap)



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
___
### Adding a validation check
In an ***MVC*** application, validation is typically applied in the domain model, not in the user interface. This means that you can define in one place the desired validation criteria that come into play wherever the model class is used.
using System.ComponentModel.DataAnnotations;
The ***ASP.NET MVC*** framework supports declarative validation rules defined using attributes from the ***System.ComponentModel***.***DataAnnotations namespace***, which means that validation constraints are expressed using standard ***C #*** attributes. The example below shows how to apply these attributes to the ***GuestResponse*** model class:

       using System.ComponentModel.DataAnnotations;
       namespace PartyInvites.Models
       {
         public class GuestResponse
        {
           [Required(ErrorMessage="Пожалуйста, введите свое имя")]
           public string Name { get; set; }

           [Required(ErrorMessage="Пожалуйста, введите email")]
           [RegularExpression(".+\\@.+\\..+", ErrorMessage="Вы ввели некорректный email")]
            public string Email { get; set; }

           [Required(ErrorMessage = "Пожалуйста, введите телефон")]
            public string Phone { get; set; }

           Required(ErrorMessage = "Пожалуйста, укажите, примите ли участие в вечеринке")]
            public bool? WillAttend { get; set; }
         }
       }



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

The Install-Package command tells NuGet to download the package along with its dependencies and then add it all to the project. The package you need is called bootstrap. Package names can either be searched on the NuGet website (http://www.nuget.org) or you can use the NuGet UI services in Visual Studio (select Tools -> Library Package Manager -> Manage NuGet Packages for Solution.

### Styling the RsvpForm View
____
The Bootstrap library defines classes that can be used to style forms.
The Bootstrap classes in this example create a header bar to give the layout structure. To style the form, use the form-group class, which styles the element that contains the label and the associated input or select element.
The following shows how these classes were applied:

 ### Sending RSVP responses by email to the party organizer
 This could be accomplished by adding an action method to create and send a message using the email classes available in the ***.NET Framework*** — an approach that aligns best with the ***MVC*** pattern.

However, we intend to use the ***WebMail*** helper class instead. It is not part of the ***MVC framework***, but it allows you to complete the example without going into the nuances of configuring the means for sending email. We want the email to be sent when rendering the ***Thanks*** view. The required changes are shown in the example below:
   

            WebMail.Send("myemail@example.com", "RSVP Приглашение",
                Model.Name + ((Model.WillAttend ?? false) ? " " : "не") + "придет");

            }
        catch (Exception)
           {
            @:<b>К сожалению при отправке письма возникла ошибка.</b>
        }
    }
    <div class="text-center">
        <h1>Спасибо, @Model.Name!</h1>
        <div class="lead">
            @if (Model.WillAttend == true)
            {
                @:Здорово что вы придете, напитки уже в холодильнике ;)
            }
            else
            {
                @:Жаль что вы не придете, но спасибо что дали об этом знать.
            }
___

         
         
The ***WebMail*** helper class was used because it allows you to demonstrate how to send an email with minimal effort. However, it is usually preferable to put this functionality in an action method.

We've added a ***Razor*** expression that uses the ***WebMail*** helper class to configure our mail server settings, including the server name, required secure connections ***(SSL)***, and account information. Once all of these details are configured, an email is sent using the ***WebMail.Send ()*** method.
