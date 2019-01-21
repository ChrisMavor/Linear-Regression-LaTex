# Linear-Regression-LaTex
Project file written in LaTeX to display a Matlab project
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%% The following is a sample document that I have created using LateX to display my final project from my computational math class. 
 % The project deals with Least Square Regression for Numerical Analysis.
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%% Preamble                                                           %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%% The preamble tells the program that you are using how to set up the 
%% document and calls any necessary packages. The packages that you
%% load are determined based on what you want to do. That means, you
%% typically will not load (or even know about) a package until you
%% need it. The following preamble should allow you to do many of the
%% things you may want to do.

\documentclass[12 pt]{article} %Sets font (You should use article)

%% The following lines allow for certain features in the document to
%% work. Do not worry about the ones called. If you do not use them
%% it won't hurt anything. If there are additional features that you
%% need, then you can load more packages just as below.
\usepackage{amsmath,amssymb,amsthm,amsfonts,blkarray,pgfplots,tkz-fct}
\usepackage{graphicx,color,epsfig,multimedia,epstopdf}
\usepackage[english]{babel}
\usepackage{matlab-prettifier}
\usetikzlibrary{intersections,backgrounds}

%% The next five lines set margin information for the document. You can
%% change these if you like, but make sure you save the original values
%% in case you mess up.
\setlength{\textwidth}{38 pc}
\setlength{\textheight}{56 pc}
\setlength{\topmargin}{-4 pc}
\setlength{\oddsidemargin}{0 pc}
\setlength{\parindent}{0pc}

%% The following lines of code are self-made definitions to make 
%% calling certain commands easier (since I use them frequently). It
%% is not necessary to use any of these definitions.

\def\NN{\mathbb N} %Symbol for natural numbers
\def\ZZ{\mathbb Z} %Symbol for integers
\def\RR{\mathbb R} %Symbol for real numbers
\def\CC{\mathbb C} %Symbol for complex numbers

\def\d{\displaystyle} %Makes relevant math show in "display mode"

\usepackage{listings}
\usepackage{color} %red, green, blue, yellow, cyan, magenta, black, white
\definecolor{mygreen}{RGB}{28,172,0} % color values Red, Green, Blue
\definecolor{mylilas}{RGB}{170,55,241}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%% Matlab environment                                                 %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\lstset{language=Matlab,%
    %basicstyle=\color{red},
    breaklines=true,%
    morekeywords={matlab2tikz},
    keywordstyle=\color{blue},%
    morekeywords=[2]{1}, keywordstyle=[2]{\color{black}},
    identifierstyle=\color{black},%
    stringstyle=\color{mylilas},
    commentstyle=\color{mygreen},%
    showstringspaces=false,%without this there will be a symbol in the places where there is a space
    numbers=left,%
    numberstyle={\tiny \color{black}},% size of the numbers
    numbersep=9pt, % this defines how far the numbers are from the text
    emph=[1]{for,end,break},emphstyle=[1]\color{red}, %some words to emphasise
    %emph=[2]{word1,word2}, emphstyle=[2]{style},    
}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%% Beginning of Document                                              %
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%% It is important to know that any math related typing be enclosed in
%% either single or double dollar signs.

\begin{document} %Begins displayed document

\thispagestyle{empty} %This is to help with page formatting

%% The following helps to create the displayed heading. This can be
%% altered.
%% The \bf command creates bold text
%% The \hfill command ensures that the horizontal space is filled. This
%% forces the type to be flush with each margin.
\begin{align} 

\end{align}%
{\bf MATH 3340}  
{\bf \hfill Chris Mavor}
\vspace{-8 pt} %Brings the line closer to heading
{\bf \begin{center} Least Square Regression for Numerical Analysis \end{center}}


\vspace{-16 pt} %(vertical spacing) Brings the horizontal line closer to heading

\hrulefill %Creates horizontal line displayed

\smallskip %Creates empty space

{\bf Final Assignment} %Note how the \bf is enclosed in 
%% The \\ forces a line break
%% itemize creates a list environment
%% You do not need to use this environment if you do not want to. You 
%% can type outside of these environments just as you would in MS Word.

\begin{itemize}
\item[\bf{1.}]The method of Least Squares represents a collection of data, by way of linear representation. The procedure uses a fitted line to best represent the data by using basic calculus and linear algebra. Because this method represents the data in a linear fashion, it takes on the the form of:
$$y = m*x+b+r_i$$

We can then state $m = \beta_1$ and $b = \beta_0$. This notation allows us to use $\beta_0,\beta_1$ as the variables in the optimization. This notation then takes the form of $y = \beta_1*x+\beta_0+r_i$. Taking this equation and solving for the $r_i$ it takes the form of $r_i = y-\beta_1*x+\beta_0$ For a linear model, as such, the least squares regression is found by minimizing the following equation: 

$$r_i = y_i-\sum_{i=1}^{n} (X_{ij}\beta_i)~\text{where S}$$
By taking this equation and rewriting it we get 
$$S =  \sum_{i=1}^{n} (r_i^2)$$

To write down the least squares estimator for the linear regression model, it becomes  convenient to use matrix notation. Let $y = (y1,...,yn)^T$ and let $X$ be the n x p data matrix of the n observations on the p variables.

