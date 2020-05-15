extract_yaml_fragments:

  The next natural step is to extract not just a value,
  but a whole chunk of YAML — a YAML Fragment.

  In ytt, we declare a function. Its body contains a YAML
  fragment. We then set the value of a YAML node to
  contain the results of that function.

  We have done that in "deployment.yml"...

  at the top - we have defined a function "labels" that
    takes one argument, "withVersion".
    - it implicitly returns the YAML fragment it contains.
    - the "app.kubernetes.io/version" is included only if
      "withVersion" is "True". (notice that the Starlark
      boolean literal for truthy is capital-T, True).

  within the YAML document - we set the value to the
    various nodes that want for the extracted YAML fragment.
    - you can optionally name parameters when
      invoking a function in Starlark. In this case, makes
      the code more readable.
    - functions can declare default arguments as well. Here,
      calling "labels()" with no argument omits the
      "version" hunk.

---
its_still_yaml:

  Even as we see what looks like a function above a YAML
  document, do not forget this is a collection of YAML nodes
  with comments that contain what looks like Starlark code.

  See for yourself...
  1. remove line 11. note the error message. ytt complains
     that it expected a "document start" (i.e. "---").
     consider why...
  2. outdent just the YAML lines of "labels()" to the first
     column. the error message went away. Why?
  3. undo all those changes

  Likewise...
  1. indent line 8. ytt expects the value of each node to
     *either* come from a literal or from a Starlark value,
     but *not both*. With this indent, suddenly,
     "app.kubernetes.io/version" becomes a child of
     "app.kubernetes.io/name".
     now, "app.kubernetes.io/name" has two values —
     the string from "app_name" and the node
     "app.kubernetes.io/version".

  2. to make this even clearer, remove the ""#@ app_name"
     from line 6.
     Note how the various labels look in the output, now.

---
thinking_in_ytt:

   "ytt templates are sets of YAML documents..."

      "...with Starlark expressions commented in."
