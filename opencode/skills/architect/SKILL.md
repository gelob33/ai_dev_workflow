---
name: architect
description: Design the shape of new code in code (types, signatures, module boundaries) before implementing. Use when a change crosses a function boundary or adds a new module.
---

# Architect

Design in the programming language, not in prose. The sketch is the contract.

1. Ground. Run the `how` skill on every system the new code touches. Skip only for true greenfield.
2. Start from the caller. Write the code a caller would write to use the feature. Types and signatures follow from that usage.
3. Sketch twice. Write two structurally different designs: types, function signatures, module layout, bodies left as `throw new Error("not implemented")` (or the language's equivalent) plus pseudocode. Different shapes, not two variants of one.
4. Pick. Compare on:
   - Can illegal states be represented? Fewer is better.
   - How small is the public surface for what it hides? Smaller is better.
   - Would a change that looks right from one file be right for the whole repo?
   - Does shared mutable state exist? Remove it if you can.
   Write three or four lines on why the winner won.
5. Commit the sketch on its own. Then fill in the bodies against it.
6. If filling in keeps fighting the sketch (repeated workarounds, casts to escape the types, special cases piling up), stop. Throw the sketch out and go back to step 3 with what you learned.

Adapted from pstack (MIT, Lauren Tan).
