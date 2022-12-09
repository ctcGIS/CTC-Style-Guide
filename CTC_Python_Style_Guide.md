<div id="top"></div>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
[![Forks][forks-shield]][forks-url]
-->


<!-- TITLE -->
<br />
<h1 align="center">CTC Python Style Guide</h1>
  <p align="center">
    A set of code style and formatting guidelines for python projects created by the CTC R&D team.
    <br />
    Includes pythonic best practices, idioms, conventions, structure, and symbology. 
    <br />
    <br />
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#zen-of-python">Zen of Python</a></li>
    <li>
      <a href="#best-practices">Best Practices</a>
      <ul>
        <li><a href="#explicit-code">Explicit code</a></li>
        <li><a href="#one-statement-per-line">One statement per line</a></li>
        <li><a href="#function-arguments">Function Arguments</a></li>
        <li><a href="#returning-values">Returning values</a></li>
      </ul>
    </li>
    <li>
      <a href="#idiomatic-python">Idiomatic Python</a>
      <ul>
        <li><a href="#unpacking">Unpacking</a></li>
        <li><a href="#create-ignored-variable">Create an ignored variable</a></li>
        <li><a href="#list-construction">List Construction</a></li>
        <li><a href="#searching-for-item-in-collection">Searching for an item in a collection</a></li>
      </ul>
    </li>
    <li>
      <a href="#conventions">Conventions</a>
      <ul>
        <li><a href="#check-if-variable-equals-constant">Check if a variable equals a constant</a></li>
        <li><a href="#access-dictionary-element">Access a Dictionary Element</a></li>
        <li><a href="#list-usage">List Usage</a></li>
        <li><a href="#read-from-file">Read from a file</a></li>
        <li><a href="#line-continuations">Line continuations</a></li>
      </ul>
    </li>
    <li>
      <a href="#pep-8">PEP 8</a>
      <ul>
        <li><a href="#personal-preference-deviations">Personal preference deviations</a></li>
      </ul>
    </li>
    <li>
      <a href="#structure-and-formatting">Structure and Formatting</a>
      <ul>
        <li><a href="#code-map">Code map</a></li>
        <li><a href="#we-are-all-responsible-users">We are all responsible users</a></li>
        <li><a href="#symbology">Symbology</a></li>
      </ul>
    </li>
  </ol>
</details>


Zen of Python
Best Practices
  Explicit code
  One statement per line
  Function arguments
    Positional arguments
    Keyword arguments
    Arbitrary argument list
    Arbitrary keyword argument dictionary
  Returning values
Idiomatic Python - Writing Pythonic code
  Unpacking
  Create an ignored variable
  List construction
    Create a length-N list of the same thing
    Create a length-N list of lists
    Create a string from a list
  Searching for an item in a collection
Conventions
  Check if a variable equals a constant
  Access a Dictionary Element
  List Usage
    Short Ways to Manipulate Lists
    Filtering a list
    Possible side effects of modifying the original list
    Modifying the values in a list
  Read From a File
  Line Continuations
PEP 8
  Personal preference deviations
Structure and Formatting
  Code Map
  We are all responsible users
  Symbology


<!-- ZEN OF PYTHON -->
<div class="section" id="zen-of-python">
<h2>Zen of Python<a class="headerlink" href="#zen-of-python" title="Permalink to this headline">¶</a></h2>
<p>Also known as <span class="target" id="index-1"></span><a class="pep reference external" href="https://www.python.org/dev/peps/pep-0020"><strong>PEP 20</strong></a>, the guiding principles for Python’s design. Long time Pythoneer Tim Peters succinctly channels the BDFL Guido van Rossum’s guiding principles for Python’s design into 20 aphorisms, only 19 of which have been written down.</p>
<div class="highlight-pycon notranslate"><div class="highlight"><pre>
<span class="go">Beautiful is better than ugly.</span>
<span class="go">Explicit is better than implicit.</span>
<span class="go">Simple is better than complex.</span>
<span class="go">Complex is better than complicated.</span>
<span class="go">Flat is better than nested.</span>
<span class="go">Sparse is better than dense.</span>
<span class="go">Readability counts.</span>
<span class="go">Special cases aren't special enough to break the rules.</span>
<span class="go">Although practicality beats purity.</span>
<span class="go">Errors should never pass silently.</span>
<span class="go">Unless explicitly silenced.</span>
<span class="go">In the face of ambiguity, refuse the temptation to guess.</span>
<span class="go">There should be one-- and preferably only one --obvious way to do it.</span>
<span class="go">Although that way may not be obvious at first unless you're Dutch.</span>
<span class="go">Now is better than never.</span>
<span class="go">Although never is often better than *right* now.</span>
<span class="go">If the implementation is hard to explain, it's a bad idea.</span>
<span class="go">If the implementation is easy to explain, it may be a good idea.</span>
<span class="go">Namespaces are one honking great idea -- let's do more of those!</span>
</pre></div>
</div>



