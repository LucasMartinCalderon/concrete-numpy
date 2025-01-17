# Configure

Behavior of **Concrete Numpy** can be customized using `Configuration`s:

```python
import concrete.numpy as cnp
import numpy as np

configuration = cnp.Configuration(p_error=0.01, loop_parallelize=True)

@cnp.compiler({"x": "encrypted"})
def f(x):
    return x + 42

inputset = range(10)
circuit = f.compile(inputset, configuration=configuration)
```

Alternatively, you can overwrite individual options as kwargs to `compile` method:

```python
import concrete.numpy as cnp
import numpy as np

@cnp.compiler({"x": "encrypted"})
def f(x):
    return x + 42

inputset = range(10)
circuit = f.compile(inputset, p_error=0.01, loop_parallelize=True)
```

Or you can combine both:

```python
import concrete.numpy as cnp
import numpy as np

configuration = cnp.Configuration(p_error=0.01)

@cnp.compiler({"x": "encrypted"})
def f(x):
    return x + 42

inputset = range(10)
circuit = f.compile(inputset, configuration=configuration, loop_parallelize=True)
```

{% hint style="info" %}
Additional kwarg to `compile` function have higher precedence. So if you set an option in both `configuration` and in `compile` method, the value in the `compile` method will be used.
{% endhint %}

## Options

* **show_graph**: bool = False
  * Whether to print computation graph during compilation.

* **show_mlir**: bool = False
  * Whether to print MLIR during compilation.

* **verbose**: bool = False
  * Whether to print computation graph and MLIR during compilation.

* **dump_artifacts_on_unexpected_failures**: bool = True
  * Whether to export debugging artifacts automatically on compilation failures.

* **p_error**: float = 0.000063342483999973
  * Error probability for table lookups.

* **jit**: bool = False
  * Whether to use JIT compilation.

* **loop_parallelize**: bool = True
  * Whether to enable loop parallelization in the compiler.

* **dataflow_parallelize**: bool = False
  * Whether to enable dataflow parallelization in the compiler.

* **auto_parallelize**: bool = False
  * Whether to enable auto parallelization in the compiler.

* **enable_unsafe_features**: bool = False
  * Whether to enable unsage features.

* **virtual**: bool = False _(Unsafe)_
  * Whether to create a virtual circuit.

* **use_insecure_key_cache**: bool = False _(Unsafe)_
  * Whether to use the insecure key cache.

* **insecure_key_cache_location**: Optional[Union[Path, str]] = None
  * Location of insecure key cache.
