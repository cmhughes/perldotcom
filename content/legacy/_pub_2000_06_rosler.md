{
   "draft" : null,
   "authors" : [
      "joe-johnston"
   ],
   "slug" : "/pub/2000/06/rosler.html",
   "description" : " An Interview with HP's Larry Rosler Larry Rosler was both editor of the draft standard and chairman of the Language Subcommittee for X3J11. He helped put 'ANSI' in front of C. He is also just another Perl hacker. Larry...",
   "thumbnail" : null,
   "tags" : [],
   "title" : "ANSI Standard Perl?",
   "image" : null,
   "categories" : "community",
   "date" : "2000-06-06T00:00:00-08:00"
}



### An Interview with HP's Larry Rosler

*Larry Rosler was both editor of the draft standard and chairman of the Language Subcommittee for X3J11. He helped put 'ANSI' in front of C. He is also just another Perl hacker. Larry recently took time out of his busy schedule to share his thoughts on the value of standards, how Sun ought to handle Java and optimizing Perl code.*

**What's your background? How did you get interested in computers?**

**LR**: My formal education was in physics; my research field was experimental nuclear physics. However, I soon learned that I was more interested in the equipment used to gather and analyze the data than in the physics. The equipment was essentially a digital computer, but there were no degrees in computer science in those days.

In my first major job, with Bell Labs in New Jersey, I worked on solid-state devices. I found that simulation was faster than building and measuring test devices. When others began to use the programs I wrote, I realized that my greatest professional satisfaction would be as a software 'toolmaker'. So I switched to building tools such as graphical design terminals, and then focused on programming languages and libraries.

**I was taught by several "hardware" guys who got into programming somewhat reluctantly. Do you feel that novice programmers lose an important perspective without knowing what goes on under the hood?**

**LR**: I taught the first course on C at Bell Labs, using a draft of K&R, which helped vet the exercises. The students were hardware engineers who were being induced to learn programming. They found C (which is 'portable assembly language') much to their liking. Essentials such as pointers are very clear if you have a machine model in mind.

Perl is at a higher level of abstraction, so the machine model isn't as necessary *at first*. But when you get to complex data structures, which require references (which are like pointers in C, but much safer), a grounding in addressing becomes useful.

In an ideal world, a student would first learn an abstract assembly language such as MIX (see Knuth, Vol. 1), do some useful exercises, then take on a higher-level language with the machine model in the back of the head.

**When did you run into Perl? What did you think of the language the first time you saw it?**

**LR**: I am a relative latecomer to Perl. I was experimenting with CGI programming using shell scripts (!) because they were better for rapid prototyping than C. Soon I discovered that Perl offered advantages similar to the shell, but was much more expressive (particularly in the manipulation of data structures) and much faster to execute.

Because of my familiarity with Unix commands such as 'sed', which made heavy use of regular expressions, and because of my C experience, I was quite comfortable with Perl syntax. The hardest adjustment was to learn to write code with as few Perl operations as possible, because of the costs of dispatching each instruction. The Benchmark module became the most important tool I used to learn how to write efficient (and hence, sometimes elegant) Perl. I also learned a lot from the newsgroup comp.lang.perl.misc, to which I eventually became able to contribute.

**Often Perl claims to be efficient in the scarce resource of the programmer's time. It isn't often that people tune scripts for optimum performance. Are there a few tips you can give to new Perl programmers on how squeak out a little better runtime performance?**

**LR**: 'Script' `ne` 'program'. When dealing with data sets that will grow (one hopes and expects), performance becomes important. I proposed a tutorial to Perl Conference 4.0 this year on this subject, but it wasn't accepted. Maybe next year.

-   0. Don't optimize prematurely!
-   1. Don't use an external command where Perl can do a task internally.
-   2. Refine the data structures and algorithms. References: The Practice of Programming (Kernighan and Pike), Programming Pearls (Bentley), Algorithms with Perl (Orwant et al).
-   3. After these are optimal, identify the remaining hot spots. (Judicious use of the time() and times() functions, or the Benchmark module.)
-   4. Try to improve the hot spots by using functions such as map() and grep() instead of explicit loops; make regexes more explicit to minimize backtracking; cache intermediate results to avoid unnecessary recalculation (memoization), ...

