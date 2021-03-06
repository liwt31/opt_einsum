Changelog
=========

2.2.0 / 2018-MM-DD
------------------

New Features
++++++++++++
- (:pr:`48`) Intermediates can now be shared between contractions, see here for more details.
- (:pr:`53`) Intermediate caching is thread safe.

Enhancements
++++++++++++
- (:pr:`48`) Expressions are now mapped to non-unicode index set so that unicode input is support for all backends.
- (:pr:`54`) General documenation update.

Bug fixes
+++++++++
- (:pr:`41`) PyTorch indices are mapped back to a small a-z subset valid for PyTorch's einsum implementation.

2.1.3 / 2018-8-23
-----------------

Bug fixes
+++++++++

- Fixes unicode issue for large numbers of tensors in Python 2.7.
- Fixes unicode install bug in README.md.

2.1.2 / 2018-8-16
-----------------

Bug fixes
+++++++++

- Ensures `versioneer.py` is in MANIFEST.in for a clean pip install.


2.1.1 / 2018-8-15
-----------------

Bug fixes
+++++++++

- Corrected Markdown display on PyPi.

2.1.0 / 2018-8-15
-----------------

``opt_einsum`` continues to improve its support for additional backends beyond NumPy with PyTorch.

We have also published the opt_einsum package in the Journal of Open Source Software. If you use this package in your work, please consider citing us!

New features
++++++++++++

- PyTorch backend support
- Tensorflow eager-mode execution backend support

Enhancements
++++++++++++

- Intermediate tensordot-like expressions are now ordered to avoid transposes.
- CI now uses conda backend to better support GPU and tensor libraries.
- Now accepts arbitrary unicode indices rather than a subset.
- New auto path option which switches between optimal and greedy at four tensors.

Bug fixes
+++++++++

- Fixed issue where broadcast indices were incorrectly locked out of tensordot-like evaluations even after their dimension was broadcast.

2.0.1 / 2018-6-28
-----------------

New Features
++++++++++++

- Allows unlimited Unicode indices.
- Adds a Journal of Open-Source Software paper.
- Minor documentation improvements.


2.0.0 / 2018-5-17
-----------------

``opt_einsum`` is a powerful tensor contraction order optimizer for NumPy and related ecosystems.

New Features
++++++++++++

- Expressions can be precompiled so that the expression optimization need not happen multiple times.
- The greedy order optimization algorithm has been tuned to be able to handle hundreds of tensors in several seconds.
- Input indices can now be unicode so that expressions can have many thousands of indices.
- GPU and distributed computing backends have been added such as Dask, TensorFlow, CUPy, Theano, and Sparse.

Bug Fixes
+++++++++

- An error affecting cases where opt_einsum mistook broadcasting operations for matrix multiply has been fixed.
- Most error messages are now more expressive.


1.0.0 / 2016-10-14
------------------

Einsum is a very powerful function for contracting tensors of arbitrary
dimension and index. However, it is only optimized to contract two terms at a
time resulting in non-optimal scaling for contractions with many terms.
Opt_einsum aims to fix this by optimizing the contraction order which can lead
to arbitrarily large speed ups at the cost of additional intermediate tensors.

Opt_einsum is also implemented into the np.einsum function as of NumPy v1.12.

New Features
++++++++++++

- Tensor contraction order optimizer.
- :func:`opt_einsum.contract` as a drop-in replacement for :func:`numpy.einsum`.
