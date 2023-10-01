<h1 align="center">Android Testing Enhanced with ChatGPT 🧪</h1>

<div align="center">
        <img width="60%" src="screenshots/badge.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

Welcome to Android Testing with ChatGPT! The goal of this repository is to implement the use of an AI tool like "ChatGPT" in the testing process, adhering to the current standards used by an Android engineering team.

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
The first one, the structure using the ChatGPT context. ChatGPT is designed to maintain context within a conversation, allowing it to understand and respond to the current thread of conversation.

The second one, using custom instructions. Through this functionality, ChatGPT allows us to preload 2 prompts through 2 questions, which will be useful to load the seed and the generator. Here, we must take into account the limit of 1500 characters for each preloaded prompt.

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

 2. Video
 - Here you will find the video of the process 👇
[![Alt text](https://img.youtube.com/vi/_Nnb6_vjATI/0.jpg)](https://www.youtube.com/watch?v=_Nnb6_vjATI)
 
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

 2. Video
 - Here you will find the video of the process 👇
[![Alt text](https://img.youtube.com/vi/uCEEq_JYcqw/0.jpg)](https://www.youtube.com/watch?v=uCEEq_JYcqw)

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

 2. Video
 - Here you will find the video of the process 👇
[![Alt text](https://img.youtube.com/vi/SRHtpYKzlxU/0.jpg)](https://www.youtube.com/watch?v=SRHtpYKzlxU)
 
 3. Use Case
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

 2. Video
 - Here you will find the video of the process 👇
[![Alt text](https://img.youtube.com/vi/vNmk_uV9VIo/0.jpg)](https://www.youtube.com/watch?v=vNmk_uV9VIo)

 3. Use Case
 <div align="center">
        <img width="75%" src="screenshots/Repository/Context/Repository.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>
 
 4. Generated Code
 <div align="center">
        <img width="75%" src="screenshots/Repository/CustomInstructions/RepositoryTest.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>


## 🚀 Generate Test Data
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

 2. Video
 - Here you will find the video of the process 👇
[![Alt text](https://img.youtube.com/vi/LfX0CiPRgAQ/0.jpg)](https://www.youtube.com/watch?v=LfX0CiPRgAQ)

3. Use Case
 <div align="center">
        <img width="75%" src="screenshots/TestData/Context/DataClass.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>
 
 4. Generated Code
 <div align="center">
        <img width="75%" src="screenshots/TestData/Context/ObjectMother.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>


## 🚦 Wrap Up
If you have an idea to improve the map, feel free to discuss it in the issues.

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