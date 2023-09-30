<h1 align="center">🧪 Repository Template </h1>

## 🤖 Example of use case generation using the ChatGPT context
### Seed:
```
You should take this class as the base for future kotlin classes, keeping the structure:
@ExperimentalCoroutinesApi
class AlbumRepositoryImplTest : BaseIntegrationTest() {

    @MockK
    private lateinit var mockAlbumRetrofitService: AlbumRetrofitService

    @MockK
    private lateinit var mockAlbumDao: AlbumDao

    private lateinit var albumRepository: AlbumRepository

    override fun build() {
        albumRepository = AlbumRepositoryImpl(mockAlbumRetrofitService, mockAlbumDao)
    }

    @Test
    fun `Given valid search phrase, When searchAlbum is called, Then return list of albums`() = runTest {
        // Given
        val phrase = "SomePhrase"
        val searchAlbumResponse = SearchAlbumResponseMother.createSearchAlbumResponse()
        val apiResult = ApiResult.Success(searchAlbumResponse)
        coEvery { mockAlbumRetrofitService.searchAlbumAsync(phrase) } returns apiResult

        // When
        val result = albumRepository.searchAlbum(phrase)

        // Then
        assertTrue(result is Result.Success)
        val albumDomain = searchAlbumResponse.results.albumMatches.album.map { it.toDomainModel() }
        assertEquals(Result.Success(albumDomain), result)
        coVerify { mockAlbumDao.insertAlbums(any()) }
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
internal class AlbumRepositoryImpl(
    private val albumRetrofitService: AlbumRetrofitService,
    private val albumDao: AlbumDao,
) : AlbumRepository {

    override suspend fun searchAlbum(phrase: String?): Result<List<Album>> =
        when (val apiResult = albumRetrofitService.searchAlbumAsync(phrase)) {
            is ApiResult.Success -> {
                val albums = apiResult
                    .data
                    .results
                    .albumMatches
                    .album
                    .also { albumsApiModels ->
                        val albumsEntityModels = albumsApiModels.map { it.toEntityModel() }
                        albumDao.insertAlbums(albumsEntityModels)
                    }
                    .map { it.toDomainModel() }

                Result.Success(albums)
            }
            is ApiResult.Error -> {
                Result.Failure()
            }
            is ApiResult.Exception -> {
                Timber.e(apiResult.throwable)

                val albums = albumDao
                    .getAll()
                    .map { it.toDomainModel() }

                Result.Success(albums)
            }
        }
}
```

## 🤖 Example of use case generation using ChatGPT's Custom Instruction
### Seed: What would you like ChatGPT to know about you to provide better responses?
```
You should take this class as the base for future kotlin classes, keeping the structure:
@ExperimentalCoroutinesApi
class AlbumRepositoryImplTest : BaseIntegrationTest() {

    @MockK
    private lateinit var mockAlbumRetrofitService: AlbumRetrofitService

    @MockK
    private lateinit var mockAlbumDao: AlbumDao

    private lateinit var albumRepository: AlbumRepository

    override fun build() {
        albumRepository = AlbumRepositoryImpl(mockAlbumRetrofitService, mockAlbumDao)
    }

    @Test
    fun `Given valid search phrase, When searchAlbum is called, Then return list of albums`() = runTest {
        // Given
        val phrase = "SomePhrase"
        val searchAlbumResponse = SearchAlbumResponseMother.createSearchAlbumResponse()
        val apiResult = ApiResult.Success(searchAlbumResponse)
        coEvery { mockAlbumRetrofitService.searchAlbumAsync(phrase) } returns apiResult

        // When
        val result = albumRepository.searchAlbum(phrase)

        // Then
        assertTrue(result is Result.Success)
        val albumDomain = searchAlbumResponse.results.albumMatches.album.map { it.toDomainModel() }
        assertEquals(Result.Success(albumDomain), result)
        coVerify { mockAlbumDao.insertAlbums(any()) }
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
internal class AlbumRepositoryImpl(
    private val albumRetrofitService: AlbumRetrofitService,
    private val albumDao: AlbumDao,
) : AlbumRepository {

    override suspend fun searchAlbum(phrase: String?): Result<List<Album>> =
        when (val apiResult = albumRetrofitService.searchAlbumAsync(phrase)) {
            is ApiResult.Success -> {
                val albums = apiResult
                    .data
                    .results
                    .albumMatches
                    .album
                    .also { albumsApiModels ->
                        val albumsEntityModels = albumsApiModels.map { it.toEntityModel() }
                        albumDao.insertAlbums(albumsEntityModels)
                    }
                    .map { it.toDomainModel() }

                Result.Success(albums)
            }
            is ApiResult.Error -> {
                Result.Failure()
            }
            is ApiResult.Exception -> {
                Timber.e(apiResult.throwable)

                val albums = albumDao
                    .getAll()
                    .map { it.toDomainModel() }

                Result.Success(albums)
            }
        }
}
```
