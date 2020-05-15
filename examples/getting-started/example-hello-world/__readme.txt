welcome:

  Welcome to the ytt getting started tutorial
  
  ytt is a general-purpose YAML and text templating tool.
  
  For our tutorial, we will use real-world examples
  from a common use-case — managing Kubernetes configuration.
  You not not need know Kubernetes.
  
  The goal is to ease your learning ytt. We will...
  - introduce one concept at a time;
  - share ways of "Thinking in ytt" so you can be more
    productive;
  - point out common gotchas and give insight designed to
    unstick you.
  
  We recommend you...
  - read carefully. we have been economic with our words.
  - go in sequence. each lesson builds from the last.
  - poke, play, and break things.
  
---
yaml-in--yaml-out:

  There is no ytt code in the YAML, below.
  Yet... there are five (5) differences between the input
  and the output. Can you spot them all?

  When there is not any code, how are there differences?

  ytt...
  1) decodes your YAML file into a tree of YAML nodes.
  2) applies edits to those YAML nodes.
  3) encodes those YAML nodes into text output.

---
thinking_in_ytt:

  "build structures..."

                "...don't template text."
