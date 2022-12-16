# Documentation

<code>c128lib</code> is a library which contains labels, macros, functions and pseudocommands to help develop application and games for Commodore 128.

It's hosted as a [GitHub organization](https://github.com/c128lib) and contains several project. Every element and project can be used to develop your application.

There is a CI workflow that builds and tests every project, using Gradle as a build system. Gradle is strongly recommended as a build system also for your projects.

Every project has a <code>c128lib</code> filenamespace and (usually) a module namespace. For example, if you need raster register of Vic2 chip ($D012) you should refer it as:
<pre>
  lda #c128lib.Vic2.RASTER
</pre>

## Currently implemented projects

[Common](common): contains labels that are no refered with a specific chipset, it's often a base for other projects. It contains also Kernal labels.

[Chipset](chipset): labels and macros that directly involves internal chips.

[Framework](framework): work in progess

## Library introduction

[Usage](usage): setup your environment to use <code>c128lib</code>.

[Become a contributor](becomeacontributor): setup you environment to become a <code>c128lib</code> developer.

[Changelog](changelog): look changes in <code>c128lib</code>.
