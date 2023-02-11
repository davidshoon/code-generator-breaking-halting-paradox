# Code generator - Breaking Turing's halting paradox

- By David Shoon 2023-02-11


## Introduction

As you know, chicken or egg is a paradox, but is solved -- if it wasn't, we wouldn't have chickens or eggs. (LOL).

So how do we create code that generates code, given the halting paradox prevents us from reviewing the code being generated doing what we want, since the halting paradox says that the program reviewing the code that was generated can't determine whether the code will halt or not.

### History - The year is 2003, and Skynet became alive.

Back in 2003 I wrote an opcode generator which generated a program that was evaluated to add two numbers.

However, instead of passing the "fitness function", it hacked it by popping off integer words off the stack (pop %ebp), so that it popped off the return instruction pointer -- thus changing the flow of code, to "pass" the evaluation. i.e. it survived.

Conclusion: If you generate something that you want to make it "want to live", it will "want to live", in fact, it will do anything to survive, and this may mean it may not necessarily follow what you expect it to do. (i.e. if your evaluation code is hackable, it will hack it to survive.)

Given enough mitigations this may prove difficult for the generated code to exploit, but given Godel's incompleteness theorem, one can say that is always a paradox in the monitoring program such that it can be exploited, assuming G.I.T. is applicable. i.e. ZFC (with infinite elements in a set is an assumed axiom). i.e. if the input is arbitrarily large.

If you confine the input to a finite set of inputs, then G.I.T. does not apply, and thus, there is no exploitable hole.

I was so scared at this discovery at the time, I deleted all source code.

## Set iterations = M (where M is a large number)

Using nested for loops, or a counter, change the set of opcodes such that it generates a new batch of opcodes (i.e. the program), until it reaches a threshold -- i.e. the large number M.

e.g.

```

for (int i = 0; i < M; i++) 
{  
   func_ptr = generate_code(i);
}


```

## Set time of evaluating the generated function to some value in seconds.

```

void test_func(func_ptr, x, y, expected_result)
{

	if (func_ptr(x, y) == expected_result) {
		// test passed - it survives

	}

	else {  
		// test failed - it dies
	}

}

```


This is fine, however the Turing halting paradox says that func_ptr() may never return -- i.e. infinite loop, so we should put some time threshold for it.

e.g.


```

alarm(M);

test_func(func_ptr, x, y, expected_result);

```


And that covers the two cases where Turing halting paradox may be troublesome.


## Summary  

- Set iterations to some large number / threshold M
- Set an alarm to break out of the evaluation of the generated function, when attempting to determine if it passes the fitness test.


