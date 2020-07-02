* ```python
    tf.compat.v1.placeholder(dtype, shape=None, name=None)
* shape[None,N],None代表一维维度未知
* ```python
    tf.compat.v1.get_variable(
    name, shape=None, dtype=None, initializer=None, regularizer=None,
    trainable=None, collections=None, caching_device=None, partitioner=None,
    validate_shape=True, use_resource=None, custom_getter=None, constraint=None,
    synchronization=tf.VariableSynchronization.AUTO,
    aggregation=tf.compat.v1.VariableAggregation.NONE
    )
* 
