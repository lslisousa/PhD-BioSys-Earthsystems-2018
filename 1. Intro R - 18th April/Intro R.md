## Intro R - Guided Exercises

**Basic Operations**

* Create a vector \texttt{w} with the components 1,-1,2,-2.
```r
w<-c(1,-1,2,-2)
```

* Print that vector in the \texttt{R} console.
```r
w
```
* Obtain a description of \texttt{w} by using function \texttt{str()}.
```r
str(w)
```
* Create vector \texttt{w+1} and print it in the \texttt{R} console.
```r
x<-w+1; x
```
* Create vector (0,1,5,10,15,...,75) by using functions \texttt{c()} and \texttt{seq()}.
```r
s<-seq(5,75,by=5)
j<-c(0,1,s);j
```
* Construct an alphanumeric vector with the labels "Patient", "Entry number"\, and "Disease", with separator ":", and dimension 10.
```r
S<-paste("Patient","Entry number","Disease",sep=":",1:10)
```
* Consider x=4 (\texttt{x<-4}), and check the following conditions:
a) x>23
```r
a <- x>23
```
b) $x\in[-1,10]$
```r
b <- x>=-1 \& x<=10
```
c) $x=3$
```r
c<-x==3
```
d) $x\leq 45$
```r
d <- x<=45
```
* Indicate the logical conditions:
i. a) $\wedge$ b)
```r
a&b
```
ii. b) $\vee$ c)
```r
b|c
```
iii. d) $\wedge$ b)
```r
d&b
```

\item[]\hspace{-0.7cm}{\bf Vectors, Matrices and Data Frames}

\item Create a numeric vector, a \emph{string} (character) vector and a logical vector:\\
\texttt{num.vec <- c(3,4,2,6,20)\\
char.vec <- c("koala","kangaroo","monkey")\\
logic.vec <- c(F,F,T,T)}
  \item Create the vector \textbf{y}=(0, 4, 2, 1, 0, 4, 0, 3, 0, 3, 3, 3, 4, 4, 2, 2, 0) and print it in the \texttt{R} console.\\
\texttt{y<-c(0, 4, 2, 1, 0, 4, 0, 3, 0, 3, 3, 3, 4, 4, 2, 2, 0)}\\
\texttt{y}
\begin{enumerate}
  \item Search for elements of \textbf{y} which are less or equal than 3.\\
\texttt{y[y<=3]}
  \item Search for elements of \textbf{y} equal to 0.\\
\texttt{y[y==0]}
  \item Search for components different form 0.\\
  \texttt{y[y!=0]}
  \item How many elements of \textbf{y} are lower than 3?\\
\texttt{length(y[y<3])}
\end{enumerate}

  \item Consider the following vector: (12,14,35,7,6,12,5,22,7,17,9,11).
  \begin{enumerate}
  \item Use this vector to build a matrix (by column) of order $3\times4$ and print it in the \texttt{R} console.\\
 \texttt{m<-matrix(c(12,14,35,7,6,12,5,22,7,17,9,11),ncol=4)}\\
 \texttt{m}
  \item What is the element of matrix \texttt{m}, which is in position "line 2, column 3"?\\
  \texttt{m[2,3]}
  \end{enumerate}

  \item Consider the following table:

  \begin{tabular}{|c|c|c|}
    \hline
    % after \\: \hline or \cline{col1-col2} \cline{col3-col4} ...
    student nr. & class & marks \\\hline
    2355& tp1 & 0.3\\
 3456 &tp1& 9.3\\
  2334 &tp2& 14.2\\
   5456 &tp3 &15.0\\
    \hline
  \end{tabular}
  \begin{enumerate}
\item Put the table into a data frame.
\texttt{final.marks<- data.frame(stud = c(2355, 3456, 2334, 5456),}\\
\texttt{class = c("tp1", "tp1", "tp2", "tp3"),}\\
\texttt{marks = c(10.3,9.3,14.2,15))}\\
\texttt{final.marks}

  \item What is the element in line 2 and column 2?\\
\texttt{final.marks[2,2]}

  \item Access the column corresponding the students' number.\\
\texttt{final.marks\$stud}

  \item What is the information obtained from the data frame
  \texttt{final.marks} when we execute the following commands?\\
  \texttt{final.marks[final.marks\$marks > 10, ]}\\
 \texttt{final.marks[final.marks\$marks > 14, "stud"]}\\
\texttt{final.marks[final.marks\$class == "tp1", c("stud", "marks")]}

  \item Execute the function which allows you to access the columns of the data frame directly.\\
 \texttt{attach(final.marks)}

  \item Insert a new column corresponding to the final results: "approved", "oral", "approved", "approved"\, (use function \texttt{edit()}).\\
  \texttt{final.marks<-edit(final.marks)}

  \item Print the variables' names of the data frame.\\
  \texttt{names(final.marks)}