**What's your favorite part of programming? Design or implementation (or other)?**

**LR**: Happy users.

**I understand you were the Chairman of the ANSI C committee. How did that come about?**

**LR**: Not the chairman -- that was primarily an administrative function, and what I did was more technical. I was the chairman of one of the three major subcommittees (Language; the others were Library and Environment), and -- most important -- I was the editor of the Draft Standard. The hand that holds the pen controls the direction of the work and the results. `:-)`

This all happened because at Bell Labs I was one of the managers of the effort to turn C from a research vehicle to a commercially useful language, which began with internal standardization. Because of the demands of some major users, such as the US Government, commercialization required the development of a formal standard. My colleague Dennis Ritchie (who created C) didn't want to participate personally, but he was always active behind the scenes in reviewing and improving my efforts. He was quite satisfied with the final results.

A few years later, now working at Hewlett Packard, I found myself in the same position regarding C++. I persuaded Bjarne Stroustrup, the creator of C++, to support standardization, as a prerequisite for successful commercialization. He agreed, and took a very active role.

**There's certainly no ANSI Perl. Does Perl need the same kind of official standardization that C got?**

**LR**: I believe that it does, in order to increase its acceptability. Many organizations either cannot or will not endorse the use of unstandardized languages in their business-critical activities.

The current situation with Perl is better than it was with the other two languages I mentioned. Perl has one official open source for its implementation, whereas the others had multiple proprietary implementations, leading to different semantics for many language features. But this single 'official' Perl semantics has never been adequately characterized independent of the implementation, so is subject to arbitrary change.

Building on quicksand is acceptable for 'scripts' of limited longevity and applicability. It is not acceptable for 'programs' of significant commercial value. I think the lack of a firm, stable, well-defined foundation is the major inhibitor for the continuing commercial evolution of Perl. Of the major contributors to Perl, Ilya Zakharevitch is most outspoken in his view that Perl is not (yet?) a 'programming' language!

Many of the people who contribute their efforts to the Perl community are interested in adding features, perhaps to overflowing. More people should devote their attention to firming up the semantics and making sure that the implementation conforms to those semantics, rather than the other way around.

**Your point is well taken about focusing future Perl development on producing consistent semantics. I'm a bit surprised that you see this as a barrier to greater Perl acceptance. Some might suggest the interpretive nature of the language is a greater barrier ("Why can't I get a hello.pl.exe?").
Or point to Perl's endearingly unique syntax.
Or to Perl's charmingly permissive OO implementation.
Are there particular areas of Perl's semantics in which the inconsistencies are glaring?**

**LR**: I am less concerned about individual programmers' decisions for their own projects and more concerned about major corporations or government agencies that reject Perl because of lack of formal support and lack of standardization.

An example of excellent work that is long overdue is Ilya's document 'perlnumber', new in Perl 5.6.0, which specifies for the first time the semantics of Perl's string-to-number conversions.

**I'm curious how one would standardize Perl when the language changes so quickly and committees move so slowly. Consider that three years ago, Perl was not threaded. Now, threads are standard, but their interface may change in the near future. Mr. Zakharevich continues to pull new regex constructs from head of Zeus. Even more striking, Perl supports unicode. Is there some way to stage the standardization so that it isn't painfully out-of-date? Would standardization necessarily slow down perl development?**

**LR**: Sometimes standardization speeds up development, by forcing convergence on a specified way of doing things. Sometimes features are characterized and implemented during standardization (wide-character types for C, for example; the Standard Template Library and many other features for C++).

One way to view it is re Samuel Johnson's famous mot: "When a man knows he is to be hanged in a fortnight, it concentrates his mind wonderfully."

