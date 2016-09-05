CJKwrap
=======

**CJKwrap** is a library for wrapping and filling CJK text.

CJKwrap fix the issue24665 because Python 2 will stay broken forever:
https://bugs.python.org/issue24665.

CJKwrap support **both** Python 2 (2.6 and above) and Python 3 (3.3 and above).

CJKwrap is developed by Florent Gallaire fgallaire@gmail.com.

Website: http://fgallaire.github.io/cjkwrap.

Download and Install
--------------------

To install the last stable version from PyPI::

    $ sudo pip install cjkwrap

To install the development version from GitHub::

    $ git clone https://github.com/fgallaire/cjkwrap
    $ cd cjkwrap
    $ sudo python setup.py install

Or you can just use the ``cjkwrap.py`` file alone, nothing more needed!

Usage
-----

``cjklen()`` and ``cjkslices()`` to replace built-in ``len()`` and slicing::

    >>> import cjkwrap
    >>> cjkwrap.cjklen(u"最終的には良い長さ")
    18
    >>> head, tail = cjkwrap.cjkslices(u"最終的には良い長さ", 6)
    >>> print head
    最終的
    >>> print tail
    には良い長さ

As ``cjklen()`` uses ``len()`` for non unicode stuff, you can safely do this::

    >>> from cjkwrap import cjklen as len
    >>> len(u"最終的には良い長さ")
    18
    >>> len('ascii string')
    12
    >>> len([1, 2, 3, 4])
    4

``wrap()`` and ``fill()`` to replace the ones from the Python standard library::

    >>> wrapped_cjk = cjkwrap.wrap(u"最終的に良いラッピング", 10)
    >>> for line in wrapped_cjk: print line
    ... 
    最終的に良
    いラッピン
    グ
    >>> print cjkwrap.fill(u"最終的に良いラッピング", 10)
    最終的に良
    いラッピン
    グ

Mixed content is allowed::

    >>> cjkwrap.cjklen(u"CJK 最終的には良い長さ")
    22
    >>> print cjkwrap.fill(u"CJK 最終的には良い長さ", 10)
    CJK 最終的
    には良い長
    さ

License
-------

CJKwrap files are released under the GNU LGPLv3 or above license.

CJKwrap codebase from textwrap by Greg Ward (gward@python.net) under the Python license.
