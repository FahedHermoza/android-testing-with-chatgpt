<h1 align="center">🧪 Entities Template </h1>

## 🤖 Example of entities generation using Independent Prompts
### Prompt:
```
Task: As an Android expert, I'll guide you in writing unit tests for a Kotlin class.

Principles: We will adhere to best practices by:

Keeping tests individual and focused.

Using string interpolation, spaces, and descriptive names for test functions.

Incorporating the parts "Event," "Action," and "Return" in test function names.

Following the AAA (Arrange, Act, Assert) pattern for each test function.

Class to convert:
internal data class Album(
    val name: String,
    val artist: String,
    val mbId: String? = null,
    val images: List<Image> = emptyList(),
    val tracks: List<Track>? = null,
    val tags: List<Tag>? = null,
) {

    val id: String = "$artist - $name"

    fun getDefaultImageUrl() = images.firstOrNull { it.size == ImageSize.EXTRA_LARGE }?.url
}

Consider the following related classes:
internal data class Image(
    val url: String,
    val size: ImageSize,
)

internal data class Track(
    val name: String,
    val duration: Int? = null,
)

internal data class Tag(
    val name: String,
)
```

## 🤖 Example of entities generation using the ChatGPT context
### Seed:
```
You should take this class as the base for future kotlin classes, keeping the structure:
class AlbumTest {

    @Test
    fun `Given an album with a name and artist, When creating an album, Then the ID should be formatted correctly`() {
        // Arrange
        val album = Album("Album Name", "Artist Name")

        // Act
        val id = album.id

        // Assert
        assertEquals("Artist Name - Album Name", id)
    }

    @Test
    fun `Given an album with images, When getting the default image URL, Then the URL of the first extra-large image should be returned`() {
        // Arrange
        val images = listOf(
            Image("url1", ImageSize.SMALL),
            Image("url2", ImageSize.EXTRA_LARGE),
            Image("url3", ImageSize.LARGE)
        )
        val album = Album("Album Name", "Artist Name", images = images)

        // Act
        val defaultImageUrl = album.getDefaultImageUrl()

        // Assert
        assertEquals("url2", defaultImageUrl)
    }

    @Test
    fun `Given an album without images, When getting the default image URL, Then null should be returned`() {
        // Arrange
        val album = Album("Album Name", "Artist Name")

        // Act
        val defaultImageUrl = album.getDefaultImageUrl()

        // Assert
        assertEquals(null, defaultImageUrl)
    }

    @Test
    fun `Given an album with empty images list, When getting the default image URL, Then null should be returned`() {
        // Arrange
        val album = Album("Album Name", "Artist Name", images = emptyList())

        // Act
        val defaultImageUrl = album.getDefaultImageUrl()

        // Assert
        assertEquals(null, defaultImageUrl)
    }
}
```
### Generator:
```
Task: As an Android expert, I'll guide you in writing unit tests for a Kotlin class.

Principles: We will adhere to best practices by:

Keeping tests individual and focused.

Using string interpolation, spaces, and descriptive names for test functions.

Incorporating the parts "Event," "Action," and "Return" in test function names.

Following the AAA (Arrange, Act, Assert) pattern for each test function.

Class to convert:
internal data class Album(
    val name: String,
    val artist: String,
    val mbId: String? = null,
    val images: List<Image> = emptyList(),
    val tracks: List<Track>? = null,
    val tags: List<Tag>? = null,
) {

    val id: String = "$artist - $name"

    fun getDefaultImageUrl() = images.firstOrNull { it.size == ImageSize.EXTRA_LARGE }?.url
}

Consider the following related classes:
internal data class Image(
    val url: String,
    val size: ImageSize,
)

internal data class Track(
    val name: String,
    val duration: Int? = null,
)

internal data class Tag(
    val name: String,
)

```
