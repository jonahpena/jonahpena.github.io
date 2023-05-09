---
title: "Together Everyone Kodes"
subtitle: "Shop computer science courses from Together Everyone Kodes (T-E-K)"
date: 2023-04-26 00:00:00
description: eCommerce Website Built with React.js, Java, SpringBoot, and MySQL
featured_image: "/images/demo/TEK/.jpg"
---

![](/images/demo/TEK/TEKfrontpageMockUp.jpg)

## Table of Contents

1. [Project Description](#project-description)
2. [Technologies and Libraries](#technologies-and-libraries)
3. [Features](#features)
4. [Usage](#usage)
5. [Code Examples](#code-examples)
6. [License](#license)
7. [Contact Information](#contact-information)
8. [Acknowledgments](#acknowledgments)

## Project Description

Together Everyone Kodes (TEK) is an eCommerce website that offers computer science courses. The project was developed to strengthen the author's understanding of React.js, Java, and related libraries. The application utilizes a combination of React concepts, such as state management and component lifecycle methods, as well as Java concepts like object-oriented programming and data manipulation.

### Key React concepts used in this project include:

##### Functional Components:

The application consists of several functional components that help to structure and organize the user interface. These components receive props from their parent components and render the appropriate UI elements accordingly.

##### React Hooks:

The useState and useEffect hooks are used to manage local component state and handle side effects. These hooks make it easier to manage state and perform side effects in functional components, rather than relying on class components and lifecycle methods.

#### React Router:

This library is used to handle client-side navigation within the application. React Router enables the creation of a single-page application, allowing users to navigate between different pages without reloading the entire page.

#### Material-UI:

A popular React UI framework is employed to style the application and create a responsive and visually appealing design.

### Key Java concepts used in this project include:

#### Object-Oriented Programming (OOP):

The backend of the application is built using Java, which is an object-oriented programming language. The OOP paradigm enables the creation of modular and reusable code by organizing related data and functions into classes and objects.

#### Data Manipulation:

The backend of the application is responsible for handling the data associated with courses, such as course information, user details, and shopping cart contents. Java is used to perform various data manipulation tasks, including searching, sorting, and filtering.

#### API Endpoints:

The application's frontend communicates with the backend through a series of API endpoints. These endpoints allow the frontend to send and receive data from the backend, enabling the application to perform CRUD operations on the data.

#### Error Handling and Validation:

Java is used to handle errors and perform validation checks on the data being sent between the frontend and backend. This ensures that the application remains stable and secure, even when users input incorrect or unexpected data.

By incorporating these React and Java concepts, the TEK project demonstrates a strong understanding of both frontend and backend development, as well as the ability to create a fully functional and user-friendly eCommerce website.

## Technologies and Libraries

The project was built using the following technologies and libraries:

- React.js
- JavaScript
- Java
- SpringBoot
- Material-UI

## Features

This eCommerce website offers users the ability to:

- Browse a list of available computer science courses
- View detailed information about each course
- Add courses to the shopping cart
- Increase and decrease the quantity of courses in the cart

## Usage

Once the application is running, users can interact with the website through its web interface. Users can browse the available courses on the main page, click on individual courses to view detailed information, and add or remove courses from the shopping cart.

## Code Examples

Here are the updated code examples showcasing the usage of React Hooks and event handling in the frontend, as well as Java API endpoints and data manipulation in the backend.

### React Hooks and Event Handling

The following example demonstrates the usage of React Hooks and event handling in the ProductPageProduct component. This component manages the state for the quantity of a course to be added to the cart and handles the add to cart and minus from cart events.

```javascript
function ProductPageProduct({
  course,
  addToCart,
  cart,
  setCart,
  minusFromCart,
}) {
  const [quantity, setQuantity] = useState(1);

  const handleAddToCart = () => {
    addToCart(course, quantity);
    setQuantity(1);
  };

  const handleMinusFromCart = () => {
    minusFromCart(course);
    setQuantity(Math.max(1, quantity - 1));
  };

  return (
    <div className="productContainer">
      {/* Display course information */}
      <Typography variant="h5">{course.title}</Typography>
      <Typography variant="subtitle1">{`Price: $${course.price}`}</Typography>
      {/* Handle quantity change */}
      <Button onClick={() => setQuantity(Math.max(1, quantity - 1))}>-</Button>
      <Typography>{quantity}</Typography>
      <Button onClick={() => setQuantity(quantity + 1)}>+</Button>
      {/* Handle add to cart and minus from cart events */}
      <Button onClick={handleAddToCart}>Add to Cart</Button>
      <Button onClick={handleMinusFromCart}>Minus from Cart</Button>
    </div>
  );
}

export default ProductPageProduct;
```

### Java API Endpoints and Data Manipulation

This example demonstrates the usage of Java API endpoints and data manipulation in the backend. The CourseController class implements the endpoints for retrieving all courses and searching for courses by title.

```javascript
import java.util.List;
import java.util.stream.Collectors;

@RestController
@RequestMapping("/api/courses")
public class CourseController {

    @Autowired
    private CourseRepository courseRepository;

    // Get all courses
    @GetMapping
    public List<Course> getAllCourses() {
        return courseRepository.findAll();
    }

    // Search courses by title
    @GetMapping("/search/{title}")
    public List<Course> searchCoursesByTitle(@PathVariable String title) {
        List<Course> allCourses = courseRepository.findAll();
        return allCourses.stream()
                .filter(course -> course.getTitle().toLowerCase().contains(title.toLowerCase()))
                .collect(Collectors.toList());
    }
}
```

## License

This project is licensed under the MIT License. For more information, please see the [LICENSE](LICENSE) file.

## Contact Information

If you have any questions, concerns, or would like to collaborate on this project, please feel free to reach out:

- Email: jonahrpena@gmail.com
- LinkedIn: [Jonah Pena](https://www.linkedin.com/in/jonahpena/)

## Acknowledgments

(under construction)
