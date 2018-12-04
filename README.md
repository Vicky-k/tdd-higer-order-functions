## TDD Vending Machine

### Objectives:

- Give and receive feedback on pairing behaviors - see Pairing Rubric below
- Practice writing tests first
- Practice writing good tests - SEAT pattern
- Practice the `refactor` phase of red, green, refactor, commit
- Practice frequent commits with good messages

### Instructions

1. This exercise is meant to be completed with pair programming.  Discuss when you will change driver/navigator roles.
1. `fork` this repository.
1. `clone` your fork of this repsitory.
1. Import the `build.gradle` file into idea.
1. Use the acceptance criteria for the first story to write a failing test.
1. Write the **simplest** code needed to make the test pass. 
1. Refactor. 
    - Are any methods more than 5 or 10 lines of code?
    - Is it obvious what each section of code does? If not, how could you make it obvious?
1. Commit with an informative message
1. Move on to the next user story and continue until all stories are completed.


### User Stories
As a customer, I want to see what is available to purchase from the vending, so that I can make a purchase.

- Given that I approach the vending machine
- when I look at it,
- then I see items inside available for purchase.
- `getItems()` returns multiple objects with description and price:
`["A1 - crisps for Rs 100", "A2 - chocolate for Rs 350", "A3 - mints for Rs 70"}]`

As a customer, I want to know how much money I have deposited, so that I know what I can purchase.

- Given I am using the vending machine, 
- when I insert money, 
- then I see the total I have deposited on a screen. 
- `deposit(100)` returns `"You have deposited Rs 100"`
- The machine should accept bills in these amounts: `10, 20, 50, 100, 500`

As a customer, I want to add additional money, so that I can use the denominations I have to purchase an item.

- Given I have deposited money in the vending machine,
- when I deposit additional money,
- then I see the new total on a screen. 
- After depositing Rs 100, `deposit(50)` returns `"You have deposited Rs 150"`

As a customer, I want to see a message if I enter a non-existent code, so that I can make another choice.

- Given I am using the vending machine, 
- when I enter a non-existent code for an item, 
- then I see a message that the code does not exist.
- `selectItem(code)` returns an object with the message `{ "message": "Code Z3 does not exist. Please try again."}`

As a customer, I want to see a message if my item is unavailable, so that I can make another choice.

- Given I am using the vending machine, 
- when I enter a code for an item that is unavailable, 
- then I see a message that the item is unavailable.
- `selectItem(code)` returns an object with the message `{ "message": "The item you selected is unavailable"}`

As a customer, I want to see a message if my deposit is insufficient, so that I know to add more money.

- Given I have made a choice, 
- when I have not deposited enough money for that item, 
- then I see a message telling me how much more to deposit.
- `selectItem(code)` returns `{ "message": "Your deposit is insufficient.  Please add Rs 20 for this item"}`

As a customer, I want to receive change, so that I don’t pay more than the item costs.

- Given I have made a selection, 
- when the item is delivered, 
- then I receive correct change (in correct monetary units)
- `selectItem(code)` returns an object with the item and multiple bills `{"item": "mints", "change": [20, 10], "message" : "Thank you"}`

As a customer, I want to receive my money back when I push the cancel button, so that I can change my mind.

- Given that I have deposited money,
- When I push the cancel button,
- Then I receive my money back
- `cancel()` returns `[100]`

As a customer, I want to know if the vending machine can make change, so that I can cancel my choice if it can't make change.

- Given I have deposited money and selected a choice, 
- when the machine does not have correct change, 
- then I see a message
- `selectItem(code)` returns `{"message": "Cannot return proper change.  Please choose another item or cancel the transaction"`

Methods:  
- `getItems()` => multiple objects with item and price
- `deposit(denomination)` => totalDeposit  
- `selectItem(code)` => item + change || insufficient funds msg || insufficient change msg || item not available msg  
- `cancel()` => totalDepositReturned

You may have more public methods than than those listed above.

### Pairing Rubric

| Pairing Behavior  | Needs Improvement | In Between    | Desirable |
|---                |---                |---            |---        |
Driving/navigating time | One pair keeps control the whole time, or takes over inappropriately | | Driver and navigator take turns as appropriate for their relative experience levels
Engagement | Navigator on their phone or another computer, sleeping, gone  | | Both pairs are attentive and engaged in the process
Communication | Either pair goes silent, Navigator is domineering  | | Communicates needs for breaks, asks clarifying questions, Both think out loud
Giving feedback | Criticizing or blaming your pair | | Kind, Actionable, Specific,Consensual
Navigating | Tells pair what to type, corrects every syntax error immediately, Takes over control | | Proposes theory for driver to test, Gives high-level suggestions, Asks about edge cases, Answers questions
Driving | Writes code on their own without navigator’s input || Asks questions, uses split screen
