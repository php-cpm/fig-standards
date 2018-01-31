扩展代码风格指南元文档
=========================================

# 1. 概要

本文档描述扩展代码风格PSR的进展和讨论。目的是说明每次讨论的原因。

# 2. 为什么要有这个规范？

PSR-2自2012年通过后，PHP已经有了一系列改变，
尤其是 PHP 7 带来的显著改变，急需要推出新的代码风格指南。
PSR-2 在撰写时对 PHP 功能覆盖很全面，
而对新增的功能支持也很好。
PSR-12试图提供一种方式使得代码风格检查工具可实现，项目可以声明遵守
且开发者可以很容易的在不同项目间联系起来，
减少代码风格不同产生的摩擦。

PSR-2 由 PHP FIG 项目当时的通用实践而建立
但最终表明它是一个不同项目指南的妥协方案。
这间接导致项目从自己的编码规范转为支持PSR-2
（而且大部分都支持PSR-1，尽管没有明确指出）变动太大
（丢失git历史，巨大的变更列表，被破坏的现存patch和PR）。

PSR-2 需要适配者格式化大量现存不合规范的代码。
PSR-12 为了减轻这个麻烦，我们采用了一个更合规范的方法
并为新语言特性在发布后定义标准。我们希望如此
因为这个规范是先于编写的代码定义的，
最好有机会被接受。


然而我们仍要实施PSR-2，而不在PSR-12外开新的议题（参考第四节，提案）。

# 3. 范围

## 3.1. 目标

该PSR与PSR-2目标一致.

> The intent of this guide is to reduce cognitive friction when scanning code from
> different authors. It does so by enumerating a shared set of rules and expectations
> about how to format PHP code.
> When various authors collaborate across multiple projects, it helps to have one set
> of guidelines to be used among all those projects. Thus, the benefit of this guide is
> not in the rules themselves, but in the sharing of those rules.

This PSR is an extension of PSR-2, and therefore also an extension of PSR-1. The basis of
PSR-12 is PSR-2 and therefore a list of differences is provided below to assist with migration
but it should be considered as an independent specification.

This PSR will include coding style guidelines related to new functionality added to PHP
after the publication of PSR-2; this includes PHP 5.5, PHP 5.6 and PHP 7.0. This PSR will
also include clarifications on the text of PSR-2, as described in the PSR-2 Errata.

## 3.2. 非目标

It is not the intention of this PSR to add entirely new coding style guidelines PSR-12 will
also not change anything stipulated in PSR-1 and PSR-2.

# 4. 提案

实施PSR-12且支持新语言特性

## 4.1. 严格类型声明

这里有讨论是否该在标准中使用严格类型模式
https://github.com/cs-extended/fig-standards/issues/7。
综合考虑我们要使用MUST、MUST NOT，尽量避免SHOULD，没人认为严格模式不该声明。
The discussion was whether it should be
considered a coding style item which should be covered or whether it was out of scope and it
was decided to be out of scope of a coding style guide.

## 4.2. Finally and Return Types Declaration Spacing

