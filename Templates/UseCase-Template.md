<h1 align="center">🧪 UseCase </h1>

<div align="center">
        <img width="60%" src="screenshots/badge.svg" alt="About screen" title="About screen"</img>
        <img height="0" width="5px">
</div>

## 🤖 Templates using the ChatGPT context
### Seed:
```
You should take this class as the base for future kotlin classes, keeping the structure:
@OptIn(ExperimentalCoroutinesApi::class)
class GetAlbumIntegrationTest: BaseIntegrationTest() {

    // Mocks
    @Mock
    private lateinit var albumRepositoryMock: AlbumRepository

    // Class under test
    private lateinit var getAlbumUseCase: GetAlbumUseCase

    override fun build() {
        getAlbumUseCase = GetAlbumUseCase(albumRepositoryMock)
    }

    @Test
    fun `given valid input, when invoking GetAlbumUseCase, then it should return Result Success`() = runTest {
        // Arrange
        val artistName = "Artist"
        val albumName = "Album"
        val mbId = "123"
        val expectedResult = mockk<Album>()
        coEvery { albumRepositoryMock.getAlbumInfo(artistName, albumName, mbId) } returns Result.Success(expectedResult)

        // Act
        build()
        val result = getAlbumUseCase(artistName, albumName, mbId)

        // Assert
        assertEquals(Result.Success(expectedResult), result)
    }
}

Base Class: The Kotlin test class GetAlbumIntegrationTest extends BaseIntegrationTest.
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
### Generator:
```
Role: Behaving as an Android expert, we'll conduct unit testing for a Kotlin class.

Testing Framework: We will use the library MockK.

Testing Guidelines:
- Keep tests individual and focused.
- Using string interpolation, spaces, and descriptive names for test functions.
- Incorporating the parts "Given," "When," and "Then" in test function names.
- Follow the AAA pattern for test functions.
- Declare global variables using the @Mock annotation, with variable names suffixed by "mock."
- The test must use "runTest" as coroutine builder.

Kotlin Class to Test:
internal class GetAlbumListUseCase(
    private val albumRepository: AlbumRepository,
) {

    suspend operator fun invoke(query: String?): Result<List<Album>> {
        val result = albumRepository
            .searchAlbum(query)
            .mapSuccess {
                val albumsWithImages = value.filter { it.getDefaultImageUrl() != null }

                copy(value = albumsWithImages)
            }

        return result
    }
}
```

## 🤖 Templates using ChatGPT's Custom Instruction
### Seed: What would you like ChatGPT to know about you to provide better responses?
```
You should take this class as the base for future kotlin classes, keeping the structure:
@OptIn(ExperimentalCoroutinesApi::class)
class GetAlbumIntegrationTest: BaseIntegrationTest() {

    // Mocks
    @Mock
    private lateinit var albumRepositoryMock: AlbumRepository

    // Class under test
    private lateinit var getAlbumUseCase: GetAlbumUseCase

    override fun build() {
        getAlbumUseCase = GetAlbumUseCase(albumRepositoryMock)
    }

    @Test
    fun `given valid input, when invoking GetAlbumUseCase, then it should return Result Success`() = runTest {
        // Arrange
        val artistName = "Artist"
        val albumName = "Album"
        val mbId = "123"
        val expectedResult = mockk<Album>()
        coEvery { albumRepositoryMock.getAlbumInfo(artistName, albumName, mbId) } returns Result.Success(expectedResult)

        // Act
        build()
        val result = getAlbumUseCase(artistName, albumName, mbId)

        // Assert
        assertEquals(Result.Success(expectedResult), result)
    }
}
```
### Generator: How would you like ChatGPT to respond?
```
Role: Behaving as an Android expert, we'll conduct unit testing for a Kotlin class.

Testing Framework: We will use the library MockK.

Base Class: The Kotlin test class GetAlbumIntegrationTest extends BaseIntegrationTest.
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

Testing Guidelines:
- Keep tests individual and focused.
- Using string interpolation, spaces, and descriptive names for test functions.
- Incorporating the parts "Given," "When," and "Then" in test function names.
- Follow the AAA pattern for test functions.
- Declare global variables using the @Mock annotation, with variable names suffixed by "mock."
- The test must use "runTest" as coroutine builder.
```

### Next prompts
```
Kotlin Class to Test:
internal class GetAlbumListUseCase(
    private val albumRepository: AlbumRepository,
) {

    suspend operator fun invoke(query: String?): Result<List<Album>> {
        val result = albumRepository
            .searchAlbum(query)
            .mapSuccess {
                val albumsWithImages = value.filter { it.getDefaultImageUrl() != null }

                copy(value = albumsWithImages)
            }

        return result
    }
}
```