### Examples

<!-- BEAUTIFUL IS BETTER THAN UGLY -->
<details>
  <summary>Beautiful is better than ugly</summary>

  ```python
   Bad
  ‾‾‾‾‾
  def LongCamelCaseFuncNameDoSomeStuff(arg1, arg2, arg3, arg4, arg5):
    if (arg1 | arg2):
        return 1;
    elif (arg4 > arg5):
        return 2;
    else:
        return arg3;
    localVar = map(lambda x,y,z,a,b,c: x+y+z+a+b+c, [1], [2], [3], [4], [5], [6]);
    return localVar


   Good 
  ‾‾‾‾‾‾
  def define_time(length, velocity):
    return length / velocity if velocity else 0

  def calculate_time_for_batch(lengths_array, velocities_array):
      time_array = map(
          define_time,
          lengths_array,
          velocities_array
      )
      return time_array if sum(time_array) else []
  ```
</details>



<!-- EXPLICIT IS BETTER THAN IMPLICIT -->
<details>
  <summary>Explicit is better than implicit</summary>

  ```python
   Bad
  ‾‾‾‾‾
  def main_function_of_program(argument_first, argument_second):
    result_first = argument_first + argument_second
    results_in_general = []
    if result_first > 0:
        results_in_general.append(result_first)
    else:
        results_in_general.append(0)
    another_action = argument_first * argument_second
    if another_action > results_in_general[0]:
        results_in_general.append(another_action)
    else:
        results_in_general.append(0)
    sum_of_results = 0
    for value in results_in_general:
        sum_of_results += value
    return sum_of_results


   Good 
  ‾‾‾‾‾‾
  def get_sum_of_values_in_two_arrays(array_a, array_b):
    return sum(array_a) + sum(array_b)

  def create_integers_array_from_string(string):
      integers_array = []
      for char in string:
          if char.isdigit():
              integers_array.append(int(char))
      return integers_array

  def strings_digits_sum(string_a, string_b):
      int_array_a = create_integers_array_from_string(string_a)
      int_array_b = create_integers_array_from_string(string_b)
      sum_of_int_a_b = get_sum_of_values_two_arrays(
          int_array_a, int_array_b
      )
      print(sum_of_int_a_b)

  if __name__ == "__main__":
      strings_digits_sum("hello123", "222goodbye")  # 12
      strings_digits_sum("abc1", "def22")  # 5
      strings_digits_sum("abc", "abc")  # 0
  ```
</details>



<!-- SIMPLE IS BETTER THAN COMPLEX -->
<details>
  <summary>Simple is better than complex</summary>

  ```python
   Bad
  ‾‾‾‾‾
  def define_how_many_letters_are_digits(string):
    alphabet = "abcdefghijklmnopqrstuvwxyz"
    digits = "0123456789"
    count_of_digits = 0
    for char in string:
        char_is_letter = None
        if char.lower() in alphabet:
            char_is_letter = True
        elif char in digits:
            char_is_letter = False
        if isinstance(char_is_letter, bool):
            if not char_is_letter:
                count_of_digits += 1
    return count_of_digits


   Good 
  ‾‾‾‾‾‾
  # example 1 via comprehension
  def define_how_many_letters_are_digits_1(string):
      return len([1 for char in string if char.isdigit()])

  # example 2 classic for loop
  def define_how_many_letters_are_digits_2(string):
      count_of_digits = 0
      for char in string:
          if char.isdigit():
              count_of_digits += 1
      return count_of_digits
  ```
</details>



