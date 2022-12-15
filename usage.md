# Usage

<code>c128lib</code> is a set of libraries that can be used in assembly programs written with Kick Assembler. Each library has  one or more source files that can be then imported in your Kick Assembler program. The most convenient is using Gradle.


## Setting up Gradle

If you don't have Gradle in you system, you have to install it first. So, you need two step:
* install JDK 8 (or better)
* install Gradle

Check specific documentation for these two steps.

If everything went well, you should open command prompt in your project folder (or a terminal window if you use Visual Studio Code) and type:

<pre>
C:\project>gradle wrapper
</pre>

Then, you should edit (or create) your <code>build.gradle</code>, that is a sort of settings file for your project. Your file should be like this:

<pre>
plugins {
    id "com.github.c64lib.retro-assembler" version "1.5.1"
}

retroProject {
    dialect = "KickAssembler"
    dialectVersion = "5.25"
    libDirs = [".ra/deps/c128lib"]

    libFromGitHub "c128lib/common", "0.5.0"
    libFromGitHub "c128lib/chipset", "0.4.0"
}
</pre>

<code>plugins</code> refers to Retro Build Tool. The complete manual for Retro Build Tool is available [here](https://c64lib.github.io/gradle-retro-assembler-plugin/).

<code>retroProject</code> contains details about your project:
* <code>dialect</code> and <code>dialectVersion</code> tells about which compiler is used in which version
* <code>libDirs</code> tells in which folder library will be found when using and import directive
* <code>libFromGitHub</code> tells a library to be downloaded from GitHub and relative version needed

## Importing c128lib projects and libraries

Importing libraries is quite simple and it's made by using an import directive like this:

<pre>
#import "vic2.asm"
</pre>

Labels are available by using this syntax:
<pre>
lda &lt;c128lib-namespace&gt;.&lt;module-namespace&gt;.&lt;label-name&gt;
</pre>

For example, if you need x-coordinate of sprite 2, you can use:
<pre>
lda c128lib.Vic2.SPRITE_2_X
</pre>

This would be translated to:

<pre>
lda $D004
</pre>

Unfortunately, macros cannot be accessed directly, so them are exposed with a prefix like <code>c128lib_</code>, through a <code>*\_global.asm</code> file. So if you need a macro, you need to use:

<pre>
#import "vic2_global.asm"
</pre>

and use macros like this:
<pre>
c128lib_setRaster(100)
</pre>

<hr>

Did you find any errors or would you like to suggest an improvement? [Open an issue](https://github.com/c128lib/c128lib.github.io/issues/new)
