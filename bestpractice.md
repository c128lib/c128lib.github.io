---
layout: default
title: Best practice
---
# Best practice

## Create an issue
Every feature or bug should have an issue in repository.
Issues should be populated with:
* consistent title
* label (at least enhancement, bug or documentation)
* project (should be c128lib)

Nice to have:
* description of the feature
* milestone

![Create issue](resources/create-issue.png)

Prioritizing and assignment should be negotiated with other member of team.

## Develop an issue
An issue should be developed in its own branch.

It's better to use VsCode extension. You can check and install by using this documentation: https://code.visualstudio.com/docs/sourcecontrol/github

After this, you can navigate through issue (assigned to you or assigned to project you own or collaborate). 
You need to choose you issue and click on the checkbox like the image.

![Start working on issue](resources/start-issue.png)

This operation will create and checkout a new branch.
When you push your commits (even if you have not completed your issue), you can edit issue by adding branch name on it.
So your commit will be automatically linked to your issue.

If an issue is assigned to you, you can also find in "My issues" group.

![Link branch on issue](resources/link-branch-on-issue.png)

## Create a pull request

#TBD

## Macro structure

Take this code as example:
<pre><code>/*
  Read from Vdc internal memory and write it to Vic screen memory by
  using source address.

  Params:
  source - Vdc memory absolute address
  destination - Vic screen memory absolute address
  qty - number of byte to copy
*/
.macro ReadFromVdcMemoryByAddress(source, destination, qty) {
  .errorif (qty &lt;= 0), "qty must be greater than 0"
  .errorif (qty &gt; 255), "qty must be lower than 256"
    ldx #$12
    lda #&gt;source
    jsr c128lib.ScreenEditor.WRITEREG
    lda #&lt;source
    inx
    jsr c128lib.ScreenEditor.WRITEREG

    ldy #0
  CopyLoop:
    jsr c128lib.ScreenEditor.WRITE80
    sta destination, y
    iny
    cpy #qty
    bne CopyLoop
}
</code></pre>

First of all, macro name should be consistent: should be easy understand what she does. Included also for parameter name.

Before macro name, it's good to add a short description.
This description will be shown when you use this macro with mouse over effect.
In this description you should add parameter definition and even results (if present).

If parameters has limits or need to be in specific range, <code>.errorif</code> can be used to check if parameter is out of range.
Violation will produce build error.

### Macro unit testing

There are two type of testing you should do with macros:
* parameter checking
* code checking

Parameter checking means add <code>.errorif</code> statement and then check it with <code>.asserterror</code> statement.

<pre><code>.asserterror "ReadFromVdcMemoryByAddress($beef, $baab, 0)", { ReadFromVdcMemoryByAddress($beef, $baab, 0) }
</code></pre>

This test checks that if qty is 0, a build error will be produced.

Code checking means verifying that macro call with certain parameter, will produce expected code. This is done by adding a <code>.assert</code> statement.

<pre><code>.assert "ReadFromVdcMemoryByAddress($beef, $baab, 100)", { ReadFromVdcMemoryByAddress($beef, $baab, 100) },
{
    ldx #$12; lda #$be; jsr $CDCC; lda #$ef; inx; jsr $CDCC;
    ldy #0; jsr $CDCA; sta $baab, y; iny; cpy #100; bne *-9;
}
</code></pre>

This assert checks that calling <code>ReadFromVdcMemoryByAddress($beef, $baab, 100)</code> will produces exactly the specified code.
