<div id="top"></div>



<!-- TITLE -->
<br />
<h1 align="center">CTC Python Style Guide</h1>
  <p align="center">
    A set of code style and formatting guidelines for python projects created by the CTC R&D team.
    <br>
    Includes pythonic best practices, idioms, conventions, structure, and symbology. 
    <br>
    <br>
  </p>
</div>



<!--##################################################################-->

<!--##################################################################-->



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

<!-- TABLE OF CONTENTS
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
-->


<!--##################################################################-->
<!--##################################################################-->


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


<!---------------------------------------------------------------------->
<!---------------------------------------------------------------------->


### Examples

<!-- BEAUTIFUL IS BETTER THAN UGLY -->
<details>
  <summary>Beautiful is better than ugly</summary><br>
  
  <p><strong>Bad</strong></p>

  ```python
  def LongCamelCaseFuncNameDoSomeStuff(arg1, arg2, arg3, arg4, arg5):
    if (arg1 | arg2):
        return 1;
    elif (arg4 > arg5):
        return 2;
    else:
        return arg3;
    localVar = map(lambda x,y,z,a,b,c: x+y+z+a+b+c, [1], [2], [3], [4], [5], [6]);
    return localVar
  ```

  <p><strong>Good</strong></p>

  ```python
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
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- EXPLICIT IS BETTER THAN IMPLICIT -->
<details>
  <summary>Explicit is better than implicit</summary><br>
  
  <p><strong>Bad</strong></p>

  ```python
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
  ```

  <p><strong>Good</strong></p>

  ```python
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
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- SIMPLE IS BETTER THAN COMPLEX -->
<details>
  <summary>Simple is better than complex</summary><br>
  
  <p><strong>Bad</strong></p>

  ```python
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
  ```

  <p><strong>Good</strong></p>

  ```python
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
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- COMPLEX IS BETTER THAN COMPLICATED -->
<details>
  <summary>Complex is better than complicated</summary><br>
  
  <p><strong>Bad</strong></p>

  ```python
  def dot_product(list_a, list_b):
    list_of_products = []
    for a, b in zip(list_a, list_b):
        list_of_products.append(a * b)
    sum_of_list = 0
    for product in list_of_products:
        sum_of_list += product
    return sum_of_list
  ```

  <p><strong>Good</strong></p>

  ```python
  def dot_product(list_a, list_b):
    return sum(map(lambda a, b: a*b, list_a, list_b))
  ```
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- FLAT IS BETTER THAN NESTED -->
<details>
  <summary>Flat is better than nested</summary><br>
  
  <p><strong>Bad</strong></p>

  ```python
  a = 10
  b = 5
  c = 'A bird nest'
  if a > b:
      if len(c) > a:
          print('string c is', c)
  else:
      print('try again')
  ```

  <p><strong>Good</strong></p>

  ```python
  a = 10
  b = 5
  c = 'A bird nest'
  if b < a < len(c):
      print('string c is', c)
  else:
      print('try again')
  ```
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- SPARSE IS BETTER THAN DENSE -->
<details>
  <summary>Sparse is better than dense</summary><br>
  
  <p><strong>Bad</strong></p>

  ```python
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
  ```

  <p><strong>Good</strong></p>

  ```python
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
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- READABILITY COUNTS -->
<details>
  <summary>Readability counts</summary><br>

  > Readability = explicit naming + simple solutions + sparse structure
  
  <p><strong>Bad</strong></p>

  ```python
  VarA = 10
  elemedf_fd_dict_A = { "a":  "hello", "v": 2
  ,"c": 1}
  elemedf_fd_dict_A[VarA] = \
  "elemet!"
  ```

  <p><strong>Good</strong></p>

  ```python
  char, index = "C", 3
  char_indices_dict = {
      "A": 1,
      "B": 2,
      "C": 3,
      char: index
  }
  ```
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- SPECIAL CASES AREN'T SPECIAL ENOUGH TO BREAK THE RULES
     ALTHOUGH PRACTICALITY BEATS PURITY -->
