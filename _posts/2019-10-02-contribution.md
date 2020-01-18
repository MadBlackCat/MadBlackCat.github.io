#### 贡献：

- 隐私政策内容冗杂，提出了一个预料库，通过机器学习的方法帮助用户自动找到和我们定义好的主题相关的segment。
- 目前有一些隐私政策没有标题，用户阅读起来异常麻烦，帮助用户找出每个segment主要在描述哪些标题。
- 我们的标签是一篇隐私政策中都会以哪些标签为主题，或是标题，展开来叙述。

#### 与OPP-115 之间的区别

- 关于OPP-115任务相比， OPP-115的每一个segment都含有多个标签；我们是每一个段落只有一个标签。

- 某一个segment 在OPP-115中没有具体标签。比如：


 > We may access, preserve and share your information in response to a legal request (like a search warrant, court order or subpoena) if we have a good faith belief that the law requires us to do so. This may include responding to legal requests from jurisdictions outside of the United States where we have a good faith belief that the response is required by law in that jurisdiction, affects users in that jurisdiction, and is consistent with internationally recognized standards. We may also access, preserve and share information when we have a good faith belief it is necessary to: detect, prevent and address fraud and other illegal activity; to protect ourselves, you and others, including as part of investigations; and to prevent death or imminent bodily harm. Information we receive about you may be accessed, processed and retained for an extended period of time when it is the subject of a legal request or obligation, governmental investigation, or investigations concerning possible violations of our terms or policies, or otherwise to prevent harm. 


OPP-115在这一段对应的标签：3个Third Party Sharing/Collection；2个Data Retention；4个First Party Collection/Use。如果按照最多数量的标签的话是First Party Collection/Use。

在我们的标签中是：Legal Basis


> By using MuseScore, you authorize us to transfer and store your informationoutside your home country, including in the United States, for the purposesdescribed in this policy. The privacy protections and the rights of authoritiesto access your information in these countries may not be the same as in yourhome country.

在OPP-115中的Label并没有最合适的标签符合这一个segment，也许是International and
Specific Audiences或是Data Security。但是这两个标签的侧重面与这一段主要的要将内容完全不同。在我们的标签就可以是nternational Data Transfer。



- OPP-115语料库无法体现隐私政策中的每个segment主要在讲哪些内容。比如：


> Time Inc. sites will not use or transfer personally identifiable information provided to us in ways unrelated to the ones described above without also providing you with an opportunity to opt out of these unrelated uses.


OPP-115 中标签是2个Third Party Sharing/Collection，一个User Choice/Control，一个First Party  Collection/Use。给标签的时候会给成Third Party Sharing/Collection， 实际上却是User Choice/Control。




> We will retain your personal information while you have an account with us and thereafter for as long as we need it for purposes not prohibited by applicable laws. Thereafter, we will either delete your personal information or de-identify it so that it is anonymous and not attributed to your identity. Your rights to request that we delete your personal information are set forth in the "Accessing, Correcting, and Deleting Your Personal Information" section above. 


同理，OPP-115含有3个Data Retention， 3个User Access, Edit and Deletion 无法给出确定的Label。但是在我们的标注方案里是Data Retention。

- 针对于Cookies，Cookies在隐私政策中是很重要的一部分，在我们的数据中，有55%的segment主要以Cookies作为主要内容来说而在OPP-115中没有这一标签。

#### 与APP350之间的区别

- 我们最终的目的完全不同，APP350语料库主要是为了诊断隐私政策和安卓应用之间的不一致性。
- APP350和OPP-115一样是，对于一个segment有多个label
- APP350针对的只是几类具体的敏感信息比如Location，Demographic或是Contact，目的在于查找隐私政策中是否涉及到了这几类敏感信息，并对其有哪几种操作。