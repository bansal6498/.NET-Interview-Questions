#### What experience do you have with C# and .NET? Can you describe a project where you used them?
**Answer:**
"I have worked extensively with C# and .NET, including .NET Core, in developing various enterprise-level applications. In one project, I developed a web application using ASP.NET Core MVC, where I implemented complex business logic using C# and integrated it with an Oracledatabase. I also created APIs using Web API, ensuring they followed best practices for performance and security."
#### How do you implement security in .NET Core applications?
**Answer:**
Security can be implemented in .NET Core applications by using: • Authentication: Verify the identity of users via JWT tokens, cookie-based authentication, or third-party providers like OAuth. • Authorization: Use role-based or policy-based authorization to control access to application.
#### What is your experience with APIs, and how do you test them?
**Answer:**
"I have developed RESTful APIs using ASP.NET Core Web API, and I ensure they are welldocumented using tools like Swagger. I test APIs using Postman, where I write test cases to check for expected responses, status codes, and error handling. I also use unit tests to ensure API controllers function as expected."
#### Describe your experience with Agile methodologies and working in an onshore/offshore model.
**Answer:**
"I have worked in Agile environments, where we use Scrum or Kanban to manage sprints and tasks. In the onshore/offshore model, I have collaborated with both onshore teams and offshore developers. We used tools like JIRA for tracking progress, and I was involved in daily standups, sprint planning, and code reviews to ensure alignment between teams."
### String vs StringBuilder

String: String is an immutable sequence of characters. When you modify a String, a new instance is created, and the original instance remains unchanged.
#### 🧩 Example
Since `String` is immutable, repeated concatenations can be inefficient, especially in loops.
```csharp
string str = "Hello";
str += " World"; // Creates a new string, "Hello World"
```
StringBuilder: `StringBuilder` is a mutable class that allows efficient string manipulation (like appending or inserting) without creating new instances.
#### 🧩 Example
StringBuilder is ideal for situations where you need to perform multiple string manipulations in a loop or dynamically change strings.
```csharp
StringBuilder sb = new StringBuilder("Hello");
sb.Append(" World"); // Modifies the original instance
```
#### Difference:
-   **Immutability (String)**: Strings are immutable, meaning every change creates anew object, making them less efficient for repeated changes.
-   **Mutability (StringBuilder)**: StringBuilder modifies the existing string, thus reducing memory usage and increasing performance for repetitive string operations.