\end{enumerate}

\pagebreak
\item[]\hspace{-0.7cm}{\bf Graphical Functions}

\item Consider the data frame \texttt{births} of package \texttt{Epi}. This database concerns births of babies in a hospital in England.\\

\begin{enumerate}
\item Identify the variables in the data frame \texttt{births}.\\
  \texttt{library(Epi)}\\
  \texttt{data(births)}\\
  \texttt{str(births)}


\item Analyse the relation between the weight of babies and the gestational week, of the data frame \texttt{births}.\\
  \texttt{attach(births)}\\
  \texttt{plot(gestwks,bweight)}

\item Plot the age of the mother \textit{vs}. the weight of the babies.\\
  \texttt{plot(matage,bweight)}\\
  \texttt{plot(matage,bweight,xlab="Mother age", ylab="Babies weight")}

\item Change the points color into green circles.\\
  \texttt{plot(matage,bweight,pch=19,col="green")}

 \item Consider the graph '\texttt{plot(gestwks,bweigth)}'. Use different color for baby girls and baby boys:\\
\texttt{plot(gestwks,bweight)}\\
\texttt{points(gestwks[sex==1],bweight[sex==1],col="blue")}\\
\texttt{points(gestwks[sex==2],bweight[sex==2],col="red")}

  \item Include a legend and a title.\\
  \texttt{legend("topleft",pch=1,legend=c("Baby boys","Baby girls"),\\
  col=c("blue","red"))}\\
  \texttt{title("Birth weight vs. gestational week (500 births)")}

\item Save the graphic into a \texttt{.pdf} file. \\
 \texttt{Graph window - Export - Save as pdf}
\end{enumerate}


\newpage\item[]\hspace{-0.7cm}{\bf Loops and Functions}

\item (a) Create a loop, using the \texttt{for()} function, that, given a numeric vector prints a number per line along with its square and its cube.
\begin{verbatim}
x<-c(1,3,5)  # for example
n<-length(x)
for(i in 1:n)
  cat(x[i],' square =',x[i]^2,'; cube =',x[i]^3,"\n")
\end{verbatim}

(b) Use function \texttt{while()} in order to reach the same result.
\begin{verbatim}
i<-1   # initialize counter
while(i<(n+1))
  {
  cat(x[i],' square =',x[i]^2,'; cube =',x[i]^3,"\n")
  i<-i+1
  }
\end{verbatim}

\item Write a function that takes a single argument: a matrix. The function should return a matrix, identical to the original, but in which every odd number is duplicated. For example, the function applied to matrix
\[ \left[ \begin{array}{ccc}
1 & 1 & 3 \\
5 & 2 & 6 \\
-2 & -1 & -3 \end{array} \right]\]
is converted into
\[ \left[ \begin{array}{ccc}
2 & 2 & 6 \\
10 & 2 & 6 \\
-2 & -2 & -6 \end{array} \right]\]

\begin{verbatim}
Func <- function(mat)
  {
  mat[mat%%2 == 1] <- 2 * mat[mat%%2 == 1]
  mat
  }
mat<-matrix(c(1,5,-2,1,2,-1,3,6,-3),3,3)
Func(mat)
\end{verbatim}
\vspace{-0.2cm}{\small{\footnotesize NOTE:} The operator \texttt{\%\%} returns the reminder of division, e.g., \texttt{5\%\%2} = 1.}

  | Genotype  | Frequency | Probability                     |
  |-----------|-----------|---------------------------------|
  | AABB      |    11     | ![](http://latex.codecogs.com/gif.latex?%24%281-%5Ctheta%29%5E2/4%24)               |
  | AABb      |    14     | ![](http://latex.codecogs.com/gif.latex?%24%5Ctheta%281-%5Ctheta%29/2%24)           |
  | AAbb      |     1     | ![](http://latex.codecogs.com/gif.latex?%24%5Ctheta%5E2/4%24)                    |
  | AaBB      |    10     | ![](http://latex.codecogs.com/gif.latex?%24%5Ctheta%281-%5Ctheta%29/2%24)            |
  | AaBb      |    27     | ![](http://latex.codecogs.com/gif.latex?%24%28%5Ctheta%5E2/2%29&plus;%5B%281-%5Ctheta%29%5E2%5D/2%24) |
  | Aabb      |    12     | ![](http://latex.codecogs.com/gif.latex?%24%5Ctheta%281-%5Ctheta%29/2%24)             |
  | aaBB      |     3     | ![](http://latex.codecogs.com/gif.latex?%24%5Ctheta%5E2/4%24)                    |
  | aaBb      |    13     | ![](http://latex.codecogs.com/gif.latex?%24%5Ctheta%281-%5Ctheta%29/2%24)             |
  | aabb      |    11     | ![](http://latex.codecogs.com/gif.latex?%24%281-%5Ctheta%29%5E2/4%24)                 |

