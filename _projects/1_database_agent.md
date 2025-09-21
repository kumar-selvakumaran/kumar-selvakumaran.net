---
layout: page
title: Database Assistant Agent
description: 
img: assets/img/project_gifs/db_agent_demo_short.gif
importance: 1
category: Projects
related_publications: true
---

[Github repo🔗](https://huggingface.co/spaces/KumarSel/database_agent/tree/main)

This project implements a ReAct {% cite yao2023react %} database agent in **LangChain**. The agent engages in a feedback loop with the database, using **multi-hop reasoning** to iteratively query and refine its understanding. Through this process, it leverages **in-context learning** to build knowledge about the database schema and contents until it has enough information to answer complex user questions. Finally, it responds with both the natural-language answer and the exact SQL commands it executed to obtain the result. The project was deployed as a [hugging Face Space](https://huggingface.co/spaces/KumarSel/database_agent)

{% include figure.liquid loading="eager" path="assets/img/project_gifs/db_agent_demo.gif" title="example image" class="img-fluid rounded z-depth-1" %}
<div class="caption">
    recording of an example run.
</div>

You can try it yourself below. Follow these steps:

1. enter your open router key below
2. ask it any question  about the database, eg: "what is the database about?"

if the below demo is not accessible, the deployment must have gone to sleep, you can restart and try it directly from the [huggingface spaces portal](https://huggingface.co/spaces/KumarSel/database_agent)

<iframe src="https://kumarsel-database-agent.hf.space" frameborder="0" width="850" height="450"></iframe>