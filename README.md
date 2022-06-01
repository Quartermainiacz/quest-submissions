0xabc975eea144ef24

DAY 1
    #Explain what the Blockchain is in your own words. 
    
    #Blockchain is a database that is shared publicly and anyone can see the data on the blockchain. There is no governing body or any one organisation #dictating what we should or shouldn't do. 
    
    #Explain what a Smart Contract is.
    
    #A smart contract is a kind of rule book for the blockchain.They have to be written and tested carefully(on TestNet) before they are put on MainNet because #otherwise things can go wrong and people can lose a lot of money. Some people do this intentionally to scam people, so knowledge of smart contracts need to be #more widespread so that people dont get scammed. They include a function, some sort of parameter(age?), it stores that parameter and then sends it to the #updated data to the blockchain. With smart contracts there is no middle man so they can be actioned quickly, and they are usually shared with communities so that there is trust and transparency within the project.
    
    #Explain the difference between a script and a transaction.
    
    #A script is a line of code that reads information from a blockchain and it is free.
    
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
    
C2 D4

![C2 D4 First Task](https://user-images.githubusercontent.com/104719670/168183062-12491e37-0b75-46e2-abb3-7b4713b99b32.png)
![C2 D4 Script wrong](https://user-images.githubusercontent.com/104719670/168183063-c7b5906a-55ef-481d-bf1d-855d37e31d1b.png)
![C2 D4 TX](https://user-images.githubusercontent.com/104719670/168183064-caf126b4-9155-4aa5-9438-641458efb702.png)

I dont seem to be able to get the script to run but I think The contract is correct and the transaction as I am able to read the changes in the output window.

C3 D1

//Notes for future for Resources

    //1.You can only make a new resource with the create keyword. The create keyword can only ever be used inside the contract. This means you, as the developer, can control when they are made. This is not true for structs, since structs can be created outside the contract.
    2.You have to use the @ symbol in front of a resource's type, like so: @Greeting.
    3.You use the <- symbol to move a resource around.
    4.You use the destroy keyword to, well, destroy a resource.
    


    In words, list 3 reasons why structs are different from resources.
    
    Resources are more secure than structs
    Resources cannot be copied
    Resources cannot be lost or over-written
    Resources cannot be created anytime you want
    

    Describe a situation where a resource might be better to use than a struct.
    Where you are moving an NFT from one user to another. So I think this would work on a marketplace like BloctoBay.
    
    What is the keyword to make a new resource?
    create
    
    Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?
    I think it could be created in a tx because this would be how a marketplace swaps an NFT from one user to another.
    
    What is the type of the resource below?
    An empty resource named Jacob??
    
    4 Errors are:
    pub fun createJacob(): Jacob { // there is 1 here
    
    1.No @ before Jacob
    
        let myJacob = Jacob() // there are 2 here
        
    2.Use of  = instead of moving operator <-
    3.No create in front of Jacob
        
        
        return myJacob // there is 1 here
       
    4.Didnt use moving operator <- between return and myJacob
    
C3 D2
![Resources and Arrays](https://user-images.githubusercontent.com/104719670/168466624-0b334ebf-cf3c-4fa1-a7d0-9e046679db73.png)

![C3D2 1st](https://user-images.githubusercontent.com/104719670/171280002-82a080ea-bac2-415c-a05d-ab50eb8cbfae.png)
![C3D2 2nd](https://user-images.githubusercontent.com/104719670/171280009-f9cafff6-070a-4806-b14d-3316f42b9d92.png)

Still getting an error on the last one. I admit I used another users code to help me get started but found it had quite a few errors.(Not sure if it was playground playing up of not) Managed to fix most of them and the screenshots are the result.

The error was in the last part about removing a resource from a Dict. 

C3 D3



    Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.
    ![C3D3 1st](https://user-images.githubusercontent.com/104719670/171283572-09839047-ba96-4ecf-a170-483286c6fcfd.png)

    Create a script that reads information from that resource using the reference from the function you defined in part 1.
    ![C3D3 2nd](https://user-images.githubusercontent.com/104719670/171283597-57b54f13-3aa2-4dab-9da0-ddda5210a631.png)
    ![C3D3 3rd](https://user-images.githubusercontent.com/104719670/171283609-5b4cb1be-40e9-47c6-b47c-d466a92c8be3.png)

    Explain, in your own words, why references can be useful in Cadence.
    References are useful because we dont have to move resources around and you can still get the information you need. References must be type cast or an error will pop up. 
    
C3D4 - Notes then answers

   How to initially set up a Resource Interface
   
   pub contract Stuff {

    pub resource interface ITest {
      pub let name: String
    }

    // It's good now :)
    pub resource Test: ITest {
      pub let name: String
      init() {
        self.name = "Spongebob" // anyone else like Spongebob?
      }
    }
}

    How to restrict access to Resource interfaces and functions
    
    pub contract Stuff {

    pub resource interface ITest {
      pub var name: String
      pub var number: Int
      pub fun updateNumber(newNumber: Int): Int
    }

    pub resource Test: ITest {
      pub var name: String
      pub var number: Int

      pub fun updateNumber(newNumber: Int): Int {
        self.number = newNumber
        return self.number // returns the new number
      }

      init() {
        self.name = "Spongebob"
        self.number = 1
      }
    }

    pub fun noInterface() {
      let test: @Test <- create Test()
      test.updateNumber(newNumber: 5)
      log(test.number) // 5

      destroy test
    }

    // Works totally fine now! :D
    pub fun yesInterface() {
      let test: @Test{ITest} <- create Test()
      let newNumber = test.updateNumber(newNumber: 5)
      log(newNumber) // 5

      destroy test
    }
}

ANSWERS

    Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content)
    
    Resource interfaces can be used to make resources implement certain things after specific requirements have been met. They can also be used to restrict access to things like functions only to certain people.(I think this is like when a NBA Topshot acccount only allows you to sell and buy moments??)

    Define your own contract. Make your own resource interface and a resource that implements the interface. Create 2 functions. In the 1st function, show an example of not restricting the type of the resource and accessing its content. In the 2nd function, show an example of restricting the type of the resource and NOT being able to access its content.
    
    ![C3D4](https://user-images.githubusercontent.com/104719670/171290228-cb66eecc-6c52-4db6-9cdc-e979f3cbd664.png)
    
    Used the example in themain. I am able to identify which things I can change but I am starting to get a litle lost around what each section does.


    How would we fix this code?

    pub contract Stuff {

    pub struct interface ITest {
      pub var greeting: String
      pub var favouriteFruit: String
      pub fun changeGreeting(newGreeting: String): String // Added to make the function accessible
    }

    // ERROR FIXED
    pub struct Test: ITest {
      pub var greeting: String
      pub var favouriteFruit: String // Add this to work with the ITest interface

      pub fun changeGreeting(newGreeting: String): String {
        self.greeting = newGreeting
        return self.greeting // returns the new greeting
      }

      init() {
        self.greeting = "WASSUP"
        self.favouriteFruit = "Raspberries" 
      }
    }

    pub fun fixThis() {
      let test: Test{ITest} = Test()
      let newGreeting = test.changeGreeting(newGreeting: "Bonjour!") // ERROR FIXED
      log(newGreeting)
    }
}

C3D5

    access(all) contract SomeContract {
    pub var testStruct: SomeStruct

    pub struct SomeStruct {

        //
        // 4 Variables
        //

        pub(set) var a: String

        pub var b: String

        access(contract) var c: String

        access(self) var d: String

        //
        // 3 Functions
        //

        pub fun publicFunc() {}

        access(contract) fun contractFunc() {}

        access(self) fun privateFunc() {}


        pub fun structFunc() {
            /**************/
            /*** AREA 1 ***/
            /**************/
            
            // a:  can be read and written
            // b:  can be read and written
            // c:  can be read and written
            // d:  can be read and written
            
            // publicFunc() can be called here
            // contractFunc() can be called here
            // privateFunc() can be called here
        }

        init() {
            self.a = "a"
            self.b = "b"
            self.c = "c"
            self.d = "d"
        }
    }

    pub resource SomeResource {
        pub var e: Int

        pub fun resourceFunc() {
            /**************/
            /*** AREA 2 ***/
            /**************/
            
            // a: can be read and written
            // b: only read
            // c: only read
            // d: no access
            
            // publicFunc() can be called here
            // contractFunc() can be called here
        }

        init() {
            self.e = 17
        }
    }

    pub fun createSomeResource(): @SomeResource {
        return <- create SomeResource()
    }

    pub fun questsAreFun() {
        /**************/
        /*** AREA 3 ****/
        /**************/
        
        // a: can be read and written
        // b: only read
        // c: only read
        // d: no access
        
        // publicFunc() can be called here
        // contractFunc() can be called here
    }

    init() {
        self.testStruct = SomeStruct()
    }
}

SCRIPT

import SomeContract from 0x01

pub fun main() {
  /**************/
  /*** AREA 4 ***/
  /**************/
  
    // a: can be read // write in a transaction
    // b: can be read
    // c: no access
    // d: no access
    
    // publicFunc() can be called here
}

LINK TO ACCESS CONTROL ON FLOW DOCS
https://docs.onflow.org/cadence/language/access-control/
