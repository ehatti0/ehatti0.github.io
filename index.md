$$
\frac{
  \Gamma, x : A \vdash e : B
}{
  \Gamma \vdash \lambda x. e : \Pi_{x : A} B
}
\quad \quad
\frac{
  \Gamma \vdash f : \Pi_{x : A} B \quad \Gamma \vdash v : A
}{
  \Gamma \vdash f(x) : B[x/v]
}
$$

I am a CS undergrad at Yale University, primarily interested in programming languages and proof assistants.