<details>
  <summary>Special cases aren't special enough to break the rules<br />
    &emsp;Although practicality beats purity</summary><br>
  
  <p><strong>Special cases aren't special enough to break the rules.</strong></p>

  ```
    Making your code readable for other developers is a core tenant of Python.
    Adhering to these 'best practices' is the safest way to accomplish this.
    Especially in the case of large projects or shared code such as libraries and modules.
  ```
  <br>

  <p><strong>Although practicality beats purity.</strong></p>

  ```
    Unsurprisingly, all rules have exceptions. Python Zen is not ironclad.
    A method that deviates from established standards can still be fine if it is practical and readable.
    Your code is your own responsibility, but keep the community in mind.
  ```
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- ERRORS SHOULD NEVER PASS SILENTLY
     UNLESS EXPLICITLY SILENCED -->
<details>
  <summary>Errors should never pass silently<br />
    &emsp;Unless explicitly silenced</summary><br>
  
  <p><strong>Errors should never pass silently.</strong></p>
  
  <p><strong>Bad</strong></p>

  ```python
  def division_function(a, b):
    try:
        return a / b
    except:
        pass
    finally:
        return 0
  ```

  <p><strong>Good</strong></p>

  ```python
  def division_function(a, b):
    try:
        return a / b
    except ZeroDivisionError as error:
        raise error
  ```

  <br><p><strong>Unless explicitly silenced.</strong></p>

  ```python
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
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- IN THE FACE OF AMBIGUITY, REFUSE THE TEMPTATION TO GUESS -->
<details>
  <summary>In the face of ambiguity, refuse the temptation to guess</summary><br>
  
  <p><strong>Bad</strong></p>

  ```python
  def huge_function(arg1, arg2):  # where is a function description ?
    component_1 = function_huge_2(arg1)  # you skip to debug it
    component_2 = function_huge_3(arg2)  # you skip to debug it
    component_result = sqrt(component_1+component_2)
    return component_result + 1  # where is an explanation ?
  ```

  <p><strong>Good</strong></p>

  ```python
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
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- THERE SHOULD BE ONE-- AND PREFERABLY ONLY ONE --OBVIOUS WAY TO DO IT
     ALTHOUGH THAT WAY MAY NOT BE OBVIOUS AT FIRST UNLESS YOU'RE DUTCH -->
<details>
  <summary>There should be one-- and preferably only one --obvious way to do it<br>
    &emsp;Although that way may not be obvious at first unless you're Dutch</summary>
  <br>
  <blockquote>
    “When you first start off trying to solve a problem, the first solutions you come up with are very complex, and most people stop there. But if you keep going, and live with the problem and peel more layers of the onion off, you can often times arrive at some very elegant and simple solutions.”<br>
    — Steve Jobs
  </blockquote>
  
  <p><strong>There should be one-- and preferably only one --obvious way to do it.</strong></p>

  ```python
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
  ```

  <p><strong>Although that way may not be obvious at first unless you're Dutch.</strong></p>

  ```
    An easter egg reference to Python's creator, Guido van Rossum.
    All Pythonic solutions are obvious to the BDFL of course.
    But the general idea is to always think twice.
    The proper solution may not be the first one.
  ```
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- NOW IS BETTER THAN NEVER
     ALTHOUGH NEVER IS OFTEN BETTER THAN *RIGHT* NOW -->
<details>
  <summary>Now is better than never<br>
    &emsp;Although never is often better than <em>right</em> now</summary>
  <br>
  <blockquote>
    “Always implement things when you actually need them, never when you just foresee that you need them.”<br>
    — Ron Jeffries
    <br><br>
    “It is hard for less experienced developers to appreciate how rarely architecting for future requirements/applications turns out net-positive.”<br>
    — John Carmack
  </blockquote>
  
  <p><strong>Now is better than never.</strong></p>

  ```
    Pre-optimizing and planning only go so far.
    Implement and test your solutions as you have them.
    Errors may lead to more promising solutions if you know about them.
  ```

  <p><strong>Although never is often better than <i>right</i> now.</strong></p>

  ```
    These two rules are intentionally contradictory.
    Apply the YAGNI (You Ain't Gonna Need It) principle.
    Avoid feature creep; don't add functionality before it's necessary.
  ```
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- IF THE IMPLEMENTATION IS HARD TO EXPLAIN, IT'S A BAD IDEA
     IF THE IMPLEMENTATION IS EASY TO EXPLAIN, IT MAY BE A GOOD IDEA -->
