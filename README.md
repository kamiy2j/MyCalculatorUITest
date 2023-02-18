# MyCalculatorUITest
 UI Testing - Jetpack Compose - Sample App

UI Test:
```
import androidx.compose.ui.test.*
import androidx.compose.ui.test.junit4.createAndroidComposeRule
import androidx.test.ext.junit.runners.AndroidJUnit4
import org.junit.runner.RunWith
import org.junit.Assert.*
import org.junit.Rule
import org.junit.Test

@RunWith(AndroidJUnit4::class)
class CalculatorOperationsE2ETest {

    @get:Rule
    val composeTestRule = createAndroidComposeRule<MainActivity>()

    private val oneButton = hasText("1") and hasClickAction()
    private val twoButton = hasText("2") and hasClickAction()
    private val threeButton = hasText("3") and hasClickAction()
    private val fourButton = hasText("4") and hasClickAction()

    private val additionButton = hasText("+") and hasClickAction()
    private val subtractionButton = hasText("-") and hasClickAction()
    private val multiplicationButton = hasText("x") and hasClickAction()
    private val divisionButton = hasText("/") and hasClickAction()

    private val equalsButton = hasText("=") and hasClickAction()

    @Test
    fun additionOperationTest() {
        composeTestRule.onNode(oneButton).performClick()
        composeTestRule.onNode(additionButton).performClick()
        composeTestRule.onNode(twoButton).performClick()
        composeTestRule.onNodeWithText("1+2").assertIsDisplayed()

        composeTestRule.onNode(equalsButton).performClick()
        composeTestRule.onNodeWithText("3.0").assertIsDisplayed()
    }

    @Test
    fun subtractionOperationTest() {
        composeTestRule.onNode(oneButton).performClick()
        composeTestRule.onNode(subtractionButton).performClick()
        composeTestRule.onNode(twoButton).performClick()
        composeTestRule.onNodeWithText("1-2").assertIsDisplayed()

        composeTestRule.onNode(equalsButton).performClick()
        composeTestRule.onNodeWithText("-1.0").assertIsDisplayed()
    }

    @Test
    fun multiplicationOperationTest() {
        composeTestRule.onNode(twoButton).performClick()
        composeTestRule.onNode(multiplicationButton).performClick()
        composeTestRule.onNode(fourButton).performClick()
        composeTestRule.onNodeWithText("2x4").assertIsDisplayed()

        composeTestRule.onNode(equalsButton).performClick()
        composeTestRule.onNodeWithText("8.0").assertIsDisplayed()
    }

    @Test
    fun divisionOperationTest() {
        composeTestRule.onNode(fourButton).performClick()
        composeTestRule.onNode(divisionButton).performClick()
        composeTestRule.onNode(twoButton).performClick()
        composeTestRule.onNodeWithText("4/2").assertIsDisplayed()

        composeTestRule.onNode(equalsButton).performClick()
        composeTestRule.onNodeWithText("2.0").assertIsDisplayed()
    }

    @Test
    fun operationsE2ETest() {
        composeTestRule.onNode(threeButton).performClick()
        composeTestRule.onNode(additionButton).performClick()
        composeTestRule.onNode(fourButton).performClick()
        composeTestRule.onNodeWithText("3+4").assertIsDisplayed()

        composeTestRule.onNode(equalsButton).performClick()
        composeTestRule.onNodeWithText("7.0").assertIsDisplayed()

        composeTestRule.onNode(subtractionButton).performClick()
        composeTestRule.onNode(twoButton).performClick()
        composeTestRule.onNodeWithText("7.0-2").assertIsDisplayed()

        composeTestRule.onNode(equalsButton).performClick()
        composeTestRule.onNodeWithText("5.0").assertIsDisplayed()

        composeTestRule.onNode(multiplicationButton).performClick()
        composeTestRule.onNode(twoButton).performClick()
        composeTestRule.onNodeWithText("5.0x2").assertIsDisplayed()

        composeTestRule.onNode(equalsButton).performClick()
        composeTestRule.onNodeWithText("10.0").assertIsDisplayed()

        composeTestRule.onNode(divisionButton).performClick()
        composeTestRule.onNode(twoButton).performClick()
        composeTestRule.onNodeWithText("10.0/2").assertIsDisplayed()

        composeTestRule.onNode(equalsButton).performClick()
        composeTestRule.onNodeWithText("5.0").assertIsDisplayed()
    }
}

```
UI test in action:
![ezgif-3-224ee40168](https://user-images.githubusercontent.com/22699271/219877800-e541f24e-5264-4db5-aef9-207e6bdb5c48.gif)

