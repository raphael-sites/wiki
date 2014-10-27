Simple human discourse model
===

Overlook of the model
---

![](https://docs.google.com/drawings/d/1z3DOPFLsRDmjqLN9DXBq-kmuGFB81NP8Vwx8S8nsmss/pub?w=600&amp;h=400)

Basically, only two types of utterance exist in this model.

Example
----

```
[Topic: job]
[Subtopic: B's job]
A: How is your new job? (question)
B: That is great (statement)
A: You seems really loves the job (statement)
[Subtopic: A's job]
B: What is your job? (question)
A: I'm a egg seller. (statement)
B: Sounds cool (statement)
[Topic: egg]
[Subtopic: whether B likes eggs]
A: By the way, do you like eating eggs? (question)
B: Huh, not really. (statement)
```

Semantic dependencies
---
In this example, we can see the content of responses are heavily relying on previous utterances. It turns out that previous 2 or 3 utterances.

Topic
---
At each time in the conversation, we all have a topic. And this topic changes over the time, but only changes at specified conditions. When a person changes the topic, he will use some transition phrases like "By the way".

Subtopic
---
The switching of subtopic is far more frequent than topic, a subtopic can be changed by a question or statement.

A chat bot based on this model
---

The following features are required.

- Learn how to make response with the context of previous 2 ~ 3 utterances.
- Learn how to infer and control the topic / subtopic.
- Learn how to determine next topic / subtopic and the timing to change.

A mind map
---

<iframe width="600" height="400" frameborder="0" src="http://www.mindmeister.com/maps/public_map_shell/470590046/conversation-model?width=600&height=400&z=auto&live_update=1" scrolling="no" style="overflow:hidden">Your browser is not able to display frames. Please visit the <a rel="nofollow" href="http://www.mindmeister.com/470590046/conversation-model" target="_blank">mind map: Conversation model</a> on <a rel="nofollow" href="http://www.mindmeister.com" target="_blank">Mind Mapping - MindMeister</a>.</iframe>