$$X = \left(\begin{array}{ccc}
X_{1,1} & \dots & X_{1,p} \\
. &  & . \\
. & \dots & . \\
. & & . \\
X_{n,1} & \dots & X_{n,p}\\
\end{array}\right) = (X_1,X_2,\dots,X_p),$$
Now, using matrix form we can adjust the summation of the product of $X_{ij}$ and $\beta_i$ to be read as
\begin{align*}
r_i &= y_i-\sum_{i=1}^{n} (X_{ij}\beta_i)\\
r_i &= \sqrt{\left(y_i-\sum_{i=1}^{n} (X_{ij}\beta_i)\right)^2}\\
&= ||y-X\beta||\\
r_i^2 &=||y-X\beta||^2\\
\text{where}~~~~ r_i^2& = S(\beta)
\end{align*}
Thus,
\begin{align*}
S(\beta) &= ||y-X\beta||^2\\
&=(y-X\beta)^T(y-X\beta)\\
&=y^Ty-\beta^TX^Ty-y^TX\beta+\beta^TX^TX\beta
\end{align*}

Taking the partial derivative of $S(\beta)$ with respect to $\beta$ and setting it $= 0$ results in:

\begin{align*}
\frac{\delta{S(\beta)}}{\delta{\beta^T}} &= 0-X^{T}y-0+X^{T}X\beta\\
&=-X^{T}y+X^{T}X\beta\\
X^{T}y&=X^{T}X\beta
\end{align*}

Where the solution of the normal equations in matrix form yields the vector $\beta$ of the optimal parameter values.
\begin{align*}\beta &= (X^TX)^{-1}X^Ty\\
\text{where}~\hat{y} &= X\beta = Hy\\
H &= X(X^TX)^{-1}X^T
\end{align*}


Allowing for $X^Ty$ to equal to $\sigma^2$ we can estimate the variance of noise. $\sigma^2$ represents the variance of the data point from the represented value on the linear regressed line. So in this instance
\begin{align*}
\sigma^2 &= X^Ty\\
\beta &= (X^TX)^{-1}\sigma^2\\
\end{align*}
as an estimator of the variance of noise, we take 
$$\sigma^2 = \frac{1}{n-p}||y-X\beta||^2\\
=\frac{y_i-\sum_{i=1}^{n} (X_{ij}\beta_i)}{n-p}$$
where $r_i = y_i-\sum_{i=1}^{n} (X_{ij}\beta_i)$, representing the residuals, and n  denoting the number of observations in the sample and p is the number of parameters in the functional part of the model.

Because $\sigma$ measures how the individual values of the response variable vary with respect to their true values, it also contains information about how far from the truth quantities derived from the data, such as the estimated values of the parameters, could be. 

\item[\bf{2.}]Approximate the solutions of the matrix formation to find the standard normal equations by differentiating with respect to each unknown coefficient.

\begin{align*}
y &= m*x+\beta+r_i\\
r_i &= \sum_{i=1}^{n} y_i-(mx_{i}+\beta)\\
r_i^2 &= \left(\sum_{i=1}^{n} y_i-(\beta_1x_{i}+\beta_0)\right)^2\\
\frac{\delta{S(\beta)}}{\delta{\beta_0}} &= -2(\sum_{i=1}^{n} (y_i-\beta_1x_{i}-\beta_0)\\
\frac{\delta{S(\beta)}}{\delta{\beta_1}} &= -2\sum_{i=1}^{n} [ (y_i-\beta_1x_{i}-\beta_0)x_i]\\ 
\end{align*}

Note that if setting these derivatives equal to zero, then in resulted $S_{\beta}$ will be minimized.
\begin{align*}
\frac{\delta{S(\beta)}}{\delta{\beta_0}} = 0 &= \sum y_i -\sum\beta_1x_{i}-\sum\beta_0\\
\frac{\delta{S(\beta)}}{\delta{\beta_1}} = 0 &= \sum x_iy_i-\sum\beta_1x_{i}^2-\sum\beta_0x_i\\ 
\end{align*}

Now, realizing that $\sum \beta_0 = n\beta_0$ we can express equations as a set of two linear expressions with two unknowns, $\beta_0,~\beta_1$
\begin{align*}
\sum y_i &= \sum\beta_1x_{i}+n\beta_0\\
\sum x_iy_i &= \beta_1\sum(x_{i}^2) + \beta_0 \sum x_i\\
\end{align*}

Resulting in the solutions to $\beta_0,~\beta_1$
\begin{align*}
\beta_1 &= \frac{n\sum x_iy_i-\sum x_i\sum y_i}{n\sum(x_{i}^2)-\left(\sum x_i\right)^2}\\
\beta_0 &= \frac{y-\beta_1x}{n}\\
\end{align*}

\newpage
\item[\bf{3.}]Develop a Matlab script which builds the approximation and plots various solutions.\\
{\bf Solution:} In the following script, there are several variables whose value is left to the discretion of the user:

\lstinputlisting{linregression.m}

\item[\bf{4.}]Using the script to display images of the by setting 
\lstinputlisting{Data1.m}
\begin{center}
\includegraphics[scale=.8]{figure1.eps}
\end{center}
\newpage
\lstinputlisting{Data2.m}
\begin{center}
\includegraphics[scale=.8]{figure2.eps}
\end{center}


\end{itemize}
\end{document}
