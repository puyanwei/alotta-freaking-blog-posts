This post might be a bit more technical then my usual, but I will try and explain things as layman’s as possible. Also to the current or potential Makers this might need a spoiler alert, but don’t worry in true Makers style I wont give you guys the answer lol.

### BANK PROGRAM EZ? NOT SO FAST…

This was the task we were given to do. Once our coach approved our code, we moved onto the next one;

![](https://cdn-images-1.medium.com/max/800/0*RVk5Rv-SpcCTsNRb.png)

You can go to your terminal in a mac, gem install ruby, type in irb and copy and paste this code in if you feel like checking it out…

Ok, lets have a go;

class Bank

  def initialize  
    @transaction\_history = \[\]  
    @balance = 0  
  end

  def deposit(date, credit)  
    @balance += credit  
    transaction = Transaction.new(date, credit, 0, @balance)  
    @transaction\_history.unshift(transaction)  
  end

  def withdrawal(date, debit)  
    @balance -= debit  
    transaction = Transaction.new(date, 0, debit, @balance)  
    @transaction\_history.unshift(transaction)  
  end

  def print\_balance  
    puts 'date || credit || debit || balance'  
    @transaction\_history.each do |log|  
      puts "#{log.date} || #{log.credit} || #{log.debit} || #{log.balance}"  
    end  
  end  
end

class Transaction

  attr\_accessor :date, :credit, :debit, :balance

  def initialize(date, credit, debit, balance)  
    @date = date  
    @credit = credit  
    @debit = debit  
    @balance = balance  
  end  
end

With every new Bank we create, we create an array (essentially a list) called transactions history that will hold our data stored in the Transaction class. Every time a deposit or a withdrawal happens, a new transaction is added to the array with the relevant information.

Our balance is always updated by having the deposit/withdrawal number add or deducting to it.

When we go for the printing of the balance, we look loop through each transaction in our transaction history array, and output all the relevant information.

Ok, so lets call our methods;

![](https://cdn-images-1.medium.com/max/800/0*3l9VNJOoKESdYQmE.gif)

bank = Bank.new  
bank.deposit("10/01/2012", 1000)  
bank.deposit("13/01/2012", 2000)  
bank.withdrawal("14/01/2012", 500)  
bank.print\_balance

pry(main)> bank = Bank.new  
\=> #<Bank:0x007fca05119488  
 @balance=0,  
 @transaction\_history=\[\]>  
bank.deposit("10/01/2012", 1000)  
\=> \[#<Transaction:0x007fca050e9c60  
  @balance=1000,  
  @credit=1000,  
  @date="10/01/2012",  
  @debit=0>\]  
bank.deposit("13/01/2012", 2000)  
\=> \[#<Transaction:0x007fca050787e0  
  @balance=3000,  
  @credit=2000,  
  @date="13/01/2012",  
  @debit=0>,  
bank.withdrawal("14/01/2012", 500)  
\=> \[#<Transaction:0x007fca0612c280  
  @balance=2500,  
  @credit=0,  
  @date="14/01/2012",  
  @debit=500>,

bank.print\_balance  
date || credit || debit || balance  
14/01/2012 || 0 || 500 || 2500  
13/01/2012 || 2000 || 0 || 3000  
10/01/2012 || 1000 || 0 || 1000

Seems like it works, but that’s not enough… this is actually low quality code!

### QUALITY CONTROL

Extra software tools were given for us to try and pass them, to assure high quality code.

There are multiple things wrong with this code, so what are they?

Testing — Well yeah, there is no testing on this code whatsoever. Testing is super important as not only does it help you work out what is wrong with the code, but for refactoring (rearranging the code for improvement) it makes it much less confusing!

The quality of the tests are important too. Do they properly test what you set them out to do? A way of testing if the tests are solid are by either slightly changing them to see if they fail, or just adding things to the code that should make them fail.

_Ruby Testing Tool — _[_RSpec_](http://rspec.info/)

It is also important that the coverage is over 95%. This means that the tests you do, cover 95% or more of the code that is written.

_Coverage Tool — _[_SimpleCov_](https://github.com/colszowka/simplecov)

**Linting** — This is looking at the formatting of the code and to see if it is consistent. This can be anything like the spacing of words, upper or lower casing, or even preferred coding conventions for a particular job of a bit of code. The lint checker Rubocop also has a feature to auto correct fails if its sure it doesn’t effect the function of the code.

_Linter Tool — _[_Rubocop_](https://github.com/bbatsov/rubocop)

Inbalanced Classes — The main problem with the code above is that there are only two classes and that basically all the functionality is in one. It is important to spread of the responsibility of the code into multiple classes, with each class making it clear what its role is.

Having code spread out also makes it better for debugging, and it makes sure that the classes aren’t too reliant on each other, meaning if something broke then it shouldn’t effect to many things.

We used Flog to check our complexity (in terms of the structure), and aimed for a score of no higher then 15 for classes and no higher then 6 for each method.

_Code Structure Assessment Tool — _[_Flog_](https://github.com/seattlerb/flog)

Extras — There are a lot of small things to do as well for good coding practice. Things like;

*   Methods should only have one sole function
*   Avoid Repetition “DRY” (Don’t Repeat Yourself)
*   Naming Conventions — Classes should be nouns, methods as verbs
*   Setting some methods to not be allowed to be accessible by the user, making them “private”

It was also good practice to use Github with quality in mind;

*   Lots of commits!
*   Detailed descriptions on the commits.
*   A detailed Readme file.

In the end, I managed to refactor [my code](https://github.com/puyanwei/bank-tech-test) into 6 classes, linter passing and had 16 passing tests at 100% coverage! It was frustrating at times, but a great exercise none the less to making myself go back and rethink about how my code could be improved. I learned so much last week!

![](https://cdn-images-1.medium.com/max/800/0*sAxgt7LlOR6WV8TD.png)

### THE END IN SIGHT

So we have two weeks left of the course and now I’m doing my final project. My group and I all had an interest to build a desktop app from scratch, and so we have been checking out and learning how to use Spectron. It seems like an amazing framework and has tons of potential for future projects.

More about that next week. I cant believe its nearly over!! I’m gonna be really sad… For now I’ll leave you guys with what should have definitely been our final project, an Augmented Reality Mario remake!