Numerous different options were suggested and they can be seen
[here for return type declarations](https://gist.github.com/michaelcullum/c025f3870c9ea1dd2668#file-returntypesspacing-php) or
[here for finally blocks](https://gist.github.com/michaelcullum/c025f3870c9ea1dd2668#file-finallyblocks-php)
and the current implementation was chosen due to consistency with other parts of the PSR-12
specification that came from PSR-2.

## 4.3. Enforcing short form for all type keywords

PHP 7.0 introduced [scalar types declaration](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration)
which does not support long type aliases. Therefore it makes sense to enforce primary short type forms to be used to
have uniform syntax and prevent possible confusion.

## 4.4. Public Survey

In order to settle things using data, survey was conducted and responses from 142 people
including 17 project representatives were gathered:

### 4.4.1. Fig Representative Results

| Representative          | Project           | Compound namespaces with a depth of two or more MUST not be used | Header statement grouping and ordering | Declare statements must each be on their own line | Declare statements in PHP files containing markup | Declare statements have no spaces: `declare(strict_types=1);` | Block declare statement formatting | `new` keyword usage, parenthesis required |Return type declaration formatting |Use statement leading slashes disallowed | Block namespace declaration formatting | General operator spacing |Try, Catch, Finally formatting | Anonymous class declaration formatting | Keyword casing, only lower case | Type keywords, short form only |
| --------------          | -------           | ---------------------------------------------------- | ---------------------------------- | ----------------------------------------- | ------------------------------------------- | -------------------------------------------------------- | ------------------------------- | ------------------------------------- |------------------------------- |------------------------------------ | ----------------------------------- | ---------------------- |--------------------------- | ----------------------------------- | --------------------------- | -------------------------- |
| Alexander Makarov       |  Yii framework    | ✓ | ✓ | ✓ | ❌ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Korvin Szanto           | concrete5         | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Leo Feyer               | Contao            | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Larry Garfield          | Drupal            | ✓ | ✓ | ✓ | ✓ | ✓ | ❌ | ✓ | ✓ | ✓ | ❌ | ✓ | ✓ | ❌ | ✓ | ✓ |
| André R.                | eZ                | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Jan Schneider           | Horde             | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Karsten Dambekalns      | Neos and Flow     | ✓ | ✓ | ✓ | ✓ | ❌ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Andres Gutierrez        | Phalcon           | ❌ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Ryan Thompson           | PyroCMS           | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ❌ | ❌ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Matteo Beccati          | Revive Adserver   | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ❌ | ✓ | ✓ | ✓ | ✓ |
| Damian Mooyman          | SilverStripe      | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Brian Retterer          | Stormpath PHP SDK | ✓ | ✓ | ✓ | ❌ | ❌ | ✓ | ❌ | ✓ | ❌ | ✓ | ✓ | ✓ | ✓ | ❌ | ❌ |
| Matthew Weier O'Phinney | Zend Framework    | ❌ | ✓ | ✓ | ❌ | ✓ | ✓ | ✓ | ❌ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Jordi Boggiano          | Composer          | ❌ | ❌ | ❌ | ✓ | ✓ | ✓ | ❌ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Ben Marks               | Magento           | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Chuck Burgess           | PEAR              | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
|                         | **Totals**:       |13/3|15/1|15/1|13/3|14/2|15/1|14/2|15/1|14/2|14/2|15/1|16/0|15/1|15/1|15/1|

### 4.4.2. General non-representative voters

| Question | For | Against | Percentage For |
| -------- | --- | ------- | -------------- |
| Compound namespaces required depth | 114 | 12 | 89.47% |
| Header statement grouping and ordering | 113 | 13 | 88.5% |
| Declare statements must each be on their own line | 120 | 6 | 95% |
| Declare statements in PHP files containing markup | 119 | 7 | 94.12% |
| Declare statements have no spaces | 116 | 10 | 91.38% |
| Block declare statement formatting | 118 | 8 | 93.22% |
| `new` keyword usage, parenthesis required | 116 | 10 | 91.38% |
| Return type declaration formatting | 115 | 11 | 90.43% |
| Use statement leading slashes disallowed | 118 | 8 | 93.22% |
| Block namespace declaration formatting | 120 | 6 | 95% |
| General operator spacing | 123 | 3 | 97.56% |
| Try, Catch, Finally formatting | 124 | 2 | 98.39% |
| Anonymous class declaration formatting | 117 | 9 | 92.31% |
| Keyword casing, only lower case | 124 | 2 | 98.39% |
| Type keywords, short form only | 121 | 5 | 95.87% |

## 4.5. Multiline Function Arguments Mixed With Multiline Return

A potential readability issue [was raised on the mailing list](https://groups.google.com/d/msg/php-fig/ULSL4gqK8GY/cgDELuPOCQAJ).
We reviewed options for changes to the specification that could provide better readability and
the floated option was to require a blank line after the opening bracket of a function if the
arguments and the return are both multiline. Instead it was pointed out that this specification
_already_ allows you to decide where you'd like to add blank lines and so we will leave it to
the implementors to decide.

# 5. Changelog from PSR-2

Please note this changelog is not a verbose list of changes from PSR-2 but highlights the most
notable changes. It should be considered a new specification and therefore you should read the
specification for a full understanding of its contents.

## 5.1. New Statements

* Lowercase for all keywords - Section 2.5
* Short form for all type keywords - Section 2.5
* Use statement grouping - Section 3
* Use statement blocks - Section 3
* Declare statement/Strict types declaration usage - Section 3
* Parentheses are always required for class instantiation - Section 4
* Return type declarations - Section 4.5
* Type hints - Section 4.5
* Add finally block - Section 5.6
* Operators - Section 6
* Anonymous classes - Section 8

## 5.2. Clarifications and Errata
* Adjust 'methods' to 'methods and functions' in a number of instances - Throughout
* Adjust references to classes and interfaces to also include traits - Throughout
* StudlyCaps meaning clarified as PascalCase - Section 2.1
* The last line should not be blank but contain an EOL character - Section 2.2
* Blank lines may be added for readability except where explicitly forbidden within the PSR - Section 2.3
* PSR-2 errata statement about multi-line arguments - Section 4
* PSR-2 errata statement about extending multiple interfaces - Section 4
* Forbid blank lines before/after closing/opening braces for classes - Section 4

# 6. People

## 6.1.  Editor:
* **Korvin Szanto**

## 6.2. Sponsor:
* **Chris Tankersley**

## 6.3. Working Group Members:
* **Alexander Makarov**
* **Michael Cullum**
* **Robert Deutz**

## 6.4. Special Thanks
* **Michael Cullum** for drafting the original specification
* **Alexandar Makarov** for coordinating the draft during FIG 2.0
* **Cees-Jan Kiewiet** for moral support

# 7. Votes

* **Entrance Vote: ** https://groups.google.com/forum/?utm_medium=email&utm_source=footer#!msg/php-fig/P9atZLOcUBM/_jwkvlYKEAAJ

# 8. Relevant Links

_**Note:** Order descending chronologically._

* [Inspiration Mailing List Thread](https://groups.google.com/forum/?utm_medium=email&utm_source=footer#!topic/php-fig/wh9avopSR9k)
* [Initial Mailing List PSR Proposal Thread](https://groups.google.com/forum/?utm_medium=email&utm_source=footer#!topic/php-fig/MkFacLdfGso)
