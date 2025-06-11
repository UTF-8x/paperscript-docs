# Naive Optimizations

Even with the simple V1 transpiler, we can already apply some naive optimizations that just require some crafty find-and-replace.

### GetActorRef / GetActorReference

{% hint style="info" %}
This proposal is not implemented
{% endhint %}

The performance of these calls can be improved by replacing them with `GetReference() as Actor`&#x20;

Suggested by [Pop000100](https://next.nexusmods.com/profile/Pop000100) on NexusMods
