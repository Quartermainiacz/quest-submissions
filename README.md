0xabc975eea144ef24

DAY 1
    #Explain what the Blockchain is in your own words. 
    
    #Blockchain is a database that is shared publicly and anyone can see the data on the blockchain. There is no governing body or any one organisation #dictating what we should or shouldn't do. 
    
    #Explain what a Smart Contract is.
    
    #A smart contract is a kind of rule book for the blockchain.They have to be written and tested carefully(on TestNet) before they are put on MainNet because #otherwise things can go wrong and people can lose a lot of money. Some people do this intentionally to scam people, so knowledge of smart contracts need to be #more widespread so that people dont get scammed. They include a function, some sort of parameter(age?), it stores that parameter and then sends it to the #updated data to the blockchain. With smart contracts there is no middle man so they can be actioned quickly, and they are usually shared with communities so that there is trust and transparency within the project.
    
    #Explain the difference between a script and a transaction.
    
    #A script is a line of code that reads information from a blockchain and it is free.
    
    #A transaction is a paid function call(when data gets changed on a blockchain). On certain blockchains this payment is known as gas and is a complete rip #off!
###########################################################################################################################################################
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
    
    NEED TO REMOVE VARIABLES TO CREATE ERROR -> SEE ADVICE FROM SNOMOBEELS BELOW
    ![Advice from SNOMOBEELS1](https://user-images.githubusercontent.com/104719670/171509135-b9579223-02b1-440d-b719-a1d7715a8a29.png)
    ![Advice from SNOMOBEELS2](https://user-images.githubusercontent.com/104719670/171509138-a75d7c0e-6f76-42ea-84b8-09ec84d3928b.png)




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
  
    // a: can be read
    // b: can be read
    // c: no access
    // d: no access
    
    // publicFunc() can be called here
    }
    //**All of these relate to var not let**//
    LINK TO ACCESS CONTROL ON FLOW DOCS
    https://docs.onflow.org/cadence/language/access-control/
    
C4D1 - Account Storage

    

    Explain what lives inside of an account.
    
    1. A contract or mulitple contracts
    2. Account storage with 3 differnet paths; Storage, Public and Private.

    What is the difference between the /storage/, /public/, and /private/ paths?
    Storage path is where all the data is stored in your account
    Public path is acessible for everyone to see
    Private path is only accessible to the Auth Account(person who owns the account) 
    

    What does .save() do? What does .load() do? What does .borrow() do?
    .save() - Allows us to put resources into storage
    .load() - Allows us to take resources from storage
    .borrow() - Allows us to borrow a reference to the resource from storage

    Explain why we couldn't save something to our account storage inside of a script.
    Because all of the code appears in the prepare section of the transaction.

    Explain why I couldn't save something to your account.
    As you dont have access to my account unless I give it to you.  I would need to sign the transaction.

    Define a contract that returns a resource that has at least 1 field in it. Then, write 2 transactions:
    
    AirPatrolIDEAContract
    
    pub contract AirPatrol {

    pub var totalSupply: UInt64

    pub resource interface IPilot {
        pub let id: UInt64
        pub let name: String
        pub var nickname: String
        pub fun changeNickname(nickname: String)
    }

    pub resource Pilot: IPilot {
        pub let id: UInt64
        pub let name: String
        pub var nickname: String

        init(name: String) {
            self.name = name

            self.nickname = ""

            // Increment the global AirPatrol IDs
            AirPatrol.totalSupply = AirPatrol.totalSupply + 1

            // Set unique AirPatrol ID to the newly incremented totalSupply
            self.id = AirPatrol.totalSupply
        }

        pub fun changeNickname(nickname: String) {
            self.nickname = nickname
        }
    }

    pub fun updateNicknameWithoutInterface() {
        let pilot: @Pilot <- create Pilot(name: "Mitchell")
        pilot.changeNickname(nickname: "Maverick")
        log(pilot.nickname) // "New"

        destroy pilot
    }

    // Restricted
    pub fun updateNicknameInterface() {
      let pilot: @Pilot{IPilot} <- create Pilot(name: "Mitchell")
        pilot.changeNickname(nickname: "Maverick")
        log(pilot.nickname) // "New"

        destroy pilot
    }

    pub fun createPilot(name: String): @Pilot {
    return <- create Pilot(name: name)
  }

    init() {
        self.totalSupply = 0
    }
    

       ** A transaction that first saves the resource to account storage, then loads it out of account storage, logs a field inside the resource, and destroys it.**
       
    import AirPatrol from 0x01

    transaction(name: String) {
    prepare(signer: AuthAccount) {
    // Save the resource to account storage
    signer.save(<- AirPatrol.createPilot(name: name), to: /storage/AirPatrolStorage)

    // Load the resource from the account storage
    let pilot <- signer.load<@AirPatrol.Pilot>(from: /storage/AirPatrolStorage)
                  ?? panic("A `@AirPatrol.Pilot` resource does not exist")

    // Log a field
    log(pilot.name)

    // Destroy the pilot
    destroy pilot
     }

     execute {

     }
    }
        **A transaction that first saves the resource to account storage, then borrows a reference to it, and logs a field inside the resource.**

    import AirPatrol from 0x01

    transaction(name: String) {
    prepare(signer: AuthAccount) {
    // Save the resource to account storage
    signer.save(<- AirPatrol.createPilot(name: name), to: /storage/AirPatrolStorage)

    // Borrow the resource from the account storage
    let pilot = signer.borrow<&AirPatrol.Pilot>(from: /storage/AirPatrolStorage)
                  ?? panic("A `@AirPatrol.Pilot` resource does not exist")

    // Log a field
    log(pilot.name)
    }

    execute {

     }
    }
    Hopefully this is correct took qute a while to get my head around the different syntax. Again I used another users code to start and then put my own spin on it. I think I work better with the whole thing in front of me then I can see the context instead of building it up bit by bit.

C4D2

    

    What does .link() do?
    
    Link allows us to take what is in our storage and make it publicly available(to look at only). It can be used with references, and restrictions can be added        to functions. You must link it to where it is stored.
    
    In your own words (no code), explain how we can use resource interfaces to only expose certain things to the /public/ path.
    
    We can use resource interfaces to expose only certain things (using functions) to the public by using capabilities. They work behind the scenes and only on a public account,     not an AuthAccount. You can use a 'getAcccount' method to access the public account using capabilities.   
    
    Deploy a contract that contains a resource that implements a resource interface. Then, do the following:
    
    pub contract AirPatrol {

    pub var totalSupply: UInt64

    pub resource interface IPilot {
        pub let id: UInt64
        pub let name: String
        pub var nickname: String
        pub fun changeNickname(nickname: String)
    }

    pub resource Pilot: IPilot {
        pub let id: UInt64
        pub let name: String
        pub var nickname: String

        init(name: String) {
            self.name = name

            self.nickname = ""

            // Increment the global AirPatrol IDs
            AirPatrol.totalSupply = AirPatrol.totalSupply + 1

            // Set unique AirPatrol ID to the newly incremented totalSupply
            self.id = AirPatrol.totalSupply
        }

        pub fun changeNickname(nickname: String) {
            self.nickname = nickname
        }
    }

    pub fun updateNicknameWithoutInterface() {
        let pilot: @Pilot <- create Pilot(name: "Mitchell")
        pilot.changeNickname(nickname: "Maverick")
        log(pilot.nickname) // "New"

        destroy pilot
    }

    // Restricted
    pub fun updateNicknameInterface() {
      let pilot: @Pilot{IPilot} <- create Pilot(name: "Mitchell")
        pilot.changeNickname(nickname: "Maverick")
        log(pilot.nickname) // "New"

        destroy pilot
    }

    pub fun createPilot(name: String): @Pilot {
    return <- create Pilot(name: name)
    }

    init() {
        self.totalSupply = 0
    }
    }    

    

        In a transaction, save the resource to storage and link it to the public with the restrictive interface.
    import AirPatrol from 0x01

    transaction(name: String) {

    prepare(signer: AuthAccount) {
    
    // Save the resource to account storage
    signer.save(<- AirPatrol.createPilot(name: name), to: /storage/AirPatrolStorage)

    // Link the resource from the account storage
    signer.link<&AirPatrol.Pilot{AirPatrol.IPilot}>(/public/AirPatrolStorage, target: /storage/AirPatrolStorage)
                  ?? panic("A `@AirPatrol.Pilot` resource does not exist")

     }

     execute {

     }
    }
        Run a script that tries to access a non-exposed field in the resource interface, and see the error pop up.
    
    import AirPatrol from 0x01

    pub fun main(address: Address): String {

    let publicCapability: Capability<&AirPatrol.Pilot{AirPatrol.IPilot}> =
    getAccount(address).getCapability<&AirPatrol.Pilot{AirPatrol.IPilot}>(/public/AirPatrolStorage)

    let pilot: &AirPatrol.Pilot{AirPatrol.IPilot} = publicCapability.borrow() ?? panic("The capability doesn't exist or you did not specify the right type when     you got the capability.")

    return pilot.name // ERROR: member of restricted type is not accessible: name
    }
    
    
        Run the script and access something you CAN read from. Return it from the script.
        
    import AirPatrol from 0x01

    pub fun main(address: Address): UInt64 {

    let publicCapability: Capability<&AirPatrol.Pilot{AirPatrol.IPilot}> =
    getAccount(address).getCapability<&AirPatrol.Pilot{AirPatrol.IPilot}>(/public/AirPatrolStorage)

    let pilot: &AirPatrol.Pilot{AirPatrol.IPilot} = publicCapability.borrow() ?? panic("The capability doesn't exist or you did not specify the right type when     you got the capability.")

    return pilot.id
    }
C4D3 - My First NFT Contract!!!!!!!! 

pub contract AirPatrol  {

  pub var totalSupply: UInt64

  pub resource NFT  {
    pub let id: UInt64

    init() {
      self.id = AirPatrol.totalSupply
      AirPatrol.totalSupply = AirPatrol.totalSupply + (1 as UInt64)
    }
}
 // Only exposes `deposit` and `getIDs`
  pub resource interface CollectionPublic {
    pub fun deposit(token: @NFT)
    pub fun getIDs(): [UInt64]
  }

  // `Collection` implements `CollectionPublic` now
  pub resource Collection: CollectionPublic {
    pub var ownedNFTs: @{UInt64: NFT}

//Allows us to deposit an NFT to the collection

    pub fun deposit(token: @NFT) {
      self.ownedNFTs[token.id] <-! token
    }
//Allows us to withdraw an NFT from the collection, if the nft does not exist it panics.
    pub fun withdraw(withdrawID: UInt64): @NFT {
      let nft <-  self.ownedNFTs.remove(key: withdrawID)
            ?? panic("This NFT does not exist in this Collection.")
      return <- nft
    }  
//Returns an array of all the NFT ids in our collection
pub fun getIDs(): [UInt64] {
    return self.ownedNFTs.keys
}

    init()  {
      self.ownedNFTs <-{}
}

  destroy() {
    destroy self.ownedNFTs
    }

}

  pub fun createNFT(): @NFT {
    return <- create NFT()
}
  pub fun createEmptyCollection(): @Collection {
    return <- create Collection()
  }
init()  {
    self.totalSupply = 0
  }

}
#######################
Restrict hat people can see
#######################
import AirPatrol from 0x01

transaction() {
  prepare(signer: AuthAccount) {
    // Store a `AirPatrol.Collection` in our account storage.
    signer.save(<- AirPatrol.createEmptyCollection(), to: /storage/MyCollection)
    
    // NOTE: We expose `&AirPatrol.Collection{AirPatrol.CollectionPublic}`, which 
    // only contains `deposit` and `getIDs`.
    signer.link<&AirPatrol.Collection{AirPatrol.CollectionPublic}>(/public/MyCollection, target: /storage/MyCollection)
  }
}

#######################
Deposit and withdraw NFT
#######################
import AirPatrol from 0x01
transaction() {
  prepare(signer: AuthAccount) {
    // Get a reference to our `AiPatrol.Collection`
    let collection = signer.borrow<&AirPatrol.Collection>(from: /storage/MyCollection)
                      ?? panic("The recipient does not have a Collection.")
    
    // deposits an `NFT` to our Collection
    collection.deposit(token: <- AirPatrol.createNFT())

    log(collection.getIDs()) // [2353]

    // withdraw the `NFT` from our Collection
    let nft <- collection.withdraw(withdrawID: 2353) // We get this number from the ids array above
  
    log(collection.getIDs()) // []

    destroy nft
  }
}

####################################
Deposit NFT to someone elses account
####################################
import AirPatrol from 0x01
transaction(recipient: Address) {

  prepare(otherPerson: AuthAccount) {
    // Get a reference to the `recipient`s public Collection
    let recipientsCollection = getAccount(recipient).getCapability(/public/MyCollection)
                                  .borrow<&AirPatrol.Collection{AirPatrol.CollectionPublic}>()
                                  ?? panic("The recipient does not have a Collection.")
    
    // deposits an `NFT` to our Collection
    recipientsCollection.deposit(token: <- AirPatrol.createNFT())
  }

}

############################
Script to read NFTs in acount
#############################


import AirPatrol from 0x01
pub fun main(address: Address): [UInt64] {
let publicCollection = getAccount(address).getCapability(/public/MyCollection)
              .borrow<&AirPatrol.Collection{AirPatrol.CollectionPublic}>()
              ?? panic("The address does not have a Collection.")
  
  return publicCollection.getIDs() // [2353]
}





###################################################################################
Quest answers
###################################################################################

    Why did we add a Collection to this contract? List the two main reasons.
    
   #### 1. It stores everything in one place
    2. It makes it easier to manage
    3. It makes it easier to restrict access

    What do you have to do if you have resources "nested" inside of another resource? ("Nested resources")

   ####When you have nested resources you must define a destroy() function so the nested resource either gets destroyed or moved when the parent resource is destroyed.

    Brainstorm some extra things we may want to add to this contract. Think about what might be problematic with this contract and how we could fix it.

        Idea #1: Do we really want everyone to be able to mint an NFT? 🤔.
        
   #### Perhaps it could be available to everyone depnds on how limited you want the collection to be ?
        You could limit who could mint by checking the wallet addresses of those who have be pre-approved on some sort of allowlist that could be referred to in the form of a csv?

        Idea #2: If we want to read information about our NFTs inside our Collection, right now we have to take it out of the Collection to do so. Is this good?
        I dont think it is good, as the nft could be lost somehow? Perhaps we could refer to the collection somehow using link or borrow?
        
        END OF DAY 3
        
C4 D4 - NEED TO COMPLETE

########################################################################Adding Comments to contract#######################################################

pub contract CryptoPoops {
//contract name 
pub var totalSupply: UInt64
//total suply of nft

// This is an NFT resource that contains a name,
// favouriteFood, and luckyNumber
pub resource NFT {
pub let id: UInt64

    pub let name: String
    pub let favouriteFood: String
    pub let luckyNumber: Int
//this gives each variable a type, string or int

    init(_name: String, _favouriteFood: String, _luckyNumber: Int) {
      self.id = self.uuid
      self.name = _name
      self.favouriteFood = _favouriteFood
      self.luckyNumber = _luckyNumber
    }
  }
//this initialises the information within the contract
  // This is a resource interface that allows us to look at, borrow and deposit to a collection 
  pub resource interface CollectionPublic {
    pub fun deposit(token: @NFT)
    pub fun getIDs(): [UInt64]
    pub fun borrowNFT(id: UInt64): &NFT
  }
    //
  pub resource Collection: CollectionPublic {
    pub var ownedNFTs: @{UInt64: NFT}
//this creates a public colection where the nft resources where the NFT can be viewed
    pub fun deposit(token: @NFT) {
    //this depsoits the nft within the collection
      self.ownedNFTs[token.id] <-! token
    }

    pub fun withdraw(withdrawID: UInt64): @NFT {
    //this allows for the NFT to be withdrawn from the collection
    let nft <- self.ownedNFTs.remove(key: withdrawID) 
              ?? panic("This NFT does not exist in this Collection.")
      return <- nft
    }

    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    //this allows you to get the ids from all of your nfts
    }

    pub fun borrowNFT(id: UInt64): &NFT {
      return (&self.ownedNFTs[id] as &NFT?)!
    //this allows you to borrow the nft from the collection storage}

    init() {
      self.ownedNFTs <- {}
    }

    destroy() {
      destroy self.ownedNFTs
    }//this destroys the NFT from the original collection
  }

  pub fun createEmptyCollection(): @Collection {
    return <- create Collection()
  }//this creates a empty collection to mint to

  pub resource Minter {
//creation of resource called minter that will help us create nfts with ids and store them correctly.
    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

    pub fun createMinter(): @Minter {
      return <- create Minter()
    }
//creation of minter
  }

  init() {
    self.totalSupply = 0
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}