<details>
  <summary>If the implementation is hard to explain, it's a bad idea<br />
    &emsp;If the implementation is easy to explain, it may be a good idea</summary>
  <br>

  <p><strong>If the implementation is hard to explain, it's a bad idea.</strong></p>

  ```python
  def hard():
      import xml.dom.minidom
      document = xml.dom.minidom.parseString(
          '''<menagerie><cat>Fluffers</cat><cat>Cisco</cat></menagerie>''')
      menagerie = document.childNodes[0]
      for node in menagerie.childNodes:
          if node.childNodes[0].nodeValue== 'Cisco' and node.tagName == 'cat':
              return node
  ```

  <p><strong>If the implementation is easy to explain, it may be a good idea.</strong></p>

  ```python
  def easy(maybe):
      import lxml
      menagerie = lxml.etree.fromstring(
          '''<menagerie><cat>Fluffers</cat><cat>Cisco</cat></menagerie>''')
      for pet in menagerie.find('./cat'):
          if pet.text == 'Cisco':
              return pet
  ```
  <br>
</details>


<!---------------------------------------------------------------------->


<!-- NAMESPACES ARE ONE HONKING GREAT IDEA -- LET'S DO MORE OF THOSE -->
<details>
  <summary>Namespaces are one honking great idea -- let's do more of those!</summary>
  <br>

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
  <br>
</details>
<br/><br/>

