.. note::

   **Fork notice.** This is a fork of grate-driver/mesa, used to bring up
   hardware GL on the Microsoft Surface RT (Tegra 3) under postmarketOS.
   The work is on the ``grate-22.2.4`` branch: it seeds ``no_scissor`` at
   context creation (an uninitialised value made the kernel reject command
   streams), exports buffers as dma-buf FDs in ``grate_resource_get_handle``
   (without it the framebuffer was empty), splits draws above the 4096-vertex
   limit, caps ``MAX_CONST_BUFFERS`` at 1, fixes ``drm_tegra_bo_from_dmabuf``,
   and adds ``GRATE_DEBUG=draw`` tracing. Result: ``es2tri`` and ``es2gears``
   render on the GR3D (about 60 fps for ``es2gears``) under the modesetting
   X driver. This fork is no longer developed: active work continues at
   https://codeberg.org/libre-tegra/mesa (branch ``grate-wip``), which moved to
   the mainline tegra-drm API. Tooling and write-up:
   https://github.com/LBSiUK/SurfaceRT-GPU-Driver

`Mesa <https://mesa3d.org>`_ - The 3D Graphics Library
======================================================


Source
------

This repository lives at https://gitlab.freedesktop.org/mesa/mesa.
Other repositories are likely forks, and code found there is not supported.


Build & install
---------------

You can find more information in our documentation (`docs/install.html
<https://mesa3d.org/install.html>`_), but the recommended way is to use
Meson (`docs/meson.html <https://mesa3d.org/meson.html>`_):

.. code-block:: sh

  $ mkdir build
  $ cd build
  $ meson ..
  $ sudo ninja install


Support
-------

Many Mesa devs hang on IRC; if you're not sure which channel is
appropriate, you should ask your question on `Freenode's #dri-devel
<irc://chat.freenode.net#dri-devel>`_, someone will redirect you if
necessary.
Remember that not everyone is in the same timezone as you, so it might
take a while before someone qualified sees your question.
To figure out who you're talking to, or which nick to ping for your
question, check out `Who's Who on IRC
<https://dri.freedesktop.org/wiki/WhosWho/>`_.

The next best option is to ask your question in an email to the
mailing lists: `mesa-dev\@lists.freedesktop.org
<https://lists.freedesktop.org/mailman/listinfo/mesa-dev>`_


Bug reports
-----------

If you think something isn't working properly, please file a bug report
(`docs/bugs.html <https://mesa3d.org/bugs.html>`_).


Contributing
------------

Contributions are welcome, and step-by-step instructions can be found in our
documentation (`docs/submittingpatches.html
<https://mesa3d.org/submittingpatches.html>`_).

Note that Mesa uses gitlab for patches submission, review and discussions.
