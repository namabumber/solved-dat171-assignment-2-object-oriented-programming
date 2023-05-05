Download Link: https://assignmentchef.com/product/solved-dat171-assignment-2-object-oriented-programming
<br>
This assignment will focus on Object-Oriented Programming (OOP). The objective is to write a general library for standard playing cards (52 card decks). This library will be used in assignment 3 to build a simple Texas Hold’em poker game.

The OOP-part of the assignment will try out the possibilities for:

<ol>

 <li>Writing classes</li>

 <li>Using inheritance and abstract functions</li>

 <li>Operator overloading</li>

 <li>String conversion methods</li>

</ol>

<strong>Please read through the whole assignment before you start working!</strong>

The task is set up as a top-down design, where the top-level functions are written before the core functionality is implemented. Insert placeholders as you go along!

You are not required to follow the provided task order. On the next page are specifications of what is required of your library.

<strong>See the requirements below.</strong>

A suggested procedure for tackling this assignment is detailed in these steps, though the order does not really matter:

<ol>

 <li>Create the card classes</li>

 <li>Create a basic hand class (skip best_poker_hand method for now)</li>

 <li>Create a class to represent the deck</li>

 <li>Create a class to represent poker hands (with poker hand we mean for example a pair, flush or straight)</li>

 <li>Implement best_poker_hand which computes the best poker hand from <em><sub>an arbitrary set of cards</sub></em></li>

</ol>

In addition to creating the library itself, you will generate a manual from your written docstrings, and write tests to ensure functionality does not regress as you keep making changes to the code. <em><sub>It is best to work on documentation </sub>and testing continuously while you work on the assignment, not as a last step. </em>Guides on documentation and testing are provided later in this document.

Note that you do not have to create a playable game in this assignment but feel free to try if you want to. It can be a very simple game where you make up the rules for yourself.

Optional step: Create a class to represent a Player for a Texas Hold’em poker game (e.g. a Hand, name and betting money + associated methods). <em>This question overlaps with the next assignment, where such a Player class will be put</em>

<em>into use.</em>

<h1>Requirements</h1>

The library must be called “cardlib.py” and should contain classes with associated methods and functions that are helpful for creating many types of card games. In particular, it must contain <strong><em><sub>classes </sub></em></strong>that represent:

<ol>

 <li>The playing cards: The classes listed below <strong><sub>must </sub></strong>inherit from an abstract base class PlayingCard. They must be comparable with the &lt; and == operators, and a method get_value() must be overloaded in each subclass.</li>

</ol>

The following constructors <strong><sub>must </sub></strong>exist:

<ol>

 <li>NumberedCard(value: int, suit: Suit)</li>

 <li>JackCard(suit: Suit)</li>

 <li>QueenCard(suit: Suit)</li>

 <li>KingCard(suit: Suit)</li>

 <li>AceCard(suit: Suit)</li>

</ol>

Implement &lt; so that it gives a strict, sensible ordering, but you will have to decide what to do with Aces and suits yourself (hint: look at how tuples handle &lt;). The method get_value is intended to help you practice implementing an abstract method, i.e. it should be included even if the need isn’t obvious for this simple class.

<ol start="2">

 <li>The class representing the suit must be named Suit, with the suits named Clubs, Diamonds, Hearts and Spades. The Suit class must be of an enum type.</li>

 <li>A class representing the hand, Hand, which must have methods for

  <ul>

   <li>adding a new card</li>

   <li>dropping several cards based on an index list</li>

   <li>sorting the cards</li>

  </ul></li>

</ol>

There must also be a method best_poker_hand(self, cards=[]) which computes the best hand out of the cards in the hand and cards in the input argument.

The best_poker_hand method returns a PokerHand object. It must be able to handle a total of more than 5 cards (as is the case in Texas Hold ’em). See <a href="https://en.wikipedia.org/wiki/List_of_poker_hands"><em>Wikipedia List of poker hands</em></a>

<ol start="4">

 <li>The deck: The class StandardDeck() must create a full deck of (52) cards. There must be functions for shuffling and taking the top card (which removes the card from the deck).</li>

 <li>The poker hand (for a lack of a better name): A PokerHand must contain a hand type (high card, one pair, two pair, three of a kind, straight, flush, full house, four of a kind, straight flush) and the highest value(s). The PokerHand must overload the &lt; operator to be able to compare which PokerHand is valued highest based on the hand type and value(s) of the cards in the best hand.</li>

 <li>Testing code for most of the functions you have written (see below for tutorial). A sample testing code is available in Canvas. Your code should pass these tests and in addition, you must <em><sub>at least </sub></em>add tests for:

  <ul>

   <li>More card types and their methods</li>

   <li>More hand methods</li>

   <li>Further testing the deck and its methods</li>

   <li>Card combinations giving the different poker hands</li>

   <li>Comparison between different poker-hands</li>

   <li>Comparison between hands with card combinations giving the same poker hand, but different card values for both the cards making up the poker hand (for example 2 kings in a pair of kings) and the remaining 3 cards</li>

  </ul></li>

 <li>HTML-documentation for everything above generated using Sphinx (see below for tutorial). This documentation must include documentation of <em>all the required and classes and methods</em>, including a brief description, input parameters, and return values. Also, include documentation for major classes/methods you add.</li>

