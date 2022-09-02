## 0x18. C - Stacks, Queues - LIFO, FIFO
  <h4 class="task">
    0. push, pall
      <span class="alert alert-warning mandatory-optional">
        mandatory
      </span>
  </h4>


  <!-- Progress vs Score -->

<!-- Task Body -->
  <p>Implement the <code>push</code> and <code>pall</code> opcodes.</p>

<p><strong>Monty byte code files</strong></p>

<p>Files containing Monty byte codes usually have the <code>.m</code> extension. Most of the industry uses this standard but it is not required by the specification of the language.
There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:</p>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat -e bytecodes/000.m
push 0$
push 1$
push 2$
  push 3$
                   pall    $
push 4$
    push 5    $
      push    6        $
pall$
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$
</code></pre>

<p>Monty byte code files can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:</p>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat -e bytecodes/001.m
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$
$
push 2$
  push 3$
                   pall    $
$
$
                           $
push 4$
$
    push 5    $
      push    6        $
$
pall This is the end of our program. Monty is awesome!$
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$
</code></pre>

<p><strong>The monty program</strong></p>

<ul>
<li>Usage: <code>monty file</code></li>
<li>where <code>file</code> is the path to the file containing Monty byte code</li>
<li>If the user does not give any file or more than one argument to your program, print <code>USAGE: monty file</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code></li>
<li>If, for any reason, it&#39;s not possible to use read the file, print <code>Error: Can&#39;t open file &lt;file&gt;</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code>

<ul>
<li>where <code>&lt;file&gt;</code> is the name of the file</li>
</ul></li>
<li>If the file contains an invalid instruction, print <code>L&lt;line_number&gt;: unknown instruction &lt;opcode&gt;</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code>

<ul>
<li>where <line_number> is the line number where the instruction appears. Line numbers always start at 1</li>
</ul></li>
<li>The monty program runs the bytecodes line by line and stop if:

<ul>
<li>it executed properly every line of the file</li>
<li>or it finds an error in the file</li>
<li>or an error occured</li>
</ul></li>
<li>If you can&#39;t malloc anymore, print <code>Error: malloc failed</code>, followed by a new line, and exit with status <code>EXIT_FAILURE</code>. You have to use <code>malloc</code> and <code>free</code> and are not allowed to use any other function from <code>man malloc</code></li>
</ul>

<p><strong>The push opcode</strong></p>

<p>The opcode <code>push</code> pushes an element to the stack.</p>

<ul>
<li>Usage: <code>push &lt;int&gt;</code></li>
<li>where <code>&lt;int&gt;</code> is an integer</li>
<li>if <code>&lt;int&gt;</code> is not an integer or if there is no argument to <code>push</code>, print the message <code>L&lt;line_number&gt;: usage: push integer</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code>

<ul>
<li>where <line_number> is the line number in the file</li>
</ul></li>
<li>You don&#39;t have to deal with overflows. Use the <code>atoi</code> function</li>
</ul>

<p><strong>The pall opcode</strong></p>

<p>The opcode <code>pall</code> prints all the values on the stack, starting from the top of the stack.</p>

<ul>
<li>Usage <code>pall</code></li>
<li>Format: see example</li>
<li>If the stack is empty, don&#39;t print anything</li>
</ul>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat -e bytecodes/00.m
push 1$
push 2$
push 3$
pall$
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ ./monty bytecodes/00.m
3
2
1
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$
</code></pre>

  <h4 class="task">
    1. pint
      <span class="alert alert-warning mandatory-optional">
        mandatory
      </span>
  </h4>


  <!-- Progress vs Score -->

<!-- Task Body -->
  <p>Implement the <code>pint</code> opcode.</p>

<p><strong>The pint opcode</strong></p>

<p>The opcode <code>pint</code> prints the value at the top of the stack, followed by a new line.</p>

<ul>
<li>Usage: <code>pint</code></li>
<li>If the stack is empty, print <code>L&lt;line_number&gt;: can&#39;t pint, stack empty</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code></li>
</ul>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat bytecodes/06.m 
push 1
pint
push 2
pint
push 3
pint
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ ./monty bytecodes/06.m 
1
2
3
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ 
</code></pre>

  <h4 class="task">
    2. pop
      <span class="alert alert-warning mandatory-optional">
        mandatory
      </span>
  </h4>


  <!-- Progress vs Score -->

<!-- Task Body -->
  <p>Implement the <code>pop</code> opcode.</p>

<p><strong>The pop opcode</strong></p>

<p>The opcode <code>pop</code> removes the top element of the stack.</p>

<ul>
<li>Usage: <code>pop</code></li>
<li>if the stack is empty, print <code>L&lt;line_number&gt;: can&#39;t pop an empty stack</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code></li>
</ul>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat bytecodes/07.m 
push 1
push 2
push 3
pall
pop
pall
pop
pall
pop
pall
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ ./monty bytecodes/07.m 
3
2
1
2
1
1
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ 
</code></pre>

  <h4 class="task">
    3. swap
      <span class="alert alert-warning mandatory-optional">
        mandatory
      </span>
  </h4>


  <!-- Progress vs Score -->

<!-- Task Body -->
  <p>Implement the <code>swap</code> opcode.</p>

<p><strong>The swap opcode</strong></p>

<p>The opcode <code>swap</code> swaps the top two elements of the stack.</p>

<ul>
<li>Usage: <code>swap</code></li>
<li>If the stack is less than two element long, print <code>L&lt;line_number&gt;: can&#39;t swap, stack too short</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code></li>
</ul>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat bytecodes/09.m 
push 1
push 2
push 3
pall
swap
pall
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ ./monty bytecodes/09.m 
3
2
1
2
3
1
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ 
</code></pre>

  <h4 class="task">
    4. add
      <span class="alert alert-warning mandatory-optional">
        mandatory
      </span>
  </h4>


  <!-- Progress vs Score -->

<!-- Task Body -->
  <p>Implement the <code>add</code> opcode.</p>

<p><strong>The add opcode</strong></p>

<p>The opcode <code>add</code> adds the top two elements of the stack.</p>

<ul>
<li>Usage: <code>add</code></li>
<li>If the stack is less than two element long, print <code>L&lt;line_number&gt;: can&#39;t add, stack too short</code>, followed by a new line, and exit with the status <code>EXIT_FAILURE</code></li>
<li>The result is stored in the second top element of the stack, and the top element is removed, so that at the end:

<ul>
<li>the top element of the stack contains the result</li>
<li>the stack is one element shorter</li>
</ul></li>
</ul>

<pre><code>julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ cat bytecodes/12.m 
push 1
push 2
push 3
pall
add
pall

julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$ ./monty bytecodes/12.m 
3
2
1
5
1
julien@ubuntu:~/0x18. Stack (LIFO) &amp; queue (FIFO)$
</code></pre>

  <h4 class="task">


## authors
````
* david perlaza @davidperlaza14
davidperlaza14@gmail.com