**Are you following the debate amongst programmers who favor Sun lessening their control over Java (especially after Sun withdrew it from the [independent standardization process](http://www.zdnet.com/eweek/stories/general/0,11011,2405787,00.html))? Do you feel Java might benefit from a more open/chaotic development model (ala Perl), should it follow the C path of getting independent standardization, or is Sun doing the best thing for the language by keeping it "in-house"?**

**LR**: My prejudice should be clear from what I have already written. AT&T handed control over C and C++ to ANSI/ISO technical committees, while keeping an active leadership role to ensure that the goals of the originators of the languages were met. Sun should do the same.

On the other hand, Microsoft's desire to 'embrace and extend' Java should be doomed by standardization, just as they failed to subvert the target independence of C and C++.

**My understanding is that Microsoft is 'embracing' ActiveState's Perl. They will be shipping Perl with their "Services for UNIX 2.0". Do you see any chance for Perl to compete on a Windows Platform as a replacement for Visual Basic? In particular, as application "glue"?**

**LR**: Why not? Perl is superior to Visual Basic in every way imaginable.

Maybe a push from Microsoft will help overcome the barrier of acceptability that I focused on above.

**Back to Java for a moment. Because they are both "web technologies", Perl and Java are often seen as competitors. There have been attempts, like Larry Wall's JPL, to provide better integration between these two beasties. What sort of utility do you see in such a marriage?**

**LR**: Hard for me to say. Java forces OO programming from the beginning, and I have never needed to write an object in any program. This may be for me a conceptual hurdle that I need not overcome.

C++ provides sweetened C syntax and semantics (particularly toward bits and bytes), generic programming (templates), and OO if you want it. This can all be done with almost the efficiency of C.

Perl provides higher-level syntax and semantics (particularly toward strings and complex data structures), and OO if you want it. I know how to write efficient Perl when I have to.

Java, in my opinion, fills a much-needed gap between those two approaches. `:-)`

**Speaking of competitors, Python is making a big splash this year. Although it seems to satisfy many of the same itches Perl does, its proponents point to its cleaner syntax and more tradition OO implementation as making it a "better Perl". What are your thoughts on Python?**

**LR**: Whatever improvements Python may offer are not sufficient to give it a critical mass of programmers and programming support relative to Perl. There is an order-of-magnitude difference in this metric (programmers, modules, books, ...), and I don't think significant inroads are being made. And, as I said, to me OO is a big yawner.

**What five people would you like to see learn Perl?**

**LR**: Hah! Some colleagues are now trying to convince me to move on to Python. `:-)`

**Have you had the chance to read Mr. Conway's \_Object Oriented Perl\_? I found I learned more about general Perl from it than OO techniques (which by no means is to say book is inadequate in the latter department).**

**LR**: Yes. It is a fine book. But it still didn't convince me about the necessity of objects. All I see is the performance-damaging complexity of the interfaces.

**How much longer do you see the "Internet Goldrush" continuing?**

**LR**: Judging by the recent performance of the NASDAQ, it may be over already.

**You presented a paper at TPC on efficient sorting with Uri Guttman, a fellow Boston Perl Monger. How did you two meet?**

**LR**: We met in comp.lang.perl.misc in March 1998 (soon after I began to post questions to the newsgroup). Uri educated me on 'hash slices', which he eventually turned into a tutorial. That July, I spotted his and his wife's names in the credits at the end of a movie, which exposed a common non-Perl interest (in Jews and Buddhism, to be specific). We met for the first time at TPC2 in San Jose that August.

The paper on sorting was developed entirely by email. The next time we met in person -- together with Damian Conway and our wives -- was at TPC3 in Monterey. We will meet again there at TPC4 this summer. Each of us is working on the Perl Golf tournament, which Uri organized.

**Do you have any tips for new programmers dealing with management?**

**LR**: Agree on useful metrics for progress and completion. Never report that your code is 90% complete, 90 days from completion, because that tends to be a steady-state description.

Never estimate more than about half your time actually working on the project, because other things will always happen.

**Has this rapid web development trampled on software quality control irreparably?**

**LR**: Not only the web -- Microsoft. Who would have imagined that the world would tolerate an environment with the dismal quality of Windows? So now every company, even those such as Hewlett Packard with long-standing reputations for high quality, has to compromise in order to compete in a timely way.

**Since you've in the business for a respectable number of years, what are your five biggest pet peeves about programming?**

**LR**: That's a toughie. How about four, in no particular order:

-   Extracting from the potential user a complete and useful specification of a problem.
-   Coping with buggy or inadequately documented tools.
-   Keeping things functioning as operating environments evolve. (No one wants anything to change except the things that that person wants changed. `:-)`
-   As I said above, evaporating expectations of quality.
    (1980's paradigm: If it's worth implementing once, it's worth implementing twice.
    1990's paradigm: Ship the prototype!
    2000's paradigm: Ship the idea!)