</ol>

You are free to introduce additional methods as you see fit. Simple types, like the Suit and the type of poker hand, <strong>must </strong>be represented by an Enum type, not raw integers or strings. All classes should be printable in a nice way. Hint: Unicode characters can be used: <a href="https://en.wikipedia.org/wiki/Playing_cards_in_Unicode"><em><sub>Wikipedia</sub></em></a><a href="https://en.wikipedia.org/wiki/Playing_cards_in_Unicode">.</a>

You should hand in <strong><sub>a .zip file </sub></strong>with your library, your tests, and your manual (both the generated manual and the source files needed to run Sphinx to generate the output). Try to avoid non-essential/scrap files in the zip file.

<h1>Appendix A: Testing guide</h1>

As the codebase you (and your collaborators) are working on becomes bigger, automatic testing becomes more important. As you make changes, if there are no tests, it is easy that things that previously worked stops working.

In this assignment, you should create a set of tests that can be run automatically and report back if there are any errors. This is easier than it might sound due to powerful testing toolkits like <a href="https://docs.pytest.org/"><em><sub>pytest</sub></em></a> that comes with Anaconda and is integrated into PyCharm.

Below are a few steps to help you get started.

<ul>

 <li>Create a new folder in your project called “test”.</li>

 <li>Create a Python file in the new folder, call it for example “test_cardlib.py”</li>

 <li>To start, put the following in the file import pytest</li>

</ul>

<strong>def </strong>test_math():

<strong>assert </strong>1 + 1 == 2 <strong>assert </strong>2 * 2 + 3 == 7

<em># It is important to also test strange inputs,</em>

<em># like dividing what zero and see that good exceptions are thrown. # What happens if you try to create a card with a numerical value 0 or -1? </em><strong>with </strong>pytest.raises(ZeroDivisionError):

1 / 0

<ul>

 <li>To run the tests, right-click the test folder and choose “Run pytest in test”. You should get the output that it worked. (If you don’t find “Run pytest in test” in the menu, please go to Settings -&gt; Tools -&gt; Python Integrated Tools and make sure Default test runner is set to <em><sub>pytest</sub></em>.)</li>

 <li>Try to make a test fail (by asserting 1 == 2 for example) and see what happens.</li>

 <li>For the computer assignment, we want most methods you implement to have a test. Be evil towards yourself! Try to break your code.</li>

 <li>Add your own tests as you progress with your card library.</li>

 <li>There are other testing tools, like nose, nose2, unittest, unittest2, which basically achieve the same thing.</li>

</ul>

<h1>Appendix B: Documentation guide</h1>

In addition to the normal documentation of the code, you must also generate a HTML (or PDF) manual for the API of your library, using the tool <a href="https://www.sphinx-doc.org/en/stable/"><em><sub>Sphinx</sub></em></a><a href="https://www.sphinx-doc.org/en/stable/">.</a> This section will give a short tutorial on how to generate such a manual from within PyCharm.

Start by going to Tools -&gt; Sphinx Quickstart (you might need to install the Sphinx package). The first time you run this in a project, it will ask for a working directory. For this project, choose “[project directory]/doc” by creating a new folder.

Next, Sphinx Quickstart will ask some questions in a terminal. Most of them can be answered with the default answer (by pressing Enter), but the following questions should be answered like this:

&gt; Separate source and build directories (y/n) [n]: y

&gt; autodoc: automatically insert docstrings from modules (y/n) [n]: y If you do not get the second question, please go to doc/source/conf.py, find the lines extensions = [

] and change them to read:

extensions = [‘sphinx.ext.autodoc’]

We now need to tell Sphinx what to document. Here we will do the simplest possible and just ask Sphinx to generate documentation for the whole module. Go to doc/source/index.rst and enter:

.. automodule:: &lt;your module name&gt; :members:

:show-inheritance:

Feel free to add some introduction, examples, whatever.

This document uses the restructured text format, see <a href="https://www.sphinx-doc.org/en/stable/rest.html"><em>http://www.sphinx-doc.org/en/stable/rest.html</em></a><a href="https://www.sphinx-doc.org/en/stable/rest.html">.</a>

Now to actually creating the manual. Create a new run configuration by going to Run -&gt; Edit configuration.

Press the + and chose Python docs -&gt; Sphinx task.

Give the task a name and enter the paths for the input (source) and output (build) inside the doc folder. Here you can choose if you want to generate HTML or PDF (or many other formats) for the documentation. The easiest is HTML but if you have latex installed, feel free to try the PDF version.

Finally, go to Run -&gt; Run… and run the Sphinx task to generate the documentation.

To view the generated documentation, open the doc/build/index.html file in a web browser. This can be done by finding the file in the PyCharm file tree, right-clicking, and choosing Open in Browser.