<!-- COMPLEX IS BETTER THAN COMPLICATED -->
<details>
  <summary>Complex is better than complicated</summary>

  ```python
   Bad
  ‾‾‾‾‾
  def dot_product(list_a, list_b):
    list_of_products = []
    for a, b in zip(list_a, list_b):
        list_of_products.append(a * b)
    sum_of_list = 0
    for product in list_of_products:
        sum_of_list += product
    return sum_of_list


   Good 
  ‾‾‾‾‾‾
  def dot_product(list_a, list_b):
    return sum(map(lambda a, b: a*b, list_a, list_b))
  ```
</details>



<!-- FLAT IS BETTER THAN NESTED -->
<details>
  <summary>Flat is better than nested</summary>

  ```python
   Bad
  ‾‾‾‾‾
  a = 10
  b = 5
  c = 'A bird nest'
  if a > b:
      if len(c) > a:
          print('string c is', c)
  else:
      print('try again')


   Good 
  ‾‾‾‾‾‾
  a = 10
  b = 5
  c = 'A bird nest'
  if b < a < len(c):
      print('string c is', c)
  else:
      print('try again')
  ```
</details>



<!-- SPARSE IS BETTER THAN DENSE -->
<details>
  <summary>Sparse is better than dense</summary>

  ```python
   Bad
  ‾‾‾‾‾
  # first example is bad
  def print_sum_of_positive_int_numbers_in_mixed_list(array):
      numbers = [value for value in array if isinstance(value, int)]
      positive = [value for value in numbers if value > 0]
      sum_of_values = sum(positive)
      print("Sum of positive numbers is %s . Thank you." % sum_of_values)
  # but this one even worse
  def print_sum_of_positive_int_numbers_in_mixed_list(array):
      print("Sum of positive numbers is %s . Thank you." %
            sum([value for value in 
                 [value for value in array if isinstance(value, int)]
                 if value > 0]))


   Good 
  ‾‾‾‾‾‾
  def get_integers_from_list(array):
    return [value for value in array if isinstance(value, int)]

  def get_greater_than_zero_integers_from_list(array):
      return [value for value in array if value > 0]

  def get_sum_of_array_values(array):
      return sum(array)

  def print_information(value):
      print("Sum of positive numbers is %s . Thank you." % value)

  def print_sum_of_positive_int_numbers_in_mixed_list(array):
      numbers = get_integers_from_list(array)
      positive = get_greater_than_zero_integers_from_list(numbers)
      sum_of_values = get_sum_of_array_values(positive)
      print_information(sum_of_values)
  ```
</details>



<!-- READABILITY COUNTS -->
<details>
  <summary>Readability counts</summary>

  ```python
  """ Readability = explicit naming + simple solutions + sparse structure """

   Bad
  ‾‾‾‾‾
  VarA = 10
  elemedf_fd_dict_A = { "a":  "hello", "v": 2
  ,"c": 1}
  elemedf_fd_dict_A[VarA] = \
  "elemet!"


   Good 
  ‾‾‾‾‾‾
  char, index = "C", 3
  char_indices_dict = {
      "A": 1,
      "B": 2,
      "C": 3,
      char: index
  }
  ```
</details>



<!-- SPECIAL CASES AREN'T SPECIAL ENOUGH TO BREAK THE RULES
     ALTHOUGH PRACTICALITY BEATS PURITY -->
<details>
  <summary>Special cases aren't special enough to break the rules<br />
    &emsp;Although practicality beats purity</summary>

  ```python
  """ Special cases aren't special enough to break the rules """

  # Making your code readable for other developers is a core tenant of Python.
  # Adhering to these 'best practices' is the safest way to accomplish this.
  # Especially in the case of large projects or shared code such as libraries and modules.


  """ Although practicality beats purity """

  # Unsurprisingly, all rules have exceptions. Python Zen is not ironclad.
  # A method that deviates from established standards can still be fine if it is practical and readable.
  # Your code is your own responsibility, but keep the community in mind.
  ```
</details>



<!-- ERRORS SHOULD NEVER PASS SILENTLY
     UNLESS EXPLICITLY SILENCED -->
