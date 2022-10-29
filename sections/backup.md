% backup.md

%%%%%%%%%%%%%%%%%%%%
\begin{frame}{Metadata for Causal Transactions}
  \begin{center}
    \[
      \knownVC \in [\D \to \N]
    \]

    \begin{property}[Property of $\knownVC$]
      \begin{center}
        For each data center $i$, \\[3pt]
        the \red{replica $p^{m}_{d}$} stores the updates to partition $m$ \\[3pt]
        by transactions originating at $i$
        with local timestamps $\le \knownVC[i]$.
      \end{center}
    \end{property}
  \end{center}
\end{frame}
%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%
\begin{frame}{Metadata for Causal Transactions}
  \begin{center}
    \[
      \stableVC \in [\D \to \N]
    \]

    \begin{property}[Property of $\stableVC$]
      \begin{center}
        For each data center $i$, \\[3pt]
        the \red{data center $d$} stores the updates \\[3pt]
        by transactions originating at $i$ with local timestamps $\le \stableVC[i]$.
      \end{center}
    \end{property}
  \end{center}
\end{frame}
%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%
\begin{frame}{Metadata for Causal Transactions}
  \begin{center}
    \[
      \uniformVC \in [\D \to \N]
    \]

    \begin{property}[Property of $\uniformVC$]
      \begin{center}
        All update transactions originating at $i$ \\[3pt]
        with local timestamps $\le \uniformVC[i]$ \\[3pt]
        are replicated at \red{$f + 1$ data centers} including $d$.
      \end{center}
    \end{property}
  \end{center}
\end{frame}
%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%
\begin{frame}{Metadata for Causal Transactions}
  \[
    \uniformVC \in [\D \to \N]
  \]

  \begin{lemma}
    \begin{center}
      All update transactions \\[3pt]
      with \red{commit vectors $\le \uniformVC$} are uniform.
    \end{center}
  \end{lemma}

  \pause
  \vspace{0.30cm}
  \begin{center}
    \unistore{} makes a remote causal transaction visible to clients \\[3pt]
    only \red{after it is uniform}.
  \end{center}
\end{frame}
%%%%%%%%%%%%%%%%%%%%