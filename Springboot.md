### Wedding Invitation Using Spring Boot Concepts

#### Code Snippets

```kotlin
import org.springframework.boot.SpringApplication
import org.springframework.boot.autoconfigure.SpringBootApplication
import org.springframework.stereotype.Component
import org.springframework.stereotype.Service
import org.springframework.web.bind.annotation.GetMapping
import org.springframework.web.bind.annotation.RestController

@SpringBootApplication
class WeddingApplication

fun main(args: Array<String>) {
    SpringApplication.run(WeddingApplication::class.java, *args)
}

// Define LoveService to handle the "business logic" of love
@Service
class LoveService {
    fun integrateLove(partner1: String, partner2: String): String {
        return "$partner1 ❤️ $partner2 = Eternal Happiness"
    }
}

// Define the CoupleComponent to represent the happy couple
@Component
class CoupleComponent {
    val partner1 = "Ahmad"
    val partner2 = "Siti"
}

// Define the WeddingController to display the wedding details
@RestController
class WeddingController(
    private val loveService: LoveService,
    private val coupleComponent: CoupleComponent
) {
    @GetMapping("/wedding")
    fun weddingDetails(): String {
        val love = loveService.integrateLove(coupleComponent.partner1, coupleComponent.partner2)
        return """
            🌸 Wedding Invitation 🌸
            Couple: ${coupleComponent.partner1} and ${coupleComponent.partner2}
            Message: $love
            Date: February 24, 2025
            Time: 11:00 AM - 4:00 PM
            Location: Dewan Harmoni [3.0899, 101.5171]
        """.trimIndent()
    }
}

```

#### Output (When You Run the App)
If you navigate to `http://localhost:8080/wedding`, you’ll see this:
```yaml
🌸 Wedding Invitation 🌸
Couple: Ahmad and Siti
Message: Ahmad ❤️ Siti = Eternal Happiness
Date: February 24, 2025
Time: 11:00 AM - 4:00 PM
Location: Dewan Harmoni [3.0899, 101.5171]

```