<details>
  <summary>Errors should never pass silently<br />
    &emsp;Unless explicitly silenced</summary>

  ```python
  """ Errors should never pass silently """
  
   Bad
  ‾‾‾‾‾
  def division_function(a, b):
    try:
        return a / b
    except:
        pass
    finally:
        return 0

   Good 
  ‾‾‾‾‾‾
  def division_function(a, b):
    try:
        return a / b
    except ZeroDivisionError as error:
        raise error


  """ Unless explicitly silenced """
  
  def division_function(a, b):
    result = 0
    try:
        result = a / b
    except ZeroDivisionError as error:
        result = error[0]
    finally:
        return result

  if __name__ == "__main__":
      value_a, value_b = 5, 0
      division = division_function(value_a, value_b)
      if division == "division by zero":
          # here we can send and error message to the developer
          pass
      else:
          print("Division result: {0}".format())
  ```
</details>



<!-- IN THE FACE OF AMBIGUITY, REFUSE THE TEMPTATION TO GUESS -->
<details>
  <summary>In the face of ambiguity, refuse the temptation to guess</summary>

  ```python
   Bad
  ‾‾‾‾‾
  def huge_function(arg1, arg2):  # where is a function description ?
    component_1 = function_huge_2(arg1)  # you skip to debug it
    component_2 = function_huge_3(arg2)  # you skip to debug it
    component_result = sqrt(component_1+component_2)
    return component_result + 1  # where is an explanation ?


   Good 
  ‾‾‾‾‾‾
  def my_custom_formula(arg1, arg2):
    """
    Custom function to calculate how ... <explanation>
    <also raw formula>
    
    **param arg1: integer, 0 < arg1 < 10
    **param arg2: float, 0 < arg2 < 1
    **return: square root of sum of arg1 in power of 10 and arg2 tangent.
    """

    component_1 = function_huge_2(arg1)  # pow to 10
    component_2 = function_huge_3(arg2)  # tangent
    component_result = sqrt(component_1+component_2)
    return component_result + 1  # see method docstring
  ```
</details>



<!-- THERE SHOULD BE ONE-- AND PREFERABLY ONLY ONE --OBVIOUS WAY TO DO IT
     ALTHOUGH THAT WAY MAY NOT BE OBVIOUS AT FIRST UNLESS YOU'RE DUTCH -->
<details>
  <summary>There should be one-- and preferably only one --obvious way to do it<br />
    &emsp;Although that way may not be obvious at first unless you're Dutch</summary>
  <br />
  <blockquote>
    “When you first start off trying to solve a problem, the first solutions you come up with are very complex, and most people stop there. But if you keep going, and live with the problem and peel more layers of the onion off, you can often times arrive at some very elegant and simple solutions.”<br>
    — Steve Jobs
  </blockquote>
  <br />

  ```python
  """ There should be one-- and preferably only one --obvious way to do it """
  
  # Create a list in Python
  # Fairly simple
  my_list = [1, 2, 3, 4, 5]
  my_list_2 = [i for i in range(1, 6)]
  my_list_3 = list(range(1, 6))
  my_list_4 = [i for i in other_list]

  # Now create a numeration list only knowing the start and end values
  # A more specific solution
  my_list = list(range(start, end+1))

  # Finally, create a custom list with a dynamic number of arguments
  # This could be done in several ways, but the obvious solution is best.
  def create_list(*args):
      return list(args)  # without list() it's a tuple

  print(create_list(1, “dog”, 2, False, “apple”, 0))  # [1, “dog”, 2, False, “apple”, 0]


  """ Although that way may not be obvious at first unless you're Dutch """
  
  # An easter egg reference to Python's creator, Guido van Rossum.
  # All Pythonic solutions are obvious to the BDFL of course.
  # But the general idea is to always think twice.
  # The proper solution may not be the first one.
  ```
</details>



<!-- NOW IS BETTER THAN NEVER
     ALTHOUGH NEVER IS OFTEN BETTER THAN *RIGHT* NOW -->
