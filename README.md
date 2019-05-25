
<html>
<head><title>The Syntax Analyzer</title><head>
<body>
<br><br>
<p>Implement a parser for the language C Minus which is defined in your textbook. 
  The grammar is given below.</p>
<h2 align="center">C minus Grammar</h2>
<pre>
&lt;program&gt; -&gt; &lt;declaration-list&gt;
&lt;declaration-list&gt; -&gt; &lt;declaration-list&gt; &lt;declaration&gt; | &lt;declaration&gt;
&lt;declaration&gt; -&gt; &lt;var-declaration&gt; | &lt;fun-declaration&gt;
&lt;var-declaration&gt; -&gt; &lt;type-specifier&gt; <b>ID ;</b> | &lt;type-specifier&gt; <b>ID [ NUM ] ;</b>
&lt;type-specifier&gt; -&gt; <b>INT</b> | <b>VOID</b>
&lt;fun-declaration&gt; -&gt; &lt;type-specifier&gt; <b>ID (</b> &lt;params&gt; <b>)</b> &lt;compound-stmt&gt;
&lt;params&gt; -&gt; &lt;param-list&gt; | <b>VOID</b>
&lt;param-list&gt; -&gt; &lt;param-list&gt; <b>,</b> &lt;param&gt; | &lt;param&gt;
&lt;param&gt; -&gt; &lt;type-specifier&gt; <b>ID</b> | &lt;type-specifier&gt; <b>ID [ ]</b>
&lt;compound-stmt&gt; -&gt; <b>{</b> &lt;local-declarations&gt; &lt;statement-list&gt; <b>}</b>
&lt;local-declarations&gt; -&gt; &lt;local-declarations&gt; &lt;var-declaration&gt; | &lt;empty&gt;
&lt;statement-list&gt; -&gt; &lt;statement-list&gt; &lt;statement&gt; | &lt;empty&gt;
&lt;statement&gt; -&gt; 	&lt;expression-stmt&gt; | &lt;compound-stmt&gt; | &lt;selection-stmt&gt;
              | &lt;iteration-stmt&gt; | &lt;return-stmt&gt;
&lt;expression-stmt&gt; -&gt; &lt;expression&gt; <b>;</b> | <b>;</b>
&lt;selection-stmt&gt; -&gt; <b>IF (</b> &lt;expression&gt; <b>)</b> &lt;statement&gt;
                  | <b>IF (</b> &lt;expression&gt; <b>)</b> &lt;statement&gt; ELSE &lt;statement&gt;
&lt;iteration-stmt&gt; -&gt; <b>WHILE  (</b> &lt;expression&gt; <b>)</b> &lt;statement&gt;
&lt;return-stmt&gt; -&gt; <b>RETURN ;</b> | <b>RETURN</b> &lt;expression&gt; <b>;</b>
&lt;expression&gt; -&gt; &lt;var&gt; <b>=</b> &lt;expression&gt; | &lt;simple-expression&gt;
&lt;var&gt; -&gt; <b>ID</b> | <b>ID [</b> &lt;expression&gt; <b>]</b>
&lt;simple-expression&gt; -&gt; &lt;additive-expression&gt; &lt;relop&gt; &lt;additive-expression&gt;
                     | &lt;additive-expression&gt;
&lt;relop&gt; -&gt; <b>&lt;</b> | <b>&lt;=</b> | <b>&gt;</b> |<b>&gt;=</b> | <b>==</b> |<b>!=</b>
&lt;additive-expression&gt; -&gt; &lt;additive-epxression&gt; &lt;addop&gt; &lt;term&gt; | &lt;term&gt;
&lt;addop&gt; -&gt; <b>+</b> | <b>-</b>
&lt;term&gt; -&gt; &lt;term&gt; &lt;mulop&gt; &lt;factor&gt; | &lt;factor&gt;
&lt;mulop&gt; -&gt; <b>*</b> | <b>/</b>
&lt;factor&gt; -&gt; <b>(</b> &lt;expression&gt; <b>)</b> | &lt;var&gt; | &lt;call&gt; | <b>NUM</b>
&lt;call&gt; -&gt; <b>ID (</b> &lt;args&gt; <b>)</b>
&lt;args&gt; -&gt; &lt;arg-list&gt; | &lt;empty&gt;
&lt;arg-list&gt; -&gt; &lt;arg-list&gt; <b>,</b> &lt;expression&gt; | &lt;expression&gt;
</pre>
<h2 align="center">Other Requirements</h2>
<ol>
<li>
    <p>Modify the grammar for C Minus in any and all appropriate ways needed to 
      create a predictive single-lookahead recursive-descent parser as discussed 
      in class.</p>
<li><p>Rewrite the modified grammar for C Minus in EBNF.</p>
<li><p>Draw all syntax charts related to the modified grammar. Your parser should be
implemented directly from these syntax charts.</p>
<li><p>Modify your compiler as needed so that the parser is called.</p>
<li><p>Create a <em>void printTree(SyntaxTree tree)</em> routine that
produces output similar to the author's <em>printTree</em> routine used
in the compiler for the language <em>Tiny</em>.</p>
<li><p>Add the global/class variable <em>parseTrace</em>. When true this flag causes 
a printout (in file <em>Listing.txt</em>) of the syntax tree created by the parser.
For this assignment set <em>parseTrace</em> to true and <em>scanTrace</em> to false.</p>
<li><p>Your source code should be properly documented.</p>
</ol>

