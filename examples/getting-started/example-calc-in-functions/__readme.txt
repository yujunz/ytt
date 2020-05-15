capture_calculations_in_functions:

  Functions in ytt can either explicitly return a value
  or implicitly return a YAMLFragment.

  In "deployment.yml", below...

  - "cpus()" and "memorys()" explicitly return resource
    values with units.
  - "request_50m_per_factor()" implicitly returns
    a YAMLFragment that is the resource configuration.

---
changing_one_thing..:

  Note what happens when you change "scaling_factor" to 4.

  In Kubernetes, "replicas" must be an integer...
  - What happens when you change "scaling_factor" to 3?
  - How would you ensure "replicas" is an integer?

---
thinking_in_ytt:

  "How would I do it in Python?"

  https://github.com/bazelbuild/starlark#starlark
