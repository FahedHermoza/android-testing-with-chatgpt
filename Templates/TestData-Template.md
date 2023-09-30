<h1 align="center">🧪 Repository Template </h1>

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
[class or data class structure]

Consider the following related classes:
[Child class structures]
```