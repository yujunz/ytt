extract_common_values_into_variables:

  One aspect of managing configuration is extracting common
  values.

  With ytt this is as simple as declaring a variable, then
  defining the value of some YAML node to be that variable.

  Study "deployment.yml"...

  at the top — this "comment" escapes into ytt programming
    language — Starlark. Starlark is very much like Python.
    Here, we define two local variables, "app_name" and
    "version".
    These variables are scoped to just this file.

  within the YAML document - to set the value of a given
    YAML node to be that of the variable, just include the
    "comment" of Starlark code that references that
    variable.

---
DRYing_templates:

  Much of the point of extracting common values is to
  avoid duplicate code aka the "DRY principle" (i.e. Do not
  Repeat Yourself)

  at spec.template.spec.containers.name - notice that the
    containers name is also "prometheus-operator" yet we
    did not set that value to "app_name".
    In Kubernetes, the name of the container is not
    required to match any other value. It just so happens
    that the author picked the same name.
    "metadata.name" and "spec.template.spec.containers.name"
    may have the same value, but they have completely
    different meanings.

---
thinking_in_ytt:

   "Extract what *must* be the same..."

      "...not what is *coincidentally* the same."