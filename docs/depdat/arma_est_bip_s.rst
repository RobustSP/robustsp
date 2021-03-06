arma_est_bip_s
==============

The function arma_est_bip_s(x, p, q) comuptes the BIP S-estimation of the
ARMA model parameters. It also computes an outlier cleaned signal

Input
^^^^^^

* x		: numeric 1d-array, the data
* p		: scalar int, autoregressive order
* q		: scalar int, moving-average order
* meth		: string, method used for optimization in scipy.optimize.minimize.
	          Default = 'SLSQP'. 

Output
^^^^
* results 		: dict, with following fields

  1. 'ar_coeffs'	: AR coefficients

  2. 'ma_coeffs'	: MA coefficients

  3. 'inno_scale'	: BIP s-estimate of the innovations scale

  4. 'cleaned_signal'	: outlier cleaned signal using BIP-ARMA(p,q) predictions

  5. 'ar_coeffs_init'	: robust starting point for BIP-AR(p) MM-estimates

  6. 'ma_coeffs_init'	: robust starting point for BIP-MA(q) MM-estimates

Examples
^^^^

.. code-block:: python

   import numpy as np
   import robustsp as rsp
   import matplotlib.pyplot as plt

   np.random.seed(123)
   original_signal = xo = np.random.randn(100)

   corrupted_signal = x = original_signal + np.random.randn(100)*100

   result = rsp.arma_est_bip_s(x, 2, 0)


.. image:: abes.jpeg

Reference
^^^^

"Bounded Influence Propagation tau-Estimation: A New Robust Method for ARMA Model Estimation." 
Muma, M. and Zoubir, A.M.
IEEE Transactions on Signal Processing, 65(7), 1712-1727, 2017.