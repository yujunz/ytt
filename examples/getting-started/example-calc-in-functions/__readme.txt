capture_calculations_in_functions:

  Functions in ytt can either explicitly return a value
  or implicitly return a YAMLFragment.

  In "deployment.yml", below...

  - "cpus()" and "memorys()" explicitly return resource
    values with units.
  - "request_50m_per_factor()" (implicitly) returns
    a YAMLFragment that is the resource configuration.

---
thinking_in_ytt:

  "Use Fragment Functions to capture
