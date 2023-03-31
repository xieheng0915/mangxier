##### reference: 
[chatGPT in depth demo: ](https://www.youtube.com/watch?v=rnIgnS8Susg)

[Sam Altman: OpenAI CEO on GPT-4, ChatGPT, and the Future of AI | Lex Fridman Podcast #367](https://www.youtube.com/watch?v=L_Guz73e6fw)
[Ilya Sutskever: Deep Learning | Lex Fridman Podcast #94](https://www.youtube.com/watch?v=13CZPWmke6A)
[Eliezer Yudkowsky: Dangers of AI and the End of Human Civilization | Lex Fridman Podcast #368](https://www.youtube.com/watch?v=AaTRHFaaPG8)
[Our Final Invention - Artificial General Intelligence (AGI)](https://www.youtube.com/watch?v=Y2d1AU7_JvM)
[SINGULARITY TIMELINE | ARTIFICIAL INTELLIGENCE + AGI + ASI (2023 - 2100¹⁰⁰)](https://www.youtube.com/watch?v=P5HNeahRYDM)


##### lex Fridman 采访 open AI CEO Sam Altman 概要归纳
我感觉我也不大会总结，就用以下列表的方式写一下，这里不遵循访谈中话题的时间顺序，想到什么写什么：  
- 关于chatGPT 的训练： Sam说其实训练的时间并不是太长，他们是基于结果，给GPT问题，假如让他回答十次，对十次回答结果分别打分，反馈给GPT，这个应该是DL当中的强化训练吧，效果很好。
- sam提到他们发现AI不是在计算（calculating, computing）而是在思考(thinking),这个是他感觉到有点害怕的。（不记得这个在哪个视频看到的，或许是ABC的采访片段里）Sam坦率地说将来或许会超出工程师的控制，不见得以后会完全align human。（大概这个发言是让很多科技大佬紧张的地方）而Lex也提到在chatGPT的回答中，他感觉到chatGPT是有一些思考的，并且感觉到有些问题他理解了，但回答错了。Lex又提到一些转换提问的方式，有时候能够套出一些不该说的话。
- 关于chatGPT的source code 有没有计划open source? 目前没有，因为不知道一旦公开之后会带来什么后果，Lex举了例子，新冠病毒是否从武汉实验室泄露，他说chatGPT的问答非常中立，因为目前没有非常确切的证据出现。sam 表示同意，并且说他们在训练chatGPT的过程中非常注意这些保持中立的言论的训练，他们的工程师非常有责任感。Lex追问是不是也有审查的顾虑，sam同意这也是一方面，twitter引发了很多争议，他们也想回避
- 关于GPT,chatGPT，以及AGI（泛化AI）：sam认为GPT-4虽然比GPT-3.5要更好，但GPT本身不是非常stunning，而chatGPT-4和chatGPT-3确实拉开了距离，并且有一点接近AGI
- 关于AI是否有意识的问题，sam表示他对于意识这个东西不是很确定,Lex追问是否有faked conscious（人造意识？）这一段两人的讨论陷入一种模糊，或许对于意识本身的认识还是没法说清楚。
- Lex也是一个程序员，他说他最近把IDE换到了vs，因为想用一下copilot x，而他用了之后发现非常棒，简直有点难以置信，同时感觉到有点可怕。Sam说，是的copilot确实会带来焦虑，并不是那些人说的只有shitty programmer才会焦虑，程序员们担心的是未来。
- 关于chatGPT 会不会夺走很多职业，sam 的回答是肯定的，但是他认为我们不应该为这个感到焦虑，当工业自动化出现的时候很多从事传统行业的人也感到焦虑，但后来都渐渐适应了。当科技发展的时候，一部分职业消失，而新的职业也会催生，很多人为了生存而工作，但也有很多人并非为了生存，工作有其他的意义，而社会福利应该致力于消灭贫穷。（这个我不完全同意，因为工作确实不仅仅是为了生存，还有个人在社会中得到的认可尊重，需要感价值等，可以参考一下美国的铁锈州，但另一方面新的职业或许会催生，而工作需要的时间会更少。总之应该会找到新的平衡，但其中一定有很多人沦为牺牲品，只是与其指责AI，不如说这是个无法阻挡的趋势。）
- 关于AI的危险性，尤其是AGI的危险性，目前主要是集中在一些fake news，操控媒体，比如FB曾经被指控用Fake news 操控美国大选，而那些fake news是一些专门制造这类假新闻的公司推送的。最代表性的是最近在网上疯传的假的罗马教皇穿白色羽绒服的照片，以及川普被逮捕的假新闻。更进一步可能是一些信息控制带来洗脑功能等。Sam表示同意，并且说这个需要政府的相关部门早日介入并立法。
- Lex问是否担心AI的力量过于强大，他提到了苏联的垮台，过于强大的政治专制体制会失去控制最后自己崩溃，但AI是一种更强大的专制力量，有没有可能控制人类，Sam表示乐观，他认为以后可能是很多AI，他们之间互相搏斗，然后形成了AI的民主社会（我听到这里脑补了一下环太平洋的画面，人进入巨大的变形金刚操控这些巨人）
- 关于如何雇佣好的员工，省略
- 关于leadership，省略

##### technical guide to GPT
昨天看了一下chatGPT的技术白皮书，大概是三种应用方式：
- API：用chatGPT的API，或者插件，纯应用
- fine-tuning: 用一些较小的数据集中train 一下专业领域的模型，然后应用
- retrain: 相对fine-tuning用略多的一些数据，训练成更专业的模型


