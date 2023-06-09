---
title: "CampaignSort"
subtitle: "Sort and display marketing campaign data with this console application"
date: 2023-05-30 00:00:00
description: A console application built using C# and .NET 6.0 that allows users to sort and display marketing campaign data based on various attributes. This application demonstrates the use of TDD, OOP, SOLID principles, MVC architecture, and clean code principles.
featured_image: "/images/demo/CampaignSort/CampaignSortProjectPage.jpg"
permalink: "project/CampaignSort/"

---

## Table of Contents

1. [Project Description](#project-description)
2. [Getting Started](#getting-started)
3. [Usage](#usage)
4. [Testing](#testing)
4. [Development](#development)
    - [Adding a new attribute](#adding-a-new-attribute)
    - [Adding a new campaign](#adding-a-new-campaign)
5. [Technology Stack](#technology-stack)
6. [Code Examples](#code-examples)
7. [Contributions](#contributions)
8. [License](#license)
9. [Contact Information](#contact-information)

## Project Description

CampaignSort is a console-based application developed in C#. It enables the users to sort and display selected marketing campaign data based on various attributes. This application can be used for quick campaign comparisons and to get insights into campaign performance metrics. The application is structured using the MVC (Model-View-Controller) architectural pattern. This ensures separation of concerns, where Models manage the application data, Views handle the user interface and presentation, and Controllers act as intermediaries, handling the communication between Models and Views. The goals of this project were to display my knowledge and use of TDD, OOP, SOLID, MVC, and clean code principles.

## Getting Started

### Prerequisites

- .NET 6.0
- NUnit

### Installation

1. Visit my github repository [here](https://github.com/jonahpena/CampaignSort.git) and clone the repository to a folder of your choice on your machine:
```sh
git clone https://github.com/jonahpena/CampaignSort.git
```
2. Navigate to the project directory:
```sh
cd CampaignSort/CampaignSort/CampaignSort
```
3. Build the project:
```sh
dotnet build
```
4. Run the project:
```sh
dotnet run
```

## Usage

Upon running the application, it will initially display a list of marketing campaigns. Input the number(s) of the campaigns you're interested in, separated by commas, or input 'all' to select all campaigns. 

Following, it will present a list of attributes. You'll be asked to select an attribute to sort by, and then to choose additional attributes for display.

Once your selections have been made, the application will display your selected campaigns, sorted by the chosen attribute, and listing the attributes you selected.

## Testing

This project uses NUnit for testing. To run the tests, navigate to the test project directory and use the following command:

```sh
dotnet test
```

## Development

### Understanding the Project Structure

The application follows the Model-View-Controller (MVC) pattern.

- Models: This directory contains classes that represent the data of the app. The main data class in our application is the `Campaign` class.
- Views: This includes classes responsible for the user interface (console output in our case). `IUserInputInterface` and its implementations are part of this.
- Controllers: These are classes that handle user input, manipulate the model, and cause the view to update. `CampaignSorter` can be seen as a part of this component.

These components work together to provide a well-structured and scalable architecture for the application.

These components work together to provide a well-structured and scalable architecture for the application.

### Adding a new attribute
To add a new attribute to the Campaign class, you need to:

1. Add the new property to the Campaign class.
2. Implement a new comparer in the `Controller/Comparers` directory, ensuring it complies with the `ICampaignComparer` interface.
3. Modify the `CampaignComparerFactory` to return your new comparer when necessary.
4. Update the Main function in `Program.cs` to include the new attribute in the attributes list.


### Adding a new campaign

Adding a new campaign is straightforward. Simply create a new instance of the Campaign class with the necessary attributes in the `Main` method of the `Program.cs` file. 

## Technology Stack

1. .NET 6.0: A free, cross-platform, open-source developer platform for building many different types of applications.
2. C#: A modern, object-oriented programming language developed by Microsoft.
3. MVC: An architectural design pattern that separates an application into three main logical components: the Model, the View, and the Controller. This pattern helps to achieve separation of concerns.
4. NUnit: A unit-testing framework for all .Net languages.

## Code Examples

#### Usage of Interfaces (IUserInputInterface and ICampaignComparer):
This allows us to define a contract for related classes and increases the flexibility of our application. It aligns with the Dependency Inversion Principle (D) of SOLID principles.

```csharp
public interface ICampaignComparer
{
    int Compare(Campaign x, Campaign y);
}
```

#### Usage of Factory Pattern (CampaignComparerFactory):
This creates and returns instances of classes that implement the ICampaignComparer interface. It allows our application to decide at runtime which class to use, promoting the Open/Closed Principle (O) of SOLID principles.

```csharp
public class CampaignComparerFactory
{
    public ICampaignComparer GetCampaignComparer(string attribute)
    {
        switch (attribute)
        {
            case "Name":
                return new CampaignNameComparer();
            case "StartDate":
                return new CampaignStartDateComparer();
            // Add other cases for each attribute as necessary
        }
    }
}
```
#### Usage of Reflection: 
This is used in our application to dynamically read and display property values of the Campaign class. It enables our application to be flexible and adaptive to changes in the class structure.

```csharp
foreach (var campaign in campaigns)
{
    foreach (var attribute in attributeSelection)
    {
        PropertyInfo propertyInfo = typeof(Campaign).GetProperty(attribute);
        Console.WriteLine($"{attribute}: {propertyInfo.GetValue(campaign)}");
    }
    Console.WriteLine("--------------------");  // Separator between campaigns
}
```

## Contributions

Contributions are what make the open-source community such an incredible place to learn, inspire, and create. Any contributions you make are greatly appreciated.

1. Fork the Project
2. Create your Feature Branch (git checkout -b feature/AmazingFeature)
3. Commit your Changes (git commit -m 'Add some AmazingFeature')
4. Push to the Branch (git push origin feature/AmazingFeature)
5. Open a Pull Request

Please make sure to update tests as appropriate. Also, ensure your code adheres to the existing coding standards within the project to make the integration process smoother.

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Contact Information
If you have any questions, concerns, or would like to collaborate on this project, please feel free to reach out:

- Email: jonahrpena@gmail.com
- LinkedIn: Jonah Pena
