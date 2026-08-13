# Math syntax visual check

Display math sections should have no markdownlint diagnostics. Inline sections
are retained for later parser work.

## LaTeX environment

Before the environment.

\begin{equation}
a
=
b
\end{equation}

After the environment.

## Bracket display math

Before the display.

\[
a
=
b
\]

After the display.

## Parenthesis inline math

Before the inline expression.

\(
a
=
b
\)

After the inline expression.

## Dollar display math

Before the display.

$$
a
=
b
$$

After the display.

## Dollar inline math

Before the inline expression.

$
a
=
b
$

After the inline expression.