<details>
  <summary>Now is better than never<br />
    &emsp;Although never is often better than <strong>right</strong> now</summary>
  <br />
  <blockquote>
    “Always implement things when you actually need them, never when you just foresee that you need them.”<br>
    — Ron Jeffries
    <br><br>
    “It is hard for less experienced developers to appreciate how rarely architecting for future requirements/applications turns out net-positive.”<br>
    — John Carmack
  </blockquote>
  <br />

  ```python
  """ Now is better than never """

  # Pre-optimizing and planning only go so far.
  # Implement and test your solutions as you have them.
  # Errors may lead to more promising solutions if you know about them.


  """ Although never is often better than *right* now """

  # These two rules are intentionally contradictory.
  # Apply the YAGNI (You Ain't Gonna Need It) principle.
  # Avoid feature creep; don't add functionality before it's necessary.
  ```
</details>



<!-- IF THE IMPLEMENTATION IS HARD TO EXPLAIN, IT'S A BAD IDEA
     IF THE IMPLEMENTATION IS EASY TO EXPLAIN, IT MAY BE A GOOD IDEA -->
<details>
  <summary>If the implementation is hard to explain, it's a bad idea<br />
    &emsp;If the implementation is easy to explain, it may be a good idea</summary>

  ```python
  def hard():
      import xml.dom.minidom
      document = xml.dom.minidom.parseString(
          '''<menagerie><cat>Fluffers</cat><cat>Cisco</cat></menagerie>''')
      menagerie = document.childNodes[0]
      for node in menagerie.childNodes:
          if node.childNodes[0].nodeValue== 'Cisco' and node.tagName == 'cat':
              return node


  def easy(maybe):
      import lxml
      menagerie = lxml.etree.fromstring(
          '''<menagerie><cat>Fluffers</cat><cat>Cisco</cat></menagerie>''')
      for pet in menagerie.find('./cat'):
          if pet.text == 'Cisco':
              return pet
  ```
</details>



<!-- NAMESPACES ARE ONE HONKING GREAT IDEA -- LET'S DO MORE OF THOSE -->
<details>
  <summary>Namespaces are one honking great idea -- let's do more of those!</summary>

  ```python
  # A namespace is a mapping from names to objects.
  my_prime = 2
  print(id(my_prime))

  my_prime = my_prime + 1  # my_prime == 3
  print(id(my_prime))
  print(id(3))

  >>> 9302208
  >>> 9302240
  >>> 9302240
  ```
</details>


<br />
Source: https://github.com/hblanks/zen-of-python-by-example
<br />
Author:	Hunter Blanks
<br />
Date:	June 15, 2013
<br />
https://bond-kirill-alexandrovich.medium.com/python-zen-in-practice-70dc8d7c4603
Kirill Bondarenko
Oct 14, 2020

https://towardsdatascience.com/the-zen-of-python-a-guide-to-pythons-design-principles-93f3f76d088a
Vishal Sharma
Jun 3, 2020
<p align="right">(<a href="#top">back to top</a>)</p>

---

<!-- BEST PRACTICES -->
## Best Practices

<div class="section" id="explicit-code">
<h3>> Explicit code<a class="headerlink" href="#explicit-code" title="Permalink to this headline">¶</a></h3>
<p>While any kind of black magic is possible with Python, the
most explicit and straightforward manner is preferred.</p>
<p><strong>Bad</strong></p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="k">def</span> <span class="nf">make_complex</span><span class="p">(</span><span class="o">*</span><span class="n">args</span><span class="p">):</span>
    <span class="n">x</span><span class="p">,</span> <span class="n">y</span> <span class="o">=</span> <span class="n">args</span>
    <span class="k">return</span> <span class="nb">dict</span><span class="p">(</span><span class="o">**</span><span class="nb">locals</span><span class="p">())</span>
</pre></div>
</div>
<p><strong>Good</strong></p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="k">def</span> <span class="nf">make_complex</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">{</span><span class="s1">'x'</span><span class="p">:</span> <span class="n">x</span><span class="p">,</span> <span class="s1">'y'</span><span class="p">:</span> <span class="n">y</span><span class="p">}</span>
</pre></div>
</div>
<p>In the good code above, x and y are explicitly received from
the caller, and an explicit dictionary is returned. The developer
using this function knows exactly what to do by reading the
first and last lines, which is not the case with the bad example.</p>
</div>

<br />

