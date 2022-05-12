0xabc975eea144ef24

DAY 1
    #Explain what the Blockchain is in your own words. 
    #Blockchain is a database that is shared publicly and anyone can see the data on the blockchain. There is no governing body or any one organisation #dictating what we should or shouldn't do. 
    #Explain what a Smart Contract is.
    #A smart contract is a kind of rule book for the blockchain.They have to be written and tested carefully(on TestNet) before they are put on MainNet because #otherwise things can go wrong and people can lose a lot of money. Some people do this intentionally to scam people, so knowledge of smart contracts need to be #more widespread so that people dont get scammed. They include a function, some sort of parameter(age?), it stores that parameter and then sends it to the #updated data to the blockchain. With smart contracts there is no middle man so they can be actioned quickly, and they are usually shared with communities so that there is trust and transparency within the project.
    #Explain the difference between a script and a transaction.
    #A script is a line of code that reads information from a blockchain
    #A transaction is a paid function call(when data gets changed on a blockchain). On certain blockchains this payment is known as gas and is a complete rip #off!
    
DAY 2
    What are the 5 Cadence Programming Language Pillars?
    Security and safety
    Clarity
    Approachability
    Developer experience
    Resource oreintated programming.
    
    In your opinion, even without knowing anything about the Blockchain or coding, why could the 5 Pillars be useful (you don't have to answer this for #5)?
Security and safety are vital because if people are going to use this blockchain we need to be able to guarantee that their assets are safe and secure. This is very important if this is going to be adopted by the masses. If this is not in place then the blockchain will not have integrity and will not survive.

Clarity of code is useful as it allows whole communities of people to understand what is happening with their items on the blockchain. It also allows other developers the chance to inmspect the contracts of other projects and help people not to be potentially scammed or make mistakes.

Approachability is useful as it allows anyone with some coding experience to identify what certain parts of the code means so it will hopefully be easier for more and more developers to be invovled and that can only help and improve the community as a whole since flow is still newish.

Developer experience is useful because being able to find bugs quickly and develop at a faster speed. To be able to find a solution would help the whole community grow quickly will only help more developers be involved.

Chapter 1.5
Basics of functions, use of concatenation.

Chapter 2 

Day 1

Make first smart contract, write a script to read the variable

![Chapter 2 img 2](https://user-images.githubusercontent.com/104719670/166220651-4ff327b6-3eaa-4392-81e8-bc8eeec60bd8.png)
![Chapter 2 img1](https://user-images.githubusercontent.com/104719670/166220657-f8871536-1989-4999-b44b-cef53fc743e8.png)

Day 2

Explain why we wouldn't call changeGreeting in a script.
As you only use scripts to read data from the Blockchain. Change greeting is changing something on the Blockchain so is a transaction??

What does the AuthAccount mean in the prepare phase of the transaction?
It gives the transacion permission to access your account and the data within it.

What is the difference between the prepare phase and the execute phase in the transaction?
Prepare is giving access to an acccount and the excute phase is about the change.


Add two new things inside your contract:
        A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
        A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber
I think this is the correct code for the contract - Can someon confirm this to be true? TIA
![Ch2 day2 Contract code](https://user-images.githubusercontent.com/104719670/166458405-29cf8150-ad59-42b9-a959-7ae394f209a4.png)
pub contract HelloWorld {

    pub var greeting: String

    pub fun changeGreeting(newGreeting: String) {
        self.greeting = newGreeting
    }

    pub var myNumber: Int

    pub fun updateMyNumber(newNumber: Int)  {
        self.myNumber = newNumber
    }

    init() {
        self.greeting = "Hello, World!"
        self.myNumber = 0
    }
}
Add a script that reads myNumber from the contract
I think this is correct. I have replaced String with Int and replaced greeting with myNumber
![Ch 2 day 2 script](https://user-images.githubusercontent.com/104719670/166467731-241f7813-b041-4da7-bdf8-b689a3453eb8.png)
import HelloWorld from 0x01

pub fun main(): Int {
    return HelloWorld.myNumber
}
Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.



![Error from TX part of Chap 2 day2](https://user-images.githubusercontent.com/104719670/167037040-c14cc799-a202-4581-88f6-5b61ac509c42.png)

TX SOLVED
![TX for C2 D2 final part](https://user-images.githubusercontent.com/104719670/167224937-8be7d895-0a9c-4811-94c7-c768a8b630f7.png)


import HelloWorld from 0x01

transaction(myNewGreeting: String, updateMyNumber: Int) {

  prepare(signer: AuthAccount) {}

  execute {
    HelloWorld.changeGreeting(newGreeting: myNewGreeting)
  }
}

Chapter 2 Day 3

Q1

![C2 D3 First script](https://user-images.githubusercontent.com/104719670/167294348-9c2e8e23-6e91-454a-aa9c-77ff70ad7dce.png)

Q2

![C2 D3 second script no result to check](https://user-images.githubusercontent.com/104719670/167294351-f00d68f0-f669-48b7-a746-fd46cdf9b9c1.png)


Explain what the force unwrap operator ! does, with an example different from the one I showed you (you can just change the type).

//The force unwrap operator allows the type of data to be identified as optional. For example a String could be mismatched with 
//another String and you could use  it to identify this. So the value could be a String or nil.


//    What the error message means
    
    //I think that it means that the program is not able to access the string because an ? has not been added to the type. Its looking at the account number which is an Int
    
    
//    Why we're getting this error

    // I think its because we have not used an ? and then an unwrap! 


//How to fix it

    //Add in an ! and an ? in the right place.!
    
    [Script fixed maybe](https://user-images.githubusercontent.com/104719670/168178860-0147c0f8-e00b-4edc-82e5-9008131cca84.png)



