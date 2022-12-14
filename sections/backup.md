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

%%%%%%%%%%%%%%%%%%%%
\begin{frame}{Adding Strong Transactions}
  \begin{center}
    \[
      \knownVC \in [\D \cup \set{\strongentry} \to \N]
    \]

    \begin{property}[Property of {$\knownVC[\strongentry]$}]
      \begin{center}
        \red{Replica $p^{m}_{d}$} stores the updates to $m$ by all strong transactions \\[3pt]
        with $\commitVC[\strongentry] \le \knownVC[\strongentry]$.
      \end{center}
    \end{property}
  \end{center}
\end{frame}
%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%
\begin{frame}{Metadata for Strong Transactions}
  \begin{center}
    \[
      \stableVC \in [\D \cup \set{\strongentry} \to \N]
    \]

    \fig{width = 0.80\textwidth}{figs/knownvc-local-strong}

    \begin{property}[Property of {$\stableVC[\strongentry]$}]
      \begin{center}
        \red{Data center $d$} stores the updates by all strong transactions \\[3pt]
        with $\commitVC[\strongentry] \le \knownVC[\strongentry]$.
      \end{center}
    \end{property}
  \end{center}
\end{frame}
%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%
\begin{frame}{Metadata for Strong Transactions}
  \begin{center}
    \[
      \uniformVC \in [\D \to \N]
    \]

    \fig{width = 0.80\textwidth}{figs/stablevc-uniformvc-strong}

    \vspace{0.30cm}
    The commit protocol for strong transactions \\[3pt]
    guarantees their uniformity.
  \end{center}
\end{frame}
%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%
\begin{frame}{Consistency Model of \unistore{} (Safety)}
  \begin{center}
    \unistore{} implements a \blue{transactional} variant of \\
    the \por{} consistency

    \pause
    \[
      \txs \triangleq \causaltxs \uplus \strongtxs
    \]

    \pause
    \vspace{0.60cm}
    \begin{enumerate}[(I)]
      \centering
      \item transactional causal consistency by default
      \item to specify conflicting transactions under strong consistency
    \end{enumerate}
  \end{center}
\end{frame}
%%%%%%%%%%%%%%%%%%%%

%%%%%%%%%%%%%%%%%%%%
\begin{frame}{Consistency Model of \unistore{} (Liveness)}

  \vspace{0.50cm}
  A transaction that is either \strongcolor{strong}
  or \causalcolor{causal that originates at a correct data center}
  eventually becomes \red{visible} at all \violet{correct} data centers.
  % \begin{itemize}
  %   \item from some point on, $t$ precedes all transactions issued at correct data
  %         centers.
  % \end{itemize}
\end{frame}
%%%%%%%%%%%%%%%%%%%%
