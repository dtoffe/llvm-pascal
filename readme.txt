LLVM-Pascal (this fork)

- Converted from Delphi project to Lazarus project.
- Delphi compatibility of the sources is not a target of this particular fork, will most likely transition to objFPC mode.
- Hopefully will upgrade LLVM dependencies and bindings to current version (v. 10 as of this commit).
- ...then, play with the language ???


===  OLD README  (roughly google-translated from Brazilian Portuguese into English  ====


LLVM-Pascal 2010.9.24 Pre-Alpha IV

Main implementation of this release: Scanner and Parser

Home: http://llvm-pascal.googlecode.com
Forum: http://groups.google.com/group/llvm-pascal
License: BSD, http://www.opensource.org/licenses/bsd-license.php

- For now, the "compilation" only does lexical and syntactic analysis.
- Compiles with any Delphi up to version XE and Free Pascal 2.4.
- Extremely small and simple sources using Object Orientation with Object Pascal.
- Compiles sources from the Delphi dialect up to the XE version, does not support operator overload in the Delphi dialect.
- Compiles Lazarus sources up to version 0.9.28.2 and Free Pascal up to version 2.4, support macros, generics, operator overloading and binary literals.
- Compiles ~148 klps (thousand lines per second) in a Intel E2200 Dual Core II 2.2 GHz with 2 GB of RAM and Windows XP SP3, compiled with Turbo Delphi, with FPC 2.4 ~98 klps.
- Part of that difference relates to functions Pos, PosEx, UpperCase and LowerCase used by the compiler, which are implemented in Assembly in Delphi and are implemented in Pascal in FPC.
- Within LLVM-Pascal those functions were substituted, only if compiled with FPC, by optimized versions in Pascal from the site FastCode, then FPC compiles ~118 klps and Turbo Delphi about ~147 klps using FastCode.
- Performance is not that good (~95 klps) in Delphi 2009/2010/XE, because our compiler is based in AnsiStrings and not in Unicode, causing lots of conversions in VCL. 
- Compile your project with LLVM-Pascal and report your questions at the fórum: http://groups.google.com/group/llvm-pascal

To compile use:

LLVM_Pascal *.pas

Command line to compare performance: LLVM_Pascal "C:\Arquivos de programas\Borland\BDS\4.0\source\*.pas" -fi"C:\Arquivos de programas\Borland\BDS\4.0\source\dunit\contrib\dunitwizard\source\common\" -v1 -vmE130,E139

