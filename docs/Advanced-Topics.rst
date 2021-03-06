Advanced Topics
===============

Missing Value Handle
--------------------

-  LightGBM enables the missing value handle by default. Disable it by setting ``use_missing=false``.

-  LightGBM uses NA (NaN) to represent missing values by default. Change it to use zero by setting ``zero_as_missing=true``.

-  When ``zero_as_missing=false`` (default), the unshown values in sparse matrices (and LightSVM) are treated as zeros.

-  When ``zero_as_missing=true``, NA and zeros (including unshown values in sparse matrices (and LightSVM)) are treated as missing.

Categorical Feature Support
---------------------------

-  LightGBM offers good accuracy with integer-encoded categorical features. LightGBM applies
   `Fisher (1958) <http://www.csiss.org/SPACE/workshops/2004/SAC/files/fisher.pdf>`_
   to find the optimal split over categories as
   `described here <./Features.rst#optimal-split-for-categorical-features>`_. This often performs better than one-hot encoding.

-  Use ``categorical_feature`` to specify the categorical features.
   Refer to the parameter ``categorical_feature`` in `Parameters <./Parameters.rst>`__.

-  Categorical features must be encoded as non-negative integers (``int``) less than ``Int32.MaxValue`` (2147483647).
   It is best to use a contiguous range of integers.

-  Use ``min_data_per_group``, ``cat_smooth`` to deal with over-fitting (when ``#data`` is small or ``#category`` is large).

-  For a categorical feature with high cardinality (``#category`` is large), it often works best to
   treat the feature as numeric, either by simply ignoring the categorical interpretation of the integers or
   by embedding the categories in a low-dimensional numeric space.

LambdaRank
----------

-  The label should be of type ``int``, such that larger numbers correspond to higher relevance (e.g. 0:bad, 1:fair, 2:good, 3:perfect).

-  Use ``label_gain`` to set the gain(weight) of ``int`` label.

-  Use ``max_position`` to set the NDCG optimization position.

Parameters Tuning
-----------------

-  Refer to `Parameters Tuning <./Parameters-Tuning.rst>`__.

Parallel Learning
-----------------

-  Refer to `Parallel Learning Guide <./Parallel-Learning-Guide.rst>`__.

GPU Support
-----------

-  Refer to `GPU Tutorial <./GPU-Tutorial.rst>`__ and `GPU Targets <./GPU-Targets.rst>`__.

Recommendations for gcc Users (MinGW, \*nix)
--------------------------------------------

-  Refer to `gcc Tips <./gcc-Tips.rst>`__.