<h2 align="center">What Must Be Turned In</h2>
<ol>
<li><p>You must turn in a copy of the modified grammar for C Minus written in EBNF. 
To get credit the grammar must be typed.</p>
<li><p>You must turn in a copy of all the syntax charts, where each chart is preceded
by the C Minus grammar production with which it is associated. To get credit this must be
either created with a software tool or produced carefully and neatly by hand.</p>
<li><p>Program test runs and copies of program code must all be put together during
a unix script session. The resulting script file should be turned in along with your grammar
written in EBNF and your syntax charts. As mentioned earlier the grammar must be typed and the
syntax charts should be created using a tool or drawn carefully and neatly by hand.
This will include the following information:</p>
  <ol type="a">
  <li><p>A copy of each source code file that is part of your compiler unit, syntax tree and parser.</p>
  <li><p>Evidence that all files compile without errors or warnings.</p>
  <li><p>Evidence that the parser works correctly. This will be provided by including a copy of the 
         file <i>Listing.txt</i> that is created after each source code test file is parsed by your program. 
		 (The test files are given below.)</p>
  </ol>
<li><p>A sample unix script session is given below. It assumes that the source code files for my 
       parser project are <em>Scanner.java</em>, <em>Defs.java</em>, <em>Compiler.java</em>, 
	   <em>Parser.java</em>, and <em>SyntaxTree.java</em>. It also assumes that the 
	   <em>parseTrace</em> variable is set to true.	Finally, the script below assumes
	   that the nine test files <em>ptest1.c</em> through <em>ptest9.c</em> (given below) 
	   reside in my directory.
<pre>
   script
   cat SyntaxTree.java
   cat Parser.java
   cat Defs.java
   cat Compiler.java
   javac Scanner.java
   javac Defs.java
   javac Compiler.java
   javac SyntaxTree.java
   javac Parser.java
   cat ptest1.c
   java Compiler ptest1.c
   cat Listing.txt
   cat ptest2.c
   java Compiler ptest2.c
   cat Listing.txt
   cat ptest3.c
   java Compiler ptest3.c
   cat Listing.txt
   cat ptest4.c
   java Compiler ptest4.c
   cat Listing.txt
   cat ptest5.c
   java Compiler ptest5.c
   cat Listing.txt
   cat ptest6.c
   java Compiler ptest6.c
   cat Listing.txt
   cat ptest7.c
   java Compiler ptest7.c
   cat Listing.txt
   cat ptest8.c
   java Compiler ptest8.c
   cat Listing.txt
   cat ptest9.c
   java Compiler ptest9.c
   cat Listing.txt
   exit
<pre>
</ol>

<h2 align="center">The Test Files</h2>
<pre>
/*
   Test File ptest1.c - CSE 481 - Spring 2002
*/

void main(void)
{
   int x;
   int y;
   int z;
   output(x=y=z=20);
}
</pre>
<hr>
<pre>
/*
   Test File ptest2.c - CSE 481 - Spring 2002
*/

void main(void)
{
   int x;
   int y;
   x = 10;
   y = 20;
   if(x<0) if(y>0) output(y/x); else output(y); 
}
</pre>
<hr>
<pre>
/*
   Test File ptest3.c - CSE 481 - Spring 2002
*/

void main(void)
{
   int x;
   x = 0;
   while(x < 10)
   {
      output(x);
      x = x + 1;
   }
}
</pre>
<hr>
<pre>
/*
   Test File ptest4.c - CSE 481 - Spring 2002
*/

void main(void)
{
   int x;
   int y;
   int z;
   x = 1;
   y = 2;
   z = 3;
   output(x+y*z-x/z);
}
</pre>
<hr>
<pre>
/*
   Test File ptest5.c - CSE 481 - Spring 2002
*/

int foo(int num)
{
   return num + 5 * num;
}

void main(void)
{
   int x;
   x = 5;
   output(foo(x));
}
</pre>
<hr>
<pre>
/*
   Test File ptest6.c - CSE 481 - Spring 2002
*/

int x[2];
int y;

void main(void)
{
   x[0] = 1;
   x[1] = 2;
   y = x[1];
   output(y);
}
</pre>
<hr>
<pre>
/*
   Test File ptest7.c - CSE 481 - Spring 2002
*/

void foo(int nums[], int index)
{
   output(nums[index]);
}

void main(void)
{
   int x[2];
   x[0] = 1;
   x[1] = 2;
   foo(x,0);
}
</pre>
<hr>
<pre>
/*
   Test File ptest8.c - CSE 481 - Spring 2002
*/

void main(void)
{
   int x;
   int y;
   int r;
   x = 7;
   y = 5;

   r = (((x+1))*((x/(x-y))));
   output(r);
}
</pre>
<hr>
<pre>
/*
   Test File ptest9.c - CSE 481 - Spring 2002
*/

void foo(void)
{
}

void main(void)
{

}
</pre>
</body>
</html>