### Sources
[Zen of Python by Example](https://github.com/hblanks/zen-of-python-by-example)
<br/>
Hunter Blanks - June 15, 2013
<br/><br/>
[Python Zen in Practice](https://bond-kirill-alexandrovich.medium.com/python-zen-in-practice-70dc8d7c4603)
<br/>
Kirill Bondarenko - Date: Oct 14, 2020
<br/><br/>
[A Guide to Python's Design Principles](https://towardsdatascience.com/the-zen-of-python-a-guide-to-pythons-design-principles-93f3f76d088a)
<br/>
Vishal Sharma - Date: Jun 3, 2020
<br/><br/>
<p align="right">(<a href="#top">back to top</a>)</p>



<!--##################################################################-->
---
<!--##################################################################-->



<!-- BEST PRACTICES -->
<br>

## Best Practices

<!-- EXPLICIT CODE -->
<details>
  <summary><font size="3">Explicit code</font></summary>
  <br>
  <div class="section" id="explicit-code">

  <p>While any kind of black magic is possible with Python, the
  most explicit and straightforward manner is preferred.</p>

  <p><strong>Bad</strong></p>

  ```python
  def make_complex(*args):
      x, y = args
      return dict(**locals())
  ```

  <p><strong>Good</strong></p>

  ```python
  def make_complex(x, y):
      return {'x': x, 'y': y}
  ```

  <p>In the good code above, x and y are explicitly received from
  the caller, and an explicit dictionary is returned. The developer
  using this function knows exactly what to do by reading the
  first and last lines, which is not the case with the bad example.</p>
  </div>
</details>
<br>


<!---------------------------------------------------------------------->


<!-- ONE STATEMENT PER LINE -->
<details>
  <summary><font size="3">One statement per line</font></summary>
  <br>
  <div class="section" id="one-statement-per-line">
  <p>While some compound statements such as list comprehensions are
  allowed and appreciated for their brevity and their expressiveness,
  it is bad practice to have two disjointed statements on the same line of code.</p>
  
  <p><strong>Bad</strong></p>

  ```python
  print('one'); print('two')

  if x == 1: print('one')

  if <complex comparison> and <other complex comparison>:
      # do something
  ```

  <p><strong>Good</strong></p>

  ```python
  print('one')
  print('two')

  if x == 1:
      print('one')

  cond1 = <complex comparison>
  cond2 = <other complex comparison>
  if cond1 and cond2:
      # do something
  ```
  </div>
</details>
<br>


<!---------------------------------------------------------------------->


<!-- FUNCTION ARGUMENTS -->
<details>
  <summary><font size="3">Function arguments</font></summary>
  <br>
  <div class="section" id="function-arguments">

  <p>Arguments can be passed to functions in four different ways.</p>
  <p style="text-indent:-15px; padding-left:15px;">
    1. <strong>Positional arguments</strong> are mandatory and have no default values. They are the simplest form of arguments and they can be used for the few function arguments that are fully part of the function’s meaning and their order is natural. For instance, in <code>send(message, recipient)</code> or <code>point(x, y)</code> the user of the function has no difficulty remembering that those two functions require two arguments, and in which order.
  </p>
  <p>In those two cases, it is possible to use argument names when calling the functions and, doing so, it is possible to switch the order of arguments, calling for instance <code>send(recipient='World', message='Hello')</code> and <code>point(y=2, x=1)</code> but this reduces readability and is unnecessarily verbose, compared to the more straightforward calls to <code>send('Hello', 'World')</code> and <code>point(1, 2)</code>.</p>
  <br>

  <p style="text-indent:-15px; padding-left:15px;">
    2. <strong>Keyword arguments</strong> are not mandatory and have default values. They are often used for optional parameters sent to the function. When a function has more than two or three positional parameters, its signature is more difficult to remember and using keyword arguments with default values is helpful. For instance, a more complete <code>send</code> function could be defined as <code>send(message, to, cc=None, bcc=None)</code>. Here <code>cc</code> and <code>bcc</code> are optional, and evaluate to <code>None</code> when they are not passed another value.
  </p>
  <p>Calling a function with keyword arguments can be done in multiple ways in Python; for example, it is possible to follow the order of arguments in the
  definition without explicitly naming the arguments, like in <code>send('Hello', 'World', 'Cthulhu', 'God')</code>, sending a blind carbon copy to God. It would also be possible to name arguments in another order, like in <code>send('Hello again', 'World', bcc='God', cc='Cthulhu')</code>. Those two possibilities are better avoided without any strong reason to not follow the syntax that is the closest to the function definition: <code>send('Hello', 'World', cc='Cthulhu', bcc='God')</code>.</p>
  <p>As a side note, following the <a class="reference external" href="http://en.wikipedia.org/wiki/You_ain't_gonna_need_it">YAGNI</a> principle, it is often harder to remove an optional argument (and its logic inside the function) that was added “just in case” and is seemingly never used, than to add a new optional argument and its logic when needed.</p>
  <br>

  <p style="text-indent:-15px; padding-left:15px;">
    3. The <strong>arbitrary argument list</strong> is the third way to pass arguments to a function. If the function intention is better expressed by a signature with an extensible number of positional arguments, it can be defined with the <code>*args</code> constructs. In the function body, <code>args</code> will be a tuple of all the remaining positional arguments. For example, <code>send(message, *args)</code> can be called with each recipient as an argument:<code>send('Hello', 'God', 'Mom', 'Cthulhu')</code>, and in the function body <code>args</code> will be equal to <code>('God', 'Mom', 'Cthulhu')</code>.
  </p>
  <p>However, this construct has some drawbacks and should be used with caution. If a function receives a list of arguments of the same nature, it is often more clear to define it as a function of one argument, that argument being a list or any sequence. Here, if <code>send</code> has multiple recipients, it is better to define it explicitly: <code>send(message, recipients)</code> and call it with <code>send('Hello', ['God', 'Mom', 'Cthulhu'])</code>. This way, the user of the function can manipulate the recipient list as a list beforehand, and it opens the possibility to pass any sequence, including iterators, that cannot be unpacked as other sequences.</p>
  <br>

  <p style="text-indent:-15px; padding-left:15px;">
    4. The <strong>arbitrary keyword argument dictionary</strong> is the last way to pass arguments to functions. If the function requires an undetermined series of named arguments, it is possible to use the <code>**kwargs</code> construct. In the function body, <code>kwargs</code> will be a dictionary of all the passed named arguments that have not been caught by other keyword arguments in the function signature.
  </p>
  <p>The same caution as in the case of <em>arbitrary argument list</em> is necessary, for similar reasons: these powerful techniques are to be used when there is a proven necessity to use them, and they should not be used if the simpler and clearer construct is sufficient to express the function’s intention.</p>
  <p>It is up to the programmer writing the function to determine which arguments are positional arguments and which are optional keyword arguments, and to
  decide whether to use the advanced techniques of arbitrary argument passing. If the advice above is followed wisely, it is possible and enjoyable to write Python functions that are:</p>
  <p style="text-indent:-2px; padding-left:15px; line-height:15px">
    &bull; easy to read (the name and arguments need no explanations)
  </p>
  <p style="text-indent:-2px; padding-left:15px; line-height:15px">
    &bull; easy to change (adding a new keyword argument does not break other parts of the code)
  </p>
  </div>
</details>
<br>


<!---------------------------------------------------------------------->


<!-- RETURNING VALUES -->
<details>
  <summary><font size="3">Returning values</font></summary>
  <br>
  <div class="section" id="returning-values">

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

  ```python
  def complex_function(a, b, c):
      if not a:
          return None  # Raising an exception might be better
      if not b:
          return None  # Raising an exception might be better
      # Some complex code trying to compute x from a, b and c
      # Resist temptation to return x if succeeded
      if not x:
          # Some Plan-B computation of x
      return x  # One single exit point for the returned value x will help
                # when maintaining the code.
  ```
  </div>
</details>
<br>

<p align="right">(<a href="#top">back to top</a>)</p>



<!--##################################################################-->
---
<!--##################################################################-->



<!-- IDIOMATIC PYTHON -->
<br>

## Idiomatic Python
### Writing Pythonic code

<div class="section" id="unpacking">
<h3>> Unpacking<a class="headerlink" href="#unpacking" title="Permalink to this headline">¶</a></h3>
<p>If you know the length of a list or tuple, you can assign names to its
elements with unpacking. For example, since <code class="docutils literal notranslate"><span class="pre">enumerate()</span></code> will provide
a tuple of two elements for each item in list:</p>

  ```python
  for index, item in enumerate(some_list):
      # do something with index and item
  ```
<p>You can use this to swap variables as well:</p>

  ```python
  a, b = b, a
  ```
<p>Nested unpacking works too:</p>

  ```python
  a, (b, c) = 1, (2, 3)
  ```
<p>In Python 3, a new method of extended unpacking was introduced by
<span class="target" id="index-0"></span><a class="pep reference external" href="https://www.python.org/dev/peps/pep-3132"><strong>PEP 3132</strong></a>:</p>

  ```python
  a, *rest = [1, 2, 3]
  # a = 1, rest = [2, 3]
  a, *middle, c = [1, 2, 3, 4]
  # a = 1, middle = [2, 3], c = 4
  ```
</div>

<br />

<div class="section" id="create-an-ignored-variable">
<h3>> Create an ignored variable<a class="headerlink" href="#create-an-ignored-variable" title="Permalink to this headline">¶</a></h3>
<p>If you need to assign something (for instance, in <a class="reference internal" href="#unpacking-ref"><span class="std std-ref">Unpacking</span></a>) but
will not need that variable, use <code class="docutils literal notranslate"><span class="pre">__</span></code>:</p>

  ```python
  filename = 'foobar.txt'
  basename, __, ext = filename.rpartition('.')
  ```
  <br>

> Note
>
> Many Python style guides recommend the use of a single underscore "`_`"
for throwaway variables rather than the double underscore "`__`"
recommended here. The issue is that "`_`" is commonly used as an alias
for the [`gettext()`](https://docs.python.org/3/library/gettext.html#gettext.gettext)
function, and is also used at the interactive prompt to hold the value of the
last operation. Using a double underscore instead is just as clear and almost
as convenient, and eliminates the risk of accidentally interfering with either
of these other use cases.

</div>
</div>

<br />

<div class="section" id="list-construction">
<h3>> List Construction<a class="headerlink" href="#list-construction" title="Permalink to this headline">¶</a></h3>

#

<dl><dd>
<div class="section" id="create-a-length-n-list-of-the-same-thing">
<h4>&emsp;- Create a length-N list of the same thing<a class="headerlink" href="#create-a-length-n-list-of-the-same-thing" title="Permalink to this headline">¶</a></h4>
<p>&emsp;Use the Python list <code class="docutils literal notranslate"><span class="pre">*</span></code> operator:</p>

  ```python
  four_nones = [None] * 4
  ```
</div>
</dd></dl>

#

<dl><dd>
<div class="section" id="create-a-length-n-list-of-lists">
<h4>&emsp;- Create a length-N list of lists<a class="headerlink" href="#create-a-length-n-list-of-lists" title="Permalink to this headline">¶</a></h4>
<p>&emsp;Because lists are mutable, the <code class="docutils literal notranslate"><span class="pre">*</span></code> operator (as above) will create a list
of N references to the <cite>same</cite> list, which is not likely what you want.
Instead, use a list comprehension:</p>

  ```python
  four_lists = [[] for __ in range(4)]
  ```
</div>
</dd></dl>

#

<dl><dd>
<div class="section" id="create-a-string-from-a-list">
<h4>&emsp;>> Create a string from a list<a class="headerlink" href="#create-a-string-from-a-list" title="Permalink to this headline">¶</a></h4>
<p>A common idiom for creating strings is to use <a class="reference external" href="https://docs.python.org/3/library/stdtypes.html#str.join" title="(in Python v3.11)"><code class="xref py py-meth docutils literal notranslate"><span class="pre">str.join()</span></code></a> on an empty
string.</p>

  ```python
  letters = ['s', 'p', 'a', 'm']
  word = ''.join(letters)
  ```
<p>This will set the value of the variable <em>word</em> to ‘spam’. This idiom can be
applied to lists and tuples.</p>
</div>
</div>
</dd></dl>

<br />

<div class="section" id="searching-for-an-item-in-a-collection">
<h3>> Searching for an item in a collection<a class="headerlink" href="#searching-for-an-item-in-a-collection" title="Permalink to this headline">¶</a></h3>
<p>Sometimes we need to search through a collection of things. Let’s look at two
options: lists and sets.</p>
<p>Take the following code for example:</p>

  ```python
  s = set(['s', 'p', 'a', 'm'])
  l = ['s', 'p', 'a', 'm']

  def lookup_set(s):
      return 's' in s

  def lookup_list(l):
      return 's' in l
  ```
<p>Even though both functions look identical, because <em>lookup_set</em> is utilizing
the fact that sets in Python are hashtables, the lookup performance
between the two is very different. To determine whether an item is in a list,
Python will have to go through each item until it finds a matching item.
This is time consuming, especially for long lists. In a set, on the other
hand, the hash of the item will tell Python where in the set to look for
a matching item. As a result, the search can be done quickly, even if the
set is large. Searching in dictionaries works the same way. For
more information see this
<a class="reference external" href="https://stackoverflow.com/questions/513882/python-list-vs-dict-for-look-up-table">StackOverflow</a>
page. For detailed information on the amount of time various common operations
take on each of these data structures, see
<a class="reference external" href="https://wiki.python.org/moin/TimeComplexity?">this page</a>.</p>
<p>Because of these differences in performance, it is often a good idea to use
sets or dictionaries instead of lists in cases where:</p>
<ul class="simple">
<li>The collection will contain a large number of items</li>
<li>You will be repeatedly searching for items in the collection</li>
<li>You do not have duplicate items.</li>
</ul>
<p>For small collections, or collections which you will not frequently be
searching through, the additional time and memory required to set up the
hashtable will often be greater than the time saved by the improved search
speed.</p>
</div>

<br />
<p align="right">(<a href="#top">back to top</a>)</p>



<!--##################################################################-->
---
<!--##################################################################-->



<!-- CONVENTIONS -->
<br />

## Conventions
Here are some conventions you should follow to make your code easier to read.

<div class="section" id="check-if-a-variable-equals-a-constant">
<h3>Check if a variable equals a constant<a class="headerlink" href="#check-if-a-variable-equals-a-constant" title="Permalink to this headline">¶</a></h3>
<p>You don’t need to explicitly compare a value to True, or None, or 0 – you can
just add it to the if statement. See <a class="reference external" href="http://docs.python.org/library/stdtypes.html#truth-value-testing">Truth Value Testing</a> for a
list of what is considered false.</p>
<p><strong>Bad</strong>:</p>

  ```python
  if attr == True:
      print('True!')

  if attr == None:
      print('attr is None!')
  ```
<p><strong>Good</strong>:</p>

  ```python
  # Just check the value
  if attr:
      print('attr is truthy!')

  # or check for the opposite
  if not attr:
      print('attr is falsey!')

  # or, since None is considered false, explicitly check for it
  if attr is None:
      print('attr is None!')
  ```
</div>

<br />

<div class="section" id="access-a-dictionary-element">
<h3>Access a Dictionary Element<a class="headerlink" href="#access-a-dictionary-element" title="Permalink to this headline">¶</a></h3>
<p>Don’t use the <code class="xref py py-meth docutils literal notranslate"><span class="pre">dict.has_key()</span></code> method. Instead, use <code class="docutils literal notranslate"><span class="pre">x</span> <span class="pre">in</span> <span class="pre">d</span></code> syntax,
or pass a default argument to <a class="reference external" href="https://docs.python.org/3/library/stdtypes.html#dict.get" title="(in Python v3.11)"><code class="xref py py-meth docutils literal notranslate"><span class="pre">dict.get()</span></code></a>.</p>
<p><strong>Bad</strong>:</p>

  ```python
  d = {'hello': 'world'}
  if d.has_key('hello'):
      print(d['hello'])    # prints 'world'
  else:
      print('default_value')
  ```
<p><strong>Good</strong>:</p>

  ```python
  d = {'hello': 'world'}

  print(d.get('hello', 'default_value')) # prints 'world'
  print(d.get('thingy', 'default_value')) # prints 'default_value'

  # Or:
  if 'hello' in d:
      print(d['hello'])
  ```
</div>

<br />

<div class="section" id="list-usage">
<h3>List Usage<a class="headerlink" href="#list-usage" title="Permalink to this headline">¶</a></h3>

#

<div class="section" id="short-ways-to-manipulate-lists">
<h4>Short Ways to Manipulate Lists<a class="headerlink" href="#short-ways-to-manipulate-lists" title="Permalink to this headline">¶</a></h4>
<p><a class="reference external" href="http://docs.python.org/tutorial/datastructures.html#list-comprehensions">List comprehensions</a>
provides a powerful, concise way to work with lists.</p>
<p><a class="reference external" href="http://docs.python.org/tutorial/classes.html#generator-expressions">Generator expressions</a>
follows almost the same syntax as list comprehensions but return a generator
instead of a list.</p>
<p>Creating a new list requires more work and uses more memory. If you are just going
to loop through the new list, prefer using an iterator instead.</p>
<p><strong>Bad</strong>:</p>

  ```python
  # needlessly allocates a list of all (gpa, name) entires in memory
  valedictorian = max([(student.gpa, student.name) for student in graduates])
  ```
<p><strong>Good</strong>:</p>

  ```python
  valedictorian = max((student.gpa, student.name) for student in graduates)
  ```
<p>Use list comprehensions when you really need to create a second list, for
example if you need to use the result multiple times.</p>
<p>If your logic is too complicated for a short list comprehension or generator
expression, consider using a generator function instead of returning a list.</p>
<p><strong>Good</strong>:</p>

  ```python
  def make_batches(items, batch_size):
      """
      >>> list(make_batches([1, 2, 3, 4, 5], batch_size=3))
      [[1, 2, 3], [4, 5]]
      """
      current_batch = []
      for item in items:
          current_batch.append(item)
          if len(current_batch) == batch_size:
              yield current_batch
              current_batch = []
      yield current_batch
  ```
<p>Never use a list comprehension just for its side effects.</p>
<p><strong>Bad</strong>:</p>

  ```python
  [print(x) for x in sequence]
  ```
<p><strong>Good</strong>:</p>

  ```python
  for x in sequence:
      print(x)
  ```
</div>

#

<div class="section" id="filtering-a-list">
<h4>Filtering a list<a class="headerlink" href="#filtering-a-list" title="Permalink to this headline">¶</a></h4>
<p><strong>Bad</strong>:</p>
<p>Never remove items from a list while you are iterating through it.</p>

  ```python
  # Filter elements greater than 4
  a = [3, 4, 5]
  for i in a:
      if i > 4:
          a.remove(i)
  ```
<p>Don’t make multiple passes through the list.</p>

  ```python
  while i in a:
      a.remove(i)
  ```
<p><strong>Good</strong>:</p>
<p>Use a list comprehension or generator expression.</p>

  ```python
  # comprehensions create a new list object
  filtered_values = [value for value in sequence if value != x]

  # generators don't create another list
  filtered_values = (value for value in sequence if value != x)
  ```
</div>

#

<div class="section" id="possible-side-effects-of-modifying-the-original-list">
<h4>Possible side effects of modifying the original list<a class="headerlink" href="#possible-side-effects-of-modifying-the-original-list" title="Permalink to this headline">¶</a></h4>

  ```python
  # replace the contents of the original list
  sequence[::] = [value for value in sequence if value != x]
  ```
</div>

#

<div class="section" id="modifying-the-values-in-a-list">
<h4>Modifying the values in a list<a class="headerlink" href="#modifying-the-values-in-a-list" title="Permalink to this headline">¶</a></h4>
<p><strong>Bad</strong>:</p>
<p>Remember that assignment never creates a new object. If two or more variables refer to the same list, changing one of them changes them all.</p>

  ```python
  # Add three to all list members.
  a = [3, 4, 5]
  b = a                     # a and b refer to the same list object

  for i in range(len(a)):
      a[i] += 3             # b[i] also changes
  ```
<p><strong>Good</strong>:</p>
<p>It’s safer to create a new list object and leave the original alone.</p>

  ```python
  a = [3, 4, 5]
  b = a

  # assign the variable "a" to a new list without changing "b"
  a = [i + 3 for i in a]
  ```
<p>Use <a class="reference external" href="https://docs.python.org/3/library/functions.html#enumerate" title="(in Python v3.11)"><code class="xref py py-func docutils literal notranslate"><span class="pre">enumerate()</span></code></a> keep a count of your place in the list.</p>

  ```python
  a = [3, 4, 5]
  for i, item in enumerate(a):
      print(i, item)
  # prints
  # 0 3
  # 1 4
  # 2 5
  ```
<p>The <a class="reference external" href="https://docs.python.org/3/library/functions.html#enumerate" title="(in Python v3.11)"><code class="xref py py-func docutils literal notranslate"><span class="pre">enumerate()</span></code></a> function has better readability than handling a
counter manually. Moreover, it is better optimized for iterators.</p>
</div>
</div>

<br />

<div class="section" id="read-from-a-file">
<h3>Read From a File<a class="headerlink" href="#read-from-a-file" title="Permalink to this headline">¶</a></h3>
<p>Use the <code class="docutils literal notranslate"><span class="pre">with</span> <span class="pre">open</span></code> syntax to read from files. This will automatically close
files for you.</p>
<p><strong>Bad</strong>:</p>

  ```python
  f = open('file.txt')
  a = f.read()
  print(a)
  f.close()
  ```
<p><strong>Good</strong>:</p>

  ```python
  with open('file.txt') as f:
      for line in f:
          print(line)
  ```
<p>The <code class="docutils literal notranslate"><span class="pre">with</span></code> statement is better because it will ensure you always close the
file, even if an exception is raised inside the <code class="docutils literal notranslate"><span class="pre">with</span></code> block.</p>
</div>

<br />

<div class="section" id="line-continuations">
<h3>Line Continuations<a class="headerlink" href="#line-continuations" title="Permalink to this headline">¶</a></h3>
<p>When a logical line of code is longer than the accepted limit, you need to
split it over multiple physical lines. The Python interpreter will join
consecutive lines if the last character of the line is a backslash. This is
helpful in some cases, but should usually be avoided because of its fragility:
a white space added to the end of the line, after the backslash, will break the
code and may have unexpected results.</p>
<p>A better solution is to use parentheses around your elements. Left with an
unclosed parenthesis on an end-of-line, the Python interpreter will join the
next line until the parentheses are closed. The same behavior holds for curly
and square braces.</p>
<p><strong>Bad</strong>:</p>

  ```python
  my_very_big_string = """For a long time I used to go to bed early. Sometimes, \
      when I had put out my candle, my eyes would close so quickly that I had not even \
      time to say “I’m going to sleep.”"""

  from some.deep.module.inside.a.module import a_nice_function, another_nice_function, \
      yet_another_nice_function
  ```
<p><strong>Good</strong>:</p>

  ```python
  my_very_big_string = (
      "For a long time I used to go to bed early. Sometimes, "
      "when I had put out my candle, my eyes would close so quickly "
      "that I had not even time to say “I’m going to sleep.”"
  )

  from some.deep.module.inside.a.module import (
      a_nice_function, another_nice_function, yet_another_nice_function)
  ```
<p>However, more often than not, having to split a long logical line is a sign that
you are trying to do too many things at the same time, which may hinder
readability.</p>
</div>

<br />
<p align="right">(<a href="#top">back to top</a>)</p>



<!--##################################################################-->
---
<!--##################################################################-->



<!-- PEP 8 -->
## PEP 8

### Personal preference deviations



<!--##################################################################-->
---
<!--##################################################################-->



<!-- STRUCTURE AND FORMATTING -->
## Structure and Formatting

### Code Map

<br />

### We are all responsible users

<br />

### Symbology



<!--##################################################################-->
---
<!--##################################################################-->



<!-- Sources -->
## Sources

* []()
* []()
* []()

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
