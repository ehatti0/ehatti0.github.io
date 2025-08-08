<script type="text/javascript" async
    src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
<script type="text/javascript">
    window.MathJax = {
        tex: {
            inlineMath: [['$', '$'], ['\\(', '\\)']],
            displayMath: [['$$', '$$'], ['\\[', '\\]']]
        }
    };
</script>

## Fun with $\epsilon$-calculi

**August 2025**

A while back I did some quick research on quantifier elimination in FOL, which led me to the extremely interesting $\epsilon$-calculi! For those not familiar with Hilbert's $\epsilon$ operator, it is a term-forming operator satisfying the following axiom.

$$
\dfrac{
}{
  P(e) \vdash P(\epsilon x. \, P(x))
}
$$

In other words, $\epsilon$ is a _choice operator_. If there exists some term for which $P$ holds, $\epsilon x. \, P(x)$ "evaluates" to it. If such a term does not exist, then $\epsilon x. \, P(x)$ evaluates to a completely arbitrary term.

This choice operator is fairly well-known, but a lesser-known thing about it is that it allows us to completely eliminate quantifiers from a logic! In any classical logic either $\forall$ or $\exists$ may be defined in terms of each other, but you need to have one of them. In $\epsilon$-calculi, _both_ may be defined.

$$
\begin{align*}
\exists x. \, P(x) &:= P(\epsilon x. \, P(x)) \\
\forall x. \, P(x) &:= P(\epsilon x. \, \neg P(x))
\end{align*}
$$

The $\exists$ definition follows easily from $\epsilon$'s first axiom. The $\forall$ definition is more odd, but again follows pretty intuitively. In a classical logic $\forall x. \, P(x)$ can read as "there does _not_ exist an $e$ such that $P(e)$ does _not_ hold" -- i.e to show $\forall x. \, P(x)$, we can show that if there _is_ an $e$ s.t $\neg P(e)$, then $\bot$ holds.

$$
\dfrac{
  \dfrac{
    \neg P(\epsilon x. \, \neg P(x)) \vdash \bot
  }{
    \neg \forall x. \, P(x) \vdash \bot
  }
}{
  \vdash \forall x. \, P(x)
}
$$

A potential application: Skolemization is a well-understood way of eliminating $\exists$ quantifiers in automated theorem provers. I wonder if $\epsilon$ is a cleaner and/or more correct way of doing that?
