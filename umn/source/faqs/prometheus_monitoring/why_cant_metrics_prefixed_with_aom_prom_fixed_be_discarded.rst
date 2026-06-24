:original_name: aom_06_0065.html

.. _aom_06_0065:

Why Can't Metrics Prefixed with aom_prom_fixed Be Discarded?
============================================================

Symptom
-------

Metrics prefixed with **aom_prom_fixed\_** cannot be discarded on the **Metric Management** page. In addition, these metrics are billed when being reported to AOM.

Possible Cause
--------------

For custom metrics named after Prometheus functions (such as **count**, **max**, **min**, **avg**, **sum**, **count_values**, **stddev**, **stdvar**, **group**, **bottomk**, **topk**, or **quantile**) or operators (such as **and**, **or**, or **unless**), AOM will add the prefix **aom_prom_fixed\_** to them when they are being reported to AOM to avoid PromQL query errors. For example, the original name of a custom metric is **count** and will be automatically converted to **aom_prom_fixed_count** when being reported. Due to name inconsistency, this metric fails to be discarded.

Solution
--------

Do not use any Prometheus function (such as **count**, **max**, **min**, **avg**, **sum**, **count_values**, **stddev**, **stdvar**, **group**, **bottomk**, **topk**, or **quantile**) or operator (such as **and**, **or**, or **unless**) as metric names. Name custom metrics in the format of "xxx_xxx_xxx".
