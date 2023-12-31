<h1 align="center">Android Testing Enhanced with ChatGPT 🧪</h1>

<div align="center">
        <img width="60%" src="screenshots/badge.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

Welcome to Android Testing with ChatGPT! The goal of this repository is to implement the use of an AI tool like “ChatGPT” in the testing process, adhering to the current standards used by an Android engineering team. With this proposal, we can achieve significantly shorter development times for "Test case generation", "Test data generation", and the "Creation of explanatory comments"

Here is a guide that will give you an introduction to the terminology used in this repository: A Brief Narrative, Repository Overview, Android Testing, Testing Approach, ChatGPT (Context, Custom Instructions, controversy), Generation of Similar Functions.
- **[Guidelines](https://medium.com/@fahedhermoza/android-testing-guidelines-enhanced-with-chatgpt-48d5ef51dd39)**

This contains all topics to help you find what you are looking for quickly. I hope I can help you.

## 🤖 Android Testing
<div align="center">
        <img width="100%" src="screenshots/AndroidTestingChatGPT-General.png" alt="About screen" title="About screen"</img>
        <img height="0" width="16px">
</div>

## 🏠 Base Project
For the examples in the repository, we used the android-showcase project by Igor Wodja as a foundation. This project was chosen because it adheres to the best practices in the industry up to the present day. Although the application is small, it could be considered as an enterprise-type application due to the comprehensive architecture of its core.
- **[android-showcase by @igorwojda](https://github.com/igorwojda/android-showcase)**

## 🤖💬 Artificial Intelligence (AI) Tool: ChatGPT
ChatGPT is a natural language processing artificial intelligence tool developed by OpenAI. While ChatGPT can offer valuable assistance, it’s crucial to emphasize that it should not be considered a replacement for thorough code reviews, rigorous testing, or professional advice when addressing critical tasks in software development. Software engineers should use ChatGPT as a complementary tool to enhance their productivity and problem-solving skills, especially in specific cases such as testing.

Taking advantage of its ability to generate coherent and relevant text, we will focus on three key applications of ChatGPT in software testing:

1. **Test Case Generation:** ChatGPT can assist in automatically generating test cases in natural language. Describing the expected behavior of a function or feature allows ChatGPT to generate detailed test cases.
2. **Test Data Generation:** ChatGPT can be used to generate realistic test data, valuable for evaluating software performance and scalability.
3. **Documentation, Comments, and Support:** ChatGPT can be a valuable tool for creating documentation, both for end-users and internal use. It facilitates explaining how to use various functions and provides answers to frequently asked questions.

While we can create basic templates using ChatGPT, **the output always must undergo a thorough review by a software engineer**. This is because the tool's effectiveness is approximately 60%, which means there will always be a margin of error that needs to be analyzed, taking into consideration the engineer's expertise.

## 🧩 Unit Test
Unit tests verify how the isolated parts of your app work.

### Guidelines
1. Keep the tests small, individual, and focused.
2. Function names should use interpolated strings, respecting spaces, following the structure: Given - When - Then.
3. The function structure should follow the AAA pattern (Arrange-Act-Assert).
4. Explanatory comment: In cases where the function doesn't have a clear name and requires context, you can include an explanatory comment in Kotlin KDoc format.
5. The class name should use the "Test" suffix.
6. Tool used: JUnit.

## 🚀 Test Case Generation
We will use two structures provided by ChatGPT:
1. Independent Prompts: This is the most basic structure that allows us to provide details in a single prompt. However, it has a limitation.
2. The Context: ChatGPT is designed to maintain the context within a conversation, enabling it to understand and respond to the current conversation thread.

### 🛠  Using Independent Prompts
```
Task: As an Android expert, I'll guide you in writing unit tests for a Kotlin class.
Principles: We will adhere to best practices by:
Keeping tests individual and focused.
Using string interpolation, spaces, and descriptive names for test functions.
Incorporating the parts "Event," "Action," and "Return" in test function names.
Following the AAA (Arrange, Act, Assert) pattern for each test function.

Class to convert:
[class or data class structure]

Consider the following related classes:
[Child class structures]
```

### 🛠  Using the Context
With the previously mentioned structure, we can obtain a base class with the established guidelines. From there, we can proceed with generating similar functions, as described in the [guideline](https://fahedhermoza.medium.com/android-testing-guidelines-enhanced-with-chatgpt-48d5ef51dd39). To create functions based on the base class, we will use the concept of seed and generator. If you want more information about seed and generator, go to this [link](https://fahedhermoza.medium.com/android-testing-guidelines-enhanced-with-chatgpt-48d5ef51dd39).

Seed
```
You should take this class as the base for future kotlin classes, keeping the structure:
[Example Base Class]
```

Generator
```
Task: As an Android expert, I'll guide you in writing unit tests for a Kotlin class.
Principles: We will adhere to best practices by:
Keeping tests individual and focused.
Using string interpolation, spaces, and descriptive names for test functions.
Incorporating the parts "Event," "Action," and "Return" in test function names.
Following the AAA (Arrange, Act, Assert) pattern for each test function.

Class to convert:
[class or data class structure]

Consider the following related classes:
[Child class structures]
```

### 🧪 Entities
#### Example of entities generation using Independent Prompts:

 1. Templates
 - **[Here you will find the seed and generator used](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/Entities-Template.md)**

 2. Process
 - **[Here you will find the video of the process](https://youtu.be/HsnxdF147iQ)**
 
 3. Use Case
 <div align="center">
        <img width="75%" src="screenshots/Entities/Prompt/Entities.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

 4. Generated Code
 <div align="center">
        <img width="75%" src="screenshots/Entities/Prompt/EntitiesTest.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

#### Example of entities generation using the ChatGPT context:
It sounds strange, but for cases like the example presented, I take the AlbumTest class as a basis and create unit tests for the Album class. A result similar to AlbumTest should be obtained; however, this should work for any entity other than Album.
 1. Templates
 - **[Here you will find the seed and generator used](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/Entities-Template.md#-example-of-entities-generation-using-the-chatgpt-context)**

 2. Process
 - **[Here you will find the video of the process]()**
 
 3. Use Case
 <div align="center">
        <img width="75%" src="screenshots/Entities/Prompt/Entities.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

 4. Generated Code
 <div align="center">
        <img width="75%" src="screenshots/Entities/Context/EntitiesTtest.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

## 🧩 Integration Test
Integration tests are responsible for verifying interactions and connection points among various components, modules, and services within an Android application.

### Guidelines
1. Keep tests small, individual, and focused.
2. Function names should use interpolated strings, respecting spaces, following the structure: Given - When - Then.
3. The function structure should follow the AAA pattern (Arrange-Act-Assert).
4. The class name should use the Test suffix.
5. Tools used: JUnit and Mockito or JUnit and MockK.
6. Declare global variables using the @Mock annotation for Mockito or @MockK for MockK, with variable names suffixed with "mock."
7. Use runTest to carry out the execution of asynchronous processes.
8. If you need to generate data for tests, use the structure of Martin Fowler's Object Mother pattern.

### Parent Class
Our example implementation has a base class called BaseTest, from which all test classes will inherit, conforming to the structure built within this class.
```
@ExperimentalCoroutinesApi
abstract class BaseIntegrationTest {
    @get:Rule
    val testInstantTaskTaskExecutorRule = InstantTaskExecutorRule()

    @Before
    fun setup() {
        val testDispatcher = StandardTestDispatcher()
        Dispatchers.setMain(testDispatcher)
        MockKAnnotations.init(this)
    }

    @After
    fun tearDown() {
        Dispatchers.resetMain()
        unmockkAll()
    }

    abstract fun build()
}
```

## 🚀 Test Case Generation
To create similar functions from a sample base class, we will use the concept of Seed and Generator from the realm of pseudo-random numbers, explained in detail in the Guidelines.

We will base ourselves on 2 structures:
1. The context: ChatGPT is designed to maintain context within a conversation, allowing it to understand and respond to the current thread of conversation.

2. Custom instructions: Through this functionality, ChatGPT allows us to preload 2 prompts through 2 questions, which will be useful to load the seed and the generator. Here, we must take into account the limit of 1500 characters for each preloaded prompt.

### 🛠  Using the context
Seed
```
You should take this class as the base for future kotlin classes, keeping the structure:
[Example Base Class]

Base Class: The Kotlin test class [Name Example Base Class] extends [Name Parent Class].
[Parent Class]
```

Generator
```
Role: Behaving as an Android expert, we'll conduct unit testing for a Kotlin class.

Testing Framework: We will use the library [MockK or Mockito].

Testing Guidelines:
- Keep tests individual and focused.
- Using string interpolation, spaces, and descriptive names for test functions.
- Incorporating the parts "Given," "When," and "Then" in test function names.
- Follow the AAA pattern for test functions.
- Declare global variables using the @Mock annotation, with variable names suffixed by "mock."
- The test must use "runTest" as coroutine builder.

Kotlin Class to Test:
[Class or function to test]
```

### 🛠 Using custom instructions

Seed: What would you like ChatGPT to know about you to provide better responses?
```
You should take this class as the base for future kotlin classes, keeping the structure:
[Example Base Class]
```

Generator: How would you like ChatGPT to respond?
```
Role: Behaving as an Android expert, we'll conduct unit testing for a Kotlin class.

Testing Framework: We will use the library [MockK or Mockito].

Base Class: The Kotlin test class extends [Name Parent Class].
[Parent Class]

Testing Guidelines:
- Keep tests individual and focused.
- Using string interpolation, spaces, and descriptive names for test functions.
- Incorporating the parts "Given," "When," and "Then" in test function names.
- Follow the AAA pattern for test functions.
- Declare global variables using the @Mock annotation, with variable names suffixed by "mock."
- The test must use "runTest" as coroutine builder.
```
### 🧪 UseCase
#### Example of use case generation using the ChatGPT context:

 1. Templates
 - **[Here you will find the seed and generator used](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/UseCase-Template.md#-example-of-use-case-generation-using-the-chatgpt-context)**

 2. Process
 - **[Here you will find the video of the process](https://www.youtube.com/watch?v=_Nnb6_vjATI)**
 
 3. Use Case
<div align="center">
        <img width="75%" src="screenshots/UseCase/Context/UseCase.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

 4. Generated Code
<div align="center">
        <img width="75%" src="screenshots/UseCase/Context/UseCaseTest.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

#### Example of use case generation using ChatGPT's Custom Instruction:
 1. Templates
- **[Here you will find the seed, generator, prompt used](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/UseCase-Template.md#-example-of-use-case-generation-using-chatgpts-custom-instruction)**

 2. Process
 - **[Here you will find the video of the process](https://www.youtube.com/watch?v=uCEEq_JYcqw)**

 3. Use Case
<div align="center">
        <img width="75%" src="screenshots/UseCase/Context/UseCase.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

 4. Generated Code
<div align="center">
        <img width="75%" src="screenshots/UseCase/CustomInstructions/UseCaseTest.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

### 🧪 Repository
#### Example of repository generation using the ChatGPT context:

 1. Templates
 - **[Here you will find the seed and generator used](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/Repository-Template.md#-example-of-use-case-generation-using-the-chatgpt-context)**

 2. Process
 - **[Here you will find the video of the process](https://www.youtube.com/watch?v=SRHtpYKzlxU)**
 
 3. Repository
<div align="center">
        <img width="75%" src="screenshots/Repository/Context/Repository.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

 4. Generated Code
<div align="center">
        <img width="75%" src="screenshots/Repository/Context/RepositoryTest.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

#### Example of repository generation using ChatGPT's Custom Instruction:
 1. Templates
- **[Here you will find the seed, generator, prompt used](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/Repository-Template.md#-example-of-use-case-generation-using-chatgpts-custom-instruction)**

 2. Process
 - **[Here you will find the video of the process](https://www.youtube.com/watch?v=vNmk_uV9VIo)**

 3. Repository
 <div align="center">
        <img width="75%" src="screenshots/Repository/Context/Repository.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>
 
 4. Generated Code
 <div align="center">
        <img width="75%" src="screenshots/Repository/CustomInstructions/RepositoryTest.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>


## 🚀 Test Data Generation
Use the structure of the Object Mother pattern to generate test data. Add the suffix "Mother" to the class name, for example, CreateAdditionalCardMother. The term "Mother" comes from Domain-Driven Design (DDD) and symbolizes the birth or creation of objects. In the context of Martin Fowler's Object Mother pattern, these classes are used to centralize the creation of test objects and provide default values to simplify test data setup. It is advisable to use this class for objects that exceed 10 lines of code.

### 🛠️ Using the context
Seed
```
You should take this class as the base for future kotlin mother classes:
[Example Base Class]
```

Generator
```
Task: Can you give me a function that mocks the following class to test? 

Testing Language: Kotlin

Testing Guidelines:
- Use Martin Fowler's mother pattern object. 
- Provide default values that are neither null nor empty. 
- Don't generate comments on default values:

Class to convert:
[class or data class structure]

Consider the following related classes:
[Child class structures]
```
### 🧪 Data Class
 1. Templates
- **[Here you will find the seed and generator used](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/DataClass-Template.md)**

 2. Process
 - **[Here you will find the video of the process](https://www.youtube.com/watch?v=LfX0CiPRgAQ)**

3. Data Class
 <div align="center">
        <img width="75%" src="screenshots/TestData/Context/DataClass.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>
 
 4. Generated Code
 <div align="center">
        <img width="75%" src="screenshots/TestData/Context/ObjectMother.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>


## 🚀 Generate explanatory comment
In cases where the function doesn't have a clear name and requires context, you can include an explanatory comment in Kotlin KDoc format. In Kotlin, KDoc (Kotlin Doc) is used for documenting code. But you can use JavaDoc or Python's docstrings depending on the project.


### 🛠 ️Using Independent Prompts
```
Task: As an [Android] expert, I'll generate the document of function kotlin.

Principles:
- Document the code in Kotlin using the [KDoc format]. 
- Provide descriptions for the functions and their parameters.

Testing functions to document:
[Functions structure]
```

### 🧪 Testing functions
#### Example of generate explanatory comment using  Independent Prompts:

 1. Templates
- Here you will find the function used:
    - **[Entities](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/TestingFunctions-Template.md#prompt-for-function-of-entities)**
    - **[Use Case](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/TestingFunctions-Template.md#prompt-for-function-of-usecase)**
    - **[Repository](https://github.com/FahedHermoza/android-testing-with-chatgpt/blob/main/Templates/TestingFunctions-Template.md#prompt-for-function-of-respository)**

 2. Process
 - **[Here you will find the video of the process](https://youtu.be/ui61FbPirhw)**
 
 3. Testing functions
 <div align="center">
        <img width="75%" src="screenshots/TestingFucntions/Prompt/TestingFunctions.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

 4. Generated Code
 <div align="center">
        <img width="75%" src="screenshots/TestingFucntions/Prompt/TestingFunctionsDoc.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

## 🚦 Wrap Up
If you have an idea to improve this proposal, do not hesitate to comment in the issues.

## ⚠️  Disclamer
Use the content of this repository at your discretion and with caution.

## Find this project useful? :heart:

Support it by joining __[stargazers](https://github.com/FahedHermoza/android-architecture-roadmap/stargazers)__ for this repository. :star: <br>
And __[follow](https://www.linkedin.com/in/fahedhermoza/)__ me for my next creations! 🤩

License
-------

    Copyright 2023 Fahed Hermoza

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.