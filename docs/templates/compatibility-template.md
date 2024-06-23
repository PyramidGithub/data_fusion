Compatibility Guide
Comet aims to provide consistent results with the version of Apache Spark that is being used.

This guide offers information about areas of functionality where there are known differences.

ANSI mode
Comet currently ignores ANSI mode in most cases, and therefore can produce different results than Spark. By default, Comet will fall back to Spark if ANSI mode is enabled. To enable Comet to accelerate queries when ANSI mode is enabled, specify spark.comet.ansi.enabled=true in the Spark configuration. Comet's ANSI support is experimental and should not be used in production.

There is an epic where we are tracking the work to fully implement ANSI support.

Cast
Cast operations in Comet fall into three levels of support:

Compatible: The results match Apache Spark
Incompatible: The results may match Apache Spark for some inputs, but there are known issues where some inputs will result in incorrect results or exceptions. The query stage will fall back to Spark by default. Setting spark.comet.cast.allowIncompatible=true will allow all incompatible casts to run natively in Comet, but this is not recommended for production use.
Unsupported: Comet does not provide a native version of this cast expression and the query stage will fall back to Spark.
Compatible Casts
The following cast operations are generally compatible with Spark except for the differences noted here.

Incompatible Casts
The following cast operations are not compatible with Spark for all inputs and are disabled by default.

Unsupported Casts
Any cast not listed in the previous tables is currently unsupported. We are working on adding more. See the tracking issue for more details.
