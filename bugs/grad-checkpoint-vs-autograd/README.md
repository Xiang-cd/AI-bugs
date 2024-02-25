
when using gradient checkpointing to do forward, then compute grad using torch.autograd.grad, it raises
```
RuntimeError: One of the differentiated Tensors appears to not have been used in the graph. Set allow_unused=True if this is the desired behavior.
```
because gradient checkpointing make some middle latents disappear, compute gragh seems broken in the view of `torch.autograd.grad`, assert your model that involves the grad computing has no gradient checkpointing.
