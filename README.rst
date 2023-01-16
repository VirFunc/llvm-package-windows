LLVM packages for Windows
=========================

.. image:: https://github.com/VirFunc/llvm-package-windows/actions/workflows/ci.yml/badge.svg
	:target: https://github.com/VirFunc/llvm-package-windows/actions/workflows/ci.yml
.. image:: https://img.shields.io/badge/donate-@jancy.org-blue.svg
	:align: right
	:target: http://jancy.org/donate.html?donate=llvm-package

Releases
--------

.. list-table::

	*	- LLVM Date
		- LLVM Version
		- Clang Version
		- Remarks

Abstract
--------

LLVM is huge, and it's getting bigger with each and every release. Building it together with a project that depends on it (e.g., a programming language) during a CI build is **not an option** -- building *just LLVM* eats most (earlier LLVM releases), and all (recent LLVM releases) of the allotted CI build time.

So why not use pre-built packages from the official `LLVM download page <http://releases.llvm.org>`__? Unfortunately, the official binaries cover just a *tiny fraction* of possible build configurations on Microsoft Windows. There are no Debug libraries, no builds for the static LIBCMT, and only a single toolchain per LLVM release.

The ``llvm-package-windows`` project builds all major versions of LLVM on **GitHub Actions** for the following, much more complete matrix:

* Toolchain:
	- Visual Studio 2017
	- Visual Studio 2015 (LLVM 3.4.2 to 8.0.0)
	- Visual Studio 2013 (LLVM 3.4.2 to 3.9.1)
	- Visual Studio 2010 (LLVM 3.4.2 only)

* Configuration:
	- Debug
	- Release

* Target CPU:
	- IA32 (a.k.a. x86)
	- AMD64 (a.k.a. x86_64)

* C/C++ Runtime:
	- LIBCMT (static)
	- MSVCRT (dynamic)

The resulting LLVM binary packages are uploaded as GitHub Release artifacts. Compiler developers can now thoroughly test their LLVM-dependent projects on GitHub CI or AppVeyor CI simply by downloading and unpacking an archive with the required LLVM prebuilt binaries during the CI installation stage.