<div class="section" id="one-statement-per-line">
<h3>> One statement per line<a class="headerlink" href="#one-statement-per-line" title="Permalink to this headline">¶</a></h3>
<p>While some compound statements such as list comprehensions are
allowed and appreciated for their brevity and their expressiveness,
it is bad practice to have two disjointed statements on the same line of code.</p>
<p><strong>Bad</strong></p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="s1">'one'</span><span class="p">);</span> <span class="k">print</span><span class="p">(</span><span class="s1">'two'</span><span class="p">)</span>

<span class="k">if</span> <span class="n">x</span> <span class="o">==</span> <span class="mi">1</span><span class="p">:</span> <span class="k">print</span><span class="p">(</span><span class="s1">'one'</span><span class="p">)</span>

<span class="k">if</span> <span class="o">&lt;</span><span class="nb">complex</span> <span class="n">comparison</span><span class="o">&gt;</span> <span class="ow">and</span> <span class="o">&lt;</span><span class="n">other</span> <span class="nb">complex</span> <span class="n">comparison</span><span class="o">&gt;</span><span class="p">:</span>
    <span class="c1"># do something</span>
</pre></div>
</div>
<p><strong>Good</strong></p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="s1">'one'</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="s1">'two'</span><span class="p">)</span>

<span class="k">if</span> <span class="n">x</span> <span class="o">==</span> <span class="mi">1</span><span class="p">:</span>
    <span class="k">print</span><span class="p">(</span><span class="s1">'one'</span><span class="p">)</span>

<span class="n">cond1</span> <span class="o">=</span> <span class="o">&lt;</span><span class="nb">complex</span> <span class="n">comparison</span><span class="o">&gt;</span>
<span class="n">cond2</span> <span class="o">=</span> <span class="o">&lt;</span><span class="n">other</span> <span class="nb">complex</span> <span class="n">comparison</span><span class="o">&gt;</span>
<span class="k">if</span> <span class="n">cond1</span> <span class="ow">and</span> <span class="n">cond2</span><span class="p">:</span>
    <span class="c1"># do something</span>
</pre></div>
</div>
</div>

<br />

