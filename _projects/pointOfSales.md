---
title: "Poke Palace"
subtitle: "A Simple Command-Line Poke Restaurant Ordering System"
date: 2023-04-28 00:00:00
description: A command-line application for a poke restaurant that allows users to create and manage orders, displaying various menu options, and calculating the order total including tax.
featured_image:
---

![](/images/demo/POS/POSSystem.jpg)

## Table of Contents

1. [Project Description](#project-description)
2. [Technologies and Libraries](#technologies-and-libraries)
3. [Features](#features)
4. [Usage](#usage)
5. [Code Examples](#code-examples)
6. [License](#license)
7. [Contact Information](#contact-information)

## Project Description

While working on the Poke Palace project, I deepened my understanding of various Java concepts and applied them effectively to build a well-structured application. Some of the key concepts I gained valuable experience in include:

##### Inheritance:

I leveraged inheritance to create a more modular design in the application. By extending the MenuBuilder class in the Menu class, I was able to inherit properties and methods from the parent class and add or override them as needed. This allowed for better code organization and easier maintenance.

##### Encapsulation:

To ensure a clean and safe design, I employed encapsulation to protect the internal states and operations of objects. For example, in the Orders class, I utilized private variables like entrees, sum, and orderNumber and provided public methods to access and modify these variables. This approach kept the internal state of objects secure and allowed for controlled manipulation through public methods.

##### Collections:

Throughout the project, I made use of Java's collections framework, specifically the List interface and ArrayList class, to store and manage groups of objects. For instance, in the SaveOrder class, I used a list to store orders, while in the Orders class, I employed a list to store MenuAddOns. The collections framework provided a convenient and flexible way to work with dynamic data structures.

##### Method overloading:

I applied method overloading to provide multiple ways of interacting with objects while maintaining a consistent interface. In the Orders class, I created overloaded versions of the addToEntrees and removeFromEntrees methods with different parameter lists. This allowed for more flexibility and improved code readability.

By incorporating these advanced Java concepts into the Poke Palace project, I was able to create a robust and efficient application that demonstrates my proficiency in the language and my ability to apply key programming principles effectively.

## Technologies and Libraries

The project was built using the following technologies:

- Java

## Features

Poke Palace offers a range of features to help users create and manage their orders:

- Display various menu options, including entrees, toppings, drinks, sides, and combo meals
- Add and remove items from the order
- Calculate the subtotal, tax, and total for each order
- Save the order history

## Usage

Follow the prompts to order any amount of food, drink, sides, and toppings that you desire. Once you've completed your order, feel free to add another. You may even view your previous orders by choosing to view receipts at the end of the ordering process.

## Code Examples

While working on the Poke Palace project, I deepened my understanding of various Java concepts and applied them effectively to build a well-structured application. Some of the key concepts I gained valuable experience in include:

#### Inheritance:

Demonstrating inheritance in the Total class, which extends the Display class.

```java
public class Total extends Display {
    @Override
    public void generate(Orders order) {
        double total = order.getSum() * (1 + TaxCalculator.calculateTax(order.getSum()));
        double roundedTotal = Math.round(total * 100.0) / 100.0;
        System.out.println("|          Total: $" + roundedTotal + "          |");
    }
}
```

#### Encapsulation:

Showcasing encapsulation in the MenuAddOns class.

```java
public class MenuAddOns {

    private String name;
    private double cost;

    public MenuAddOns(String name, double cost) {
        this.name = name;
        this.cost = cost;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getCost() {
        return cost;
    }

    public void setCost(double cost) {
        this.cost = cost;
    }
}
```

#### Collections:

Using collections in the Orders class.

```java
public class Orders {
    private List<MenuAddOns> entrees = new ArrayList<>();

    // Other methods and fields...

    public List<MenuAddOns> getEntrees() {
        return entrees;
    }

    public void setEntrees(List<MenuAddOns> entrees) {
        this.entrees = entrees;
    }
}
```

#### Method Overloading:

Demonstrating method overloading in the TaxCalculator class.

```java
public class TaxCalculator {
    private static final double DEFAULT_TAX_RATE = 0.07;

    public static double calculateTax(double amount) {
        return calculateTax(amount, DEFAULT_TAX_RATE);
    }

    public static double calculateTax(double amount, double taxRate) {
        return amount * taxRate;
    }
}
```

## License

This project is licensed under the MIT License. For more information, please see the [LICENSE](LICENSE) file.

## Contact Information

If you have any questions, concerns, or would like to collaborate on this project, please feel free to reach out:

- Email: jonahrpena@gmail.com
- LinkedIn: [Jonah Pena](https://www.linkedin.com/in/jonahpena/)
