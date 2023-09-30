<h1 align="center">🧪 Test Data Template </h1>

## 🤖 Example of use case generation using the ChatGPT context
### Seed:
```
You should take this class as the base for future kotlin mother classes:
object AdditionalCheckResponseMother {
    fun createAdditionalCheckResponse(
        accountNumber: String = "12345678",
        currency: String = "USD",
        creditLine: String = "1000",
        cardNumber: String = "98765432",
        beneficiary: String = "John Doe",
        markCode: String = "M",
        mark: String = "Mark",
        situation: String = "Active",
        status: String = "Approved",
        typeCode: String = "T",
        type: String = "Type",
        activationDate: String = "2023-01-01",
        additionalCards: List<AdditionalCheckResponse.AdditionalAccount.AdditionalAccountCard>? = null,
        minimumLineAmount: String = "500"
    ): AdditionalCheckResponse {
        return AdditionalCheckResponse(
            accounts = arrayListOf(
                AdditionalCheckResponse.AdditionalAccount(
                    accountNumber = accountNumber,
                    currency = currency,
                    creditLine = creditLine,
                    card = AdditionalCheckResponse.AdditionalAccount.AdditionalAccountCard(
                        cardNumber = cardNumber,
                        beneficiary = beneficiary,
                        markCode = markCode,
                        mark = mark,
                        situation = situation,
                        status = status,
                        typeCode = typeCode,
                        type = type,
                        activationDate = activationDate,
                        additionalCards = additionalCards
                    )
                )
            ),
            minimumLineAmount = minimumLineAmount
        )
    }
}

```

### Generator:
```
Task: Can you give me a function that mocks the following class to test? 

Testing Language: Kotlin

Testing Guidelines:
- Use Martin Fowler's mother pattern object. 
- Provide default values that are neither null nor empty. 
- Don't generate comments on default values:

Class to convert:
@Serializable
internal data class GetAlbumInfoResponse(
    @SerialName("album") val album: AlbumApiModel,
)

Consider the following related classes:
@Serializable
internal data class AlbumApiModel(
    @SerialName("mbid") val mbId: String? = null,
    @SerialName("name") val name: String,
    @SerialName("artist") val artist: String,
    @SerialName("image") val images: List<ImageApiModel>? = null,
    @SerialName("tracks") val tracks: TrackListApiModel? = null,
    @SerialName("tags") val tags: TagListApiModel? = null,
)

@Serializable
internal data class ImageApiModel(
    @SerialName("#text") val url: String,
    @SerialName("size") val size: ImageSizeApiModel,
)

@Serializable
internal enum class ImageSizeApiModel {

    @SerialName("medium")
    MEDIUM,

    @SerialName("small")
    SMALL,

    @SerialName("large")
    LARGE,

    @SerialName("extralarge")
    EXTRA_LARGE,

    @SerialName("mega")
    MEGA,

    @SerialName("")
    UNKNOWN,
}

@Serializable
internal data class TrackListApiModel(
    @SerialName("track") val track: List<TrackApiModel>,
)

@Serializable
internal data class TrackApiModel(
    @SerialName("name") val name: String,
    @SerialName("duration") val duration: Int? = null,
)

@Serializable
internal data class TagListApiModel(
    @SerialName("tag") val tag: List<TagApiModel>,
)

@Serializable
internal data class TagApiModel(
    @SerialName("name") val name: String,
)
```