<div class="section" id="function-arguments">
<h3>> Function arguments<a class="headerlink" href="#function-arguments" title="Permalink to this headline">¶</a></h3>
<p>Arguments can be passed to functions in four different ways.</p>
<ol class="arabic simple">
<li><strong>Positional arguments</strong> are mandatory and have no default values. They are
the simplest form of arguments and they can be used for the few function
arguments that are fully part of the function’s meaning and their order is
natural. For instance, in <code class="docutils literal notranslate"><span class="pre">send(message,</span> <span class="pre">recipient)</span></code> or <code class="docutils literal notranslate"><span class="pre">point(x,</span> <span class="pre">y)</span></code>
the user of the function has no difficulty remembering that those two
functions require two arguments, and in which order.</li>
</ol>
<p>In those two cases, it is possible to use argument names when calling the
functions and, doing so, it is possible to switch the order of arguments,
calling for instance <code class="docutils literal notranslate"><span class="pre">send(recipient='World',</span> <span class="pre">message='Hello')</span></code> and
<code class="docutils literal notranslate"><span class="pre">point(y=2,</span> <span class="pre">x=1)</span></code> but this reduces readability and is unnecessarily verbose,
compared to the more straightforward calls to <code class="docutils literal notranslate"><span class="pre">send('Hello',</span> <span class="pre">'World')</span></code> and
<code class="docutils literal notranslate"><span class="pre">point(1,</span> <span class="pre">2)</span></code>.</p>
<ol class="arabic simple" start="2">
<li><strong>Keyword arguments</strong> are not mandatory and have default values. They are
often used for optional parameters sent to the function. When a function has
more than two or three positional parameters, its signature is more difficult
to remember and using keyword arguments with default values is helpful. For
instance, a more complete <code class="docutils literal notranslate"><span class="pre">send</span></code> function could be defined as
<code class="docutils literal notranslate"><span class="pre">send(message,</span> <span class="pre">to,</span> <span class="pre">cc=None,</span> <span class="pre">bcc=None)</span></code>. Here <code class="docutils literal notranslate"><span class="pre">cc</span></code> and <code class="docutils literal notranslate"><span class="pre">bcc</span></code> are
optional, and evaluate to <code class="docutils literal notranslate"><span class="pre">None</span></code> when they are not passed another value.</li>
</ol>
<p>Calling a function with keyword arguments can be done in multiple ways in
Python; for example, it is possible to follow the order of arguments in the
definition without explicitly naming the arguments, like in
<code class="docutils literal notranslate"><span class="pre">send('Hello',</span> <span class="pre">'World',</span> <span class="pre">'Cthulhu',</span> <span class="pre">'God')</span></code>, sending a blind carbon copy to
God. It would also be possible to name arguments in another order, like in
<code class="docutils literal notranslate"><span class="pre">send('Hello</span> <span class="pre">again',</span> <span class="pre">'World',</span> <span class="pre">bcc='God',</span> <span class="pre">cc='Cthulhu')</span></code>. Those two
possibilities are better avoided without any strong reason to not follow the
syntax that is the closest to the function definition:
<code class="docutils literal notranslate"><span class="pre">send('Hello',</span> <span class="pre">'World',</span> <span class="pre">cc='Cthulhu',</span> <span class="pre">bcc='God')</span></code>.</p>
<p>As a side note, following the <a class="reference external" href="http://en.wikipedia.org/wiki/You_ain't_gonna_need_it">YAGNI</a>
principle, it is often harder to remove an optional argument (and its logic
inside the function) that was added “just in case” and is seemingly never used,
than to add a new optional argument and its logic when needed.</p>
<ol class="arabic simple" start="3">
<li>The <strong>arbitrary argument list</strong> is the third way to pass arguments to a
function. If the function intention is better expressed by a signature with
an extensible number of positional arguments, it can be defined with the
<code class="docutils literal notranslate"><span class="pre">*args</span></code> constructs. In the function body, <code class="docutils literal notranslate"><span class="pre">args</span></code> will be a tuple of all
the remaining positional arguments. For example, <code class="docutils literal notranslate"><span class="pre">send(message,</span> <span class="pre">*args)</span></code>
can be called with each recipient as an argument: <code class="docutils literal notranslate"><span class="pre">send('Hello',</span> <span class="pre">'God',</span>
<span class="pre">'Mom',</span> <span class="pre">'Cthulhu')</span></code>, and in the function body <code class="docutils literal notranslate"><span class="pre">args</span></code> will be equal to
<code class="docutils literal notranslate"><span class="pre">('God',</span> <span class="pre">'Mom',</span> <span class="pre">'Cthulhu')</span></code>.</li>
</ol>
<p>However, this construct has some drawbacks and should be used with caution. If a
function receives a list of arguments of the same nature, it is often more
clear to define it as a function of one argument, that argument being a list or
any sequence. Here, if <code class="docutils literal notranslate"><span class="pre">send</span></code> has multiple recipients, it is better to define
it explicitly: <code class="docutils literal notranslate"><span class="pre">send(message,</span> <span class="pre">recipients)</span></code> and call it with <code class="docutils literal notranslate"><span class="pre">send('Hello',</span>
<span class="pre">['God',</span> <span class="pre">'Mom',</span> <span class="pre">'Cthulhu'])</span></code>. This way, the user of the function can manipulate
the recipient list as a list beforehand, and it opens the possibility to pass
any sequence, including iterators, that cannot be unpacked as other sequences.</p>
<ol class="arabic simple" start="4">
<li>The <strong>arbitrary keyword argument dictionary</strong> is the last way to pass
arguments to functions. If the function requires an undetermined series of
named arguments, it is possible to use the <code class="docutils literal notranslate"><span class="pre">**kwargs</span></code> construct. In the
function body, <code class="docutils literal notranslate"><span class="pre">kwargs</span></code> will be a dictionary of all the passed named
arguments that have not been caught by other keyword arguments in the
function signature.</li>
</ol>
<p>The same caution as in the case of <em>arbitrary argument list</em> is necessary, for
similar reasons: these powerful techniques are to be used when there is a
proven necessity to use them, and they should not be used if the simpler and
clearer construct is sufficient to express the function’s intention.</p>
<p>It is up to the programmer writing the function to determine which arguments
are positional arguments and which are optional keyword arguments, and to
decide whether to use the advanced techniques of arbitrary argument passing. If
the advice above is followed wisely, it is possible and enjoyable to write
Python functions that are:</p>
<ul class="simple">
<li>easy to read (the name and arguments need no explanations)</li>
<li>easy to change (adding a new keyword argument does not break other parts of
the code)</li>
</ul>
</div>

<br />

<div class="section" id="returning-values">
<h3>> Returning values<a class="headerlink" href="#returning-values" title="Permalink to this headline">¶</a></h3>
<p>When a function grows in complexity, it is not uncommon to use multiple return
statements inside the function’s body. However, in order to keep a clear intent
and a sustainable readability level, it is preferable to avoid returning
meaningful values from many output points in the body.</p>
<p>There are two main cases for returning values in a function: the result of the
function return when it has been processed normally, and the error cases that
indicate a wrong input parameter or any other reason for the function to not be
able to complete its computation or task.</p>
<p>If you do not wish to raise exceptions for the second case, then returning a
value, such as None or False, indicating that the function could not perform
correctly might be needed. In this case, it is better to return as early as the
incorrect context has been detected. It will help to flatten the structure of
the function: all the code after the return-because-of-error statement can
assume the condition is met to further compute the function’s main result.
Having multiple such return statements is often necessary.</p>
<p>However, when a function has multiple main exit points for its normal course,
it becomes difficult to debug the returned result, so it may be preferable to
keep a single exit point. This will also help factoring out some code paths,
and the multiple exit points are a probable indication that such a refactoring
is needed.</p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="k">def</span> <span class="nf">complex_function</span><span class="p">(</span><span class="n">a</span><span class="p">,</span> <span class="n">b</span><span class="p">,</span> <span class="n">c</span><span class="p">):</span>
    <span class="k">if</span> <span class="ow">not</span> <span class="n">a</span><span class="p">:</span>
        <span class="k">return</span> <span class="bp">None</span>  <span class="c1"># Raising an exception might be better</span>
    <span class="k">if</span> <span class="ow">not</span> <span class="n">b</span><span class="p">:</span>
        <span class="k">return</span> <span class="bp">None</span>  <span class="c1"># Raising an exception might be better</span>
    <span class="c1"># Some complex code trying to compute x from a, b and c</span>
    <span class="c1"># Resist temptation to return x if succeeded</span>
    <span class="k">if</span> <span class="ow">not</span> <span class="n">x</span><span class="p">:</span>
        <span class="c1"># Some Plan-B computation of x</span>
    <span class="k">return</span> <span class="n">x</span>  <span class="c1"># One single exit point for the returned value x will help</span>
              <span class="c1"># when maintaining the code.</span>
</pre></div>
</div>
</div>




<!-- IDIOMATIC PYTHON -->
## Idiomatic Python
### Writing Pythonic code

### Unpacking

<br />

### Create an ignored variable

<br />

### List construction

<br />

#### Create a length-N list of the same thing

<br />

#### Create a length-N list of lists

<br />

#### Create a string from a list

<br />

### Searching for an item in a collection




<!-- CONVENTIONS -->
## Conventions

### Check if a variable equals a constant

<br />

### Access a Dictionary Element

<br />

### List Usage

<br />

#### Short Ways to Manipulate Lists

<br />

#### Filtering a list

<br />

#### Possible side effects of modifying the original list

<br />

#### Modifying the values in a list

<br />

### Read From a File

<br />

### Line Continuations




<!-- PEP 8 -->
## PEP 8

### Personal preference deviations




<!-- STRUCTURE AND FORMATTING -->
## Structure and Formatting

### Code Map

<br />

### We are all responsible users

<br />

### Symbology











<!-- GETTING STARTED -->
## Getting Started

This 

### Prerequisites

This
* npm
  ```sh
  npm install npm@latest -g
  ```

1. Get a free API Key at [https://example.com](https://example.com)
2. Clone the repo
   ```sh
   git clone https://github.com/github_username/repo_name.git
   ```

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

Use

_For more examples, please refer to the [Documentation](https://example.com)_

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [ ] Feature 1
    - [ ] Nested Feature

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Your Name - [@twitter_handle](https://twitter.com/twitter_handle) - email@email_client.com

Project Link: [https://github.com/github_username/repo_name](https://github.com/github_username/repo_name)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- Sources -->
## Sources

* []()
* []()
* []()

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[product-screenshot]: images/screenshot.png