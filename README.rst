ZopfliPy
========

A Python_ bindings for Zopfli_.

.. image:: https://img.shields.io/pypi/v/zopflipy.svg
   :target: https://pypi.python.org/pypi/zopflipy

.. image:: https://semaphoreci.com/api/v1/hattya/zopflipy/branches/master/badge.svg
   :target: https://semaphoreci.com/hattya/zopflipy

.. image:: https://ci.appveyor.com/api/projects/status/98a7e7d6qlkvs6vl/branch/master?svg=true
   :target: https://ci.appveyor.com/project/hattya/zopflipy

.. image:: https://codecov.io/gh/hattya/zopflipy/branch/master/graph/badge.svg
   :target: https://codecov.io/gh/hattya/zopflipy

.. _Python: https://www.python.org/
.. _Zopfli: https://github.com/google/zopfli


Requirements
------------

- Python 2.7 or 3.4+


Installation
------------

.. code:: console

   $ pip install zopflipy


Usage
-----

ZopfliCompressor:

.. code:: pycon

   >>> import zopfli
   >>> c = zopfli.ZopfliCompressor(zopfli.ZOPFLI_FORMAT_DEFLATE)
   >>> z = c.compress(b'Hello, world!') + c.flush()
   >>> d = zopfli.ZopfliDecompressor(zopfli.ZOPFLI_FORMAT_DEFLATE)
   >>> d.decompress(z) + d.flush()
   b'Hello, world!''

ZopfliDeflater:

.. code:: pycon

   >>> import zopfli
   >>> c = zopfli.ZopfliDeflater()
   >>> z = c.compress(b'Hello, world!') + c.flush()
   >>> d = zopfli.ZopfliDecompressor(zopfli.ZOPFLI_FORMAT_DEFLATE)
   >>> d.decompress(z) + d.flush()
   b'Hello, world!''

ZopfliPNG:

.. code:: pycon

   >>> import zopfli
   >>> png = zopfli.ZopfliPNG()
   >>> with open('in.png', 'rb') as fp:
   ...     data = fp.read()
   >>> len(png.optimize(data)) < len(data)
   True


License
-------

ZopfliPy is distributed under the terms of the Apache License, Version 2.0.
