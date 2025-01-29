# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.
Citations: To get more aquinted with this material I watched the following video https://www.bing.com/videos/search?view=detail&q=recurrence+analysis+explained&&mid=CFA473EE1A555E67A339CFA473EE1A555E67A339&mmscn=mtsc&&FORM=VRDGAR . I also learned more on recurrence analysis through changes being requested on divide and conquer, and applied that knowledge. I also reviewed the slides on sorting.

I submitted this work Fall 2024.

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.
T(n) = { 1, n <=1 3T(n/3) + n^(5), n > 1, since in this function there are 3 recursive calls, n going through the for loops is 5 times, and the data gets smaller by 1/3 with every recursive call. } 
T
(
n
)
=
3
T
(
n
/
3
)
+
n
5
 
T
(
n
/
3
)
=
3
T
(
n
/
3
/
3
)
+
(
n
/
3
)
5
 
T
(
n
)
=
3
(
3
T
(
n
/
9
)
+
(
n
5
/
243
)
)
+
n
5
 
=
9
T
(
n
/
9
)
+
n
5
/
81
+
n
5
 
T
(
n
/
9
)
=
3
T
(
n
/
3
/
9
)
+
(
n
/
9
)
5
 
T
(
n
)
=
9
(
3
T
(
n
/
27
)
+
(
n
/
9
)
5
)
+
(
n
5
/
81
)
+
n
5
 
=
27
T
(
n
/
27
)
+
(
n
5
/
6561
)
+
(
n
5
/
81
)
+
n
5
, since the middle values keep getting smaller, we can remove those from the equation. = 
(
3
i
)
T
(
n
/
3
i
)
+
n
5
, in this: 3^(i)T(n/3^(i)), the value in T will keep getting closer to 0 resulting in this also being able to be removed. So, 
O
(
n
5
)
