<template>
  <div id="intro">

    <div id="octocat">
      <a href="https://github.com/watchduck/tree_table">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/Octicons-mark-github.svg/40px-Octicons-mark-github.svg.png" width="40px">
      </a>
    </div>

    Enter terms like the following to get a table describing the corresponding
    <a href="https://en.wikipedia.org/wiki/Tree_structure">tree structure</a>:
    <ul>
      <li>a(b, c)</li>
      <li>a(b, c(a(b, c(d))))</li>
      <li>f(f, f(f))</li>
      <li>f(f, f(f), f(f, f(f)))</li>
      <li>=(^(c, 2), +(^(a, 2), ^(b, 2), *(−, 2, a, b, cos(ang(c)))))</li>
      <li><span>.(1(1(1(1(1(., .), 5(., .)), 4(5(., .), 4(., .))), 3(4(4(., .), 7(., .)), 3(7(., .), 3(., .)))), 2(3(3(3(., .), 8(., .)), 5(8(., .), 5(., .))), 2(5(5(., .), 7(., .)), 2(7(., .), 2(., .))))), 1(2(2(2(2(., .), 7(., .)), 5(7(., .), 5(., .))), 3(5(5(., .), 8(., .)), 3(8(., .), 3(., .)))), 1(3(3(3(., .), 7(., .)), 4(7(., .), 4(., .))), 1(4(4(., .), 5(., .)), 1(5(., .), 1(., .))))))</span></li>
    </ul>
    (The two last examples are the <a href="https://en.wikipedia.org/wiki/Law_of_cosines">law of cosines</a>
    and the <a href="https://en.wikipedia.org/wiki/Calkin%E2%80%93Wilf_tree">Calkin–Wilf tree</a>.)
  </div>
</template>
