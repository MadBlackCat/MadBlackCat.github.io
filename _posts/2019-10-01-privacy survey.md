---
\[tle: Privacy Policy Survey

tags: Paper

---
# 2013

### Privacy as Part of the App Decision-Making Process
They investigate how permissions and privacy could play a more active role in app-selection decisions. They designed a short “Privacy Facts” display, which they tested in a 20-participant lab study and a 366-participant online experiment. They found that by bringing privacy information to the user when they were making the decision and by presenting it in a clearer fashion, they could assist users in choosing applications that request fewer permissions. Through this paper, we can also find that most users do not pay attention to privacy when choosing an app download.

However , one of the main problems with this paper is that the paper was published in 2013 . In 2015 , Android 6.0 was released , and there are many new features of application rights management . The main thing is that after Android 6.0 , some of the more dangerous privacy permissions will prompt the user for authorization at the first time . (similar to IOS)



# 2014

### A Step Towards Usable Privacy Policy:Automatic Alignment of Privacy Statements

They divided the 1010 privacy policy into sections according to the subtitle and break the sections by lines for generating paragraph. They randomly extracted 1000 document pairs to generate section pairs and paragraph pairs, and divided the pairs into 4 parts according to the cosine similarity interval([0, 0.25], (0.25, 0.5], (0.5, 0.75], (0.75, 1]). They let the crowdworkers judge whether these pairs describe the same issue. Each section/paragraph pair was judged by five crowdworkers and was rewarded $0.05.



They used **the hidden Markov model** to capture local transitions between topics, and used **Expectation-Maximization \**(**EM**) and \**variational Bayesian** (**VB**) **inference** as estimation procedures. They combined these two methods with **CLUTO** to do a set of comparative experiments. At the same time their results can play a similar role to the lower half of crowdworkers.



# 2016

### The Creation and Analysis of a Website Privacy Policy Corpus

*S. Wilson, F. Schaub, A. Dara, F. Liu, S. Cherivirala, P.G. Leon, M.S. Andersen, S. Zimmeck, K. Sathyendra, N.C. Russell, T.B. Norton, E. Hovy, J.R. Reidenberg, N. Sadeh, **"The Creation and Analysis of a Website Privacy Policy Corpus"**, ACL '16: Annual Meeting of the Association for Computational Linguistics, Aug 2016*

Wilson et al. create a corpus of 115 privacy policy. They developed a policy secheme with ten data practice (First Party Collection/Use, Third Party Sharing/Collection, User Choice/Control, User Access, Edit, & Deletion, Data Retention, Data Security, Policy Change, Do Not Track, International & Specific Audiences, Other) formulated by domain experts. For a data practice, it will have many attributes. For example, for the data practice User Choice/Control, it have Choice Type, Choice Scope, Personal Information Type, Purpose and one optional attribute (User Type). Then skilled annotators used annotation tool which developed by authors to select data practice and its attributes. Besides that, they analysis the distribution of data practice and use logistic regression, SVM and HMM to predict privacy policy’s structure. They split ‘Other’ into three categories(Introductory/Generic, Practice Not Covered, and Privacy Contact Information). If two or more annotators agreed that a segment have a category, then they labeled that segment with that category.They used a 12 length binary vector to represent a segment. For the *i* th element, 1 represent this segment have the *i* th data practice. Otherwise it is 0. The result shows that the SVM model have the best effect.



### Automatic Extraction of Opt-Out Choices from Privacy Policies

目的在于找出隐私政策中关于Opt-Out的句子。作者设计了两种方法，用OPP-115作为数据集，第一种是简单的基于关键词组匹配，另一种是机器学习的方法，结论证明在这个任务中，词组匹配效果极其不理想，光是词组匹配肯定不够，所以使用了机器学习的方法。

![1570550554260](F:\Desktop\MadBlackCat.github.io\assets\1570550554260.png)



### Analyzing Vocabulary Intersections of Expert Annotations and Topic Models for Data Practices in Privacy Policies

In this paper, the author uses NMF to generate a topic of privacy policy, assuming that the topic model generated using the unsupervised method has a one to one mapping relationship with the categories proposed by legal experts in Wilson et al. They use the Logistic Regression model to extract the keywords for each data practice. After that, they use NMF to generate the topic, and corresponding to each topic, the corresponding keywords can be generated. Each category and topic can then be represented by the extracted keywords. They analyzed the relationship between topic and category by analyzing the Jaccard Similarity of topic and category keywords. Their results indicate a meaningful mapping between the topic model and the expert-defined categories. Unfortunately, there is no One to One mapping, mostly One to Many, Many to One or Many to May.



### Extracting keyword and keyphrase from online privacy policies.

Audich et al.[9] used RAKE, TextRank, AlchemyAPI, TF-IDF for keyword and key extraction on small data sets and large data sets, respectively, and compared them with manual extraction results. The small data set comes from 21 privacy policies on the most visited websites in Wikipedia. The big data set comes from 631 privacy policies in the Data Management and Privacy Governance Lab at the University of geulph. It was found that TF-IDF performed well on manual annotations on small datasets of 21 strategies, while AlchemyAPI performed slightly better on TF-IDF on \larger datasets. Due to the lack of standardized languages used in online privacy policies, algorithms that evaluate individual documents (TextRank, RAKE, AlchemyAPI) perform better than significant marginal algorithms that extract keywords from larger corpora (TF-IDF). Their results show that natural language processing techniques are still a challenging task for retrieving keywords and key phrases from legal and semi-legal documents




#2017
### Helping Users Understand Privacy Notices with Automated Question Answering Functionality: An Exploratory Study
*Kanthashree Mysore Sathyendra, Abhilasha Ravichander, Peter Garth Story, Alan W Black, Norman Sadeh, **"Helping Users Understand Privacy Notices with Automated Question Answering Functionality: An Exploratory Study"**, Carnegie Mellon University Technical Report CMU-ISR-17-114R and CMU-LTI-17-005, Institute for Software Research and Language Technologies Institute, School of Computer Science, Dec 2017*

**在这篇论文里提到了4个有用的数据集：**

- **OPP-115 Corpus**
- **35,000 privacy policies shared with us by researchers working on the PriBot**
  **project [14]**
- **Dataset of privacy related questions submitted via Twitter, also shared with us by the PriBot project [14]**
- **6,000 privacy policies crawled from the web**

目的在于研究一套QA系统，在这篇论文中只提到了初步工作。作者研究出了Closed QA 与 Open QA approaches两种方法。

Closed QA方法先假设可以把所有的问题分类到几个与设计好的问题上，再自动找答案。作者将OPP-115中的标签转化为三个等级，Value Level (Finest), Attribute Level, Category Level (Coarsest)，但是作者通过实验发现，并不是所有的问题都可以转化为预先设计好的标签之中。

在 Open QA中，作者将每个segment视为一个候选答案，寻找和问题最符合的segment。在这里由于数据集的缺失，作者将每个segment的标题设计成问题，并将why/when/how/what添加到标题的开始作为问题，一共有3,00,000个问题答案对。均使用的是附有Attention的双向LSTM模型，最后用余弦相似度来计算相似性。

![1570525764329](F:\Desktop\MadBlackCat.github.io\assets\1570525764329.png)

#### Future

- 增加相关数据集
- 可以确定所提问题不在隐私政策中
- 在句子级别作分析
- 加入Coreference resolution
- 通过对话系统提高性能
- 语音小助手



### Nudges for Privacy and Security：Understanding and Assisting Users’ Choices Online

*A. Acquisti, M. Sleeper, Y. Wang, S. Wilson, I. Adjerid, R. Balebako, L. Brandimarte, L. F. Cranor, S. Komanduri, P. G. Leon, N. Sadeh, and F. Schaub, **"Nudges for Privacy and Security"**, ACM Computing Surveys (CSUR), 50, 3, Oct 2017*

讨论了关于隐私政策上面关于user choices的潜在好处和缺点，关键性问题，未来面临的挑战。



### Identifying the Provision of Choices in Privacy Policy Text

*Kanthashree Mysore Sathyendra, Shomir Wilson, Florian Schaub, Sebastian Zimmeck, and Norman Sadeh, **"Identifying the Provision of Choices in Privacy Policy Text"**, Conference on Empirical Methods in Natural Language Processing (EMNLP), Copenhagen, Denmark, Sep 2017* 

粗粒度的分类模型，作者合并使用OPP-115作为数据集，在数据里面属性标有opt-out属性的句子作为正样本，其余的作为负样本。将隐私政策分为85和35分别作为训练集和测试集，在句子层级上使用逻辑回归模型来作为分类器的分类。

![1570536501331](F:\Desktop\MadBlackCat.github.io\assets\1570536501331.png)

细粒度模型，此外作者从Alex排名上180 个最受欢迎的网站上抽取含有超链接的句子，一共2842个句子，使用训练好的粗粒度的分类模型并且人工验证出了124个正样本。并在更细的标签上进行人工标注（有两个label分别是Party Offering Choice和Purpose，每个label都含有First Party (FI), Third Party, (TH), 或 Browser (BR)），并在这124个句子上使用逻辑回归做8（2个label*4）个做更细层次上的分类。由于数据稀疏，只显示了最频繁的前两个类别进行展示。

![1570536460190](F:\Desktop\MadBlackCat.github.io\assets\1570536460190.png)

### **Increasing the Salience of Data Use Opt-Outs Online**

*N. Nisal, S.K. Cherivirala, K.M. Sathyendra, M. Hagan, F. Schaub, S. Wilson, L.F. Cranor, N. Sadeh, **"Increasing the Salience of Data Use Opt-Outs Online"**, SOUPS ’17: Symposium on Usable Privacy and Security, USENIX, Jul 2017 Poster*

由于隐私政策非常冗长，所以很少人去阅读原文，许多用户关心自己可以对自己的隐私有那些操作。作者开发了一个谷歌插件可以自动找出隐私政策中的用户决策部分，使用的的方法是 **Identifying the Provision of Choices in Privacy Policy Text** 提到的方法。

### **Mobile App Privacy Compliance: Automated Technology to Help Regulators, App Stores and Developers**

*S. Zimmeck, Z. Wang, L. Zou, R. Iyengar, B. Liu, F. Schaub, S. Wilson, N. Sadeh, S.M. Bellovin, J.R. Reidenberg, **"Mobile App Privacy Compliance: Automated Technology to Help Regulators, App Stores and Developers"**, SOUPS ’17: Symposium on Usable Privacy and Security, USENIX, Jul 2017 Poster*

开发了一套判断安卓应用和隐私政策一致性的系统用来追踪安卓应用不合法。使用的是 **"Automated Analysis of Privacy Requirements for Mobile Apps"** 提到的方法来检测的。

![1570539417519](F:\Desktop\MadBlackCat.github.io\assets\1570539417519.png)

### A Data Purpose Case Study of Privacy Policies

*Jaspreet Bhatia, Travis D. Breaux, **"A Data Purpose Case Study of Privacy Policies"**, 25th IEEE International Requirements Engineering Conference, RE:Next! Track, Lisbon, Portugal, Jun 2017*

为了帮助公司更好地写出关于收集数据目的的隐私政策，作者研究了5个购物领域的隐私政策，探讨描述用户手机信息目的的不同方法。作者标注了这5篇隐私政策，总共标注有218个数据的目的，并且将其分为六个类别：

- Service Purpose (SP) 
- Legal Purpose (LP)
- Communication Purpose (CP) 
- Protection Purpose (PP)
- Merger Purpose (MP)
- Vague Purpose (VP)


描述收集信息目的的类别有以下：
- DP – 句子中只包含数据的目的
- K-DP – 有一个关键字在最前面，之后收集数据的目的的详细叙述 
- IT-K-DP – 收集数据的类型，数据目的关键词，收集数据的目的的详细叙述
- K-DP-IT - 关键词在最前面，其次是数据目的的详细叙述，最后才是数据类型（此类稀有）
- K-IT-K-DP - 关键词-数据类型-关键词-数据目的，第一个关键词表示，这一句话是用来描述收集数据目的存在，比如关键词（"use"）
  

![1570542036049](F:\Documents\documents\img\1570542036049.png)



### Automated Analysis of Privacy Requirements for Mobile Apps

*S. Zimmeck, Z. Wang, L. Zou, R. Iyengar, B. Liu, F. Schaub, S. Wilson, N. Sadeh, S.M. Bellovin, J.R. Reidenberg, **"Automated Analysis of Privacy Requirements for Mobile Apps"**, NDSS'17: Network and Distributed System Security Symposium, Feb 2*

Zimmeck, Sebastian, et al. [4] propose a novel combination of machine learning (ML) and static analysis techniques to analyze apps’ potential noncompliance with privacy requirements. They define privacy requirements as follows: Privacy Policy Requirements, Notice Policy Change (NPC), Notice Access,Edit, and Delete (NAED), Collection IDentifier (CID), Collection Location (CL), Collection Contact (CC), Sharing IDentifier (SID), Sharing Location (SL) and Sharing Contact (SC). They first analyze the privacy policy, they used support vector machines and logistic regression to classify privacy policies, then they analyzed apps, they determine the actual privacy practice of the application by statically analyzing the API code of the application. Finally they compare policy analysis results to what apps actually do according to their code to determine the inconsistency.

They provide a tool that automatically analyzes the inconsistencies between Apps and their privacy policy descriptions. Their research law defines nine practice, namely privacy policy requirements, NPC, NAED, CID, CL, CC, SID, SL, SC. They crawled 17,991 apps from Google Play, of which 9295 apps have links to privacy policies. For each exercise, the keywords are extracted with tf-idf and Information Gain, and then the sentences containing the keywords are extracted and converted into unigram and bigram feature carriers. They used OPP-155 as a training set and classified the privacy policies of 9295 applications using SVM and LR models.

For the app, they use a static analysis method to determine what the app does by analyzing their api and permission. For the full app/policy set (n = 9,050) they found that 2,455 apps have one potential inconsistency, 2,460 have two, and only 1,461 adhere completely to their policy. Each app exhibits a mean of 1.83 (16,536/9,050) potential inconsistencies.

# 2018

### A comprehensive keyword analysis of online privacy policies

Kaur et al. They collected privacy policies from different domain and countries. They fist used 2000 policies that were collected by Massey, Eisenstein, Antón, and Swire (2013). Then they collected 600 policies covering 11 different application domains from Alexa. They also collected financial and e-commerce related privacy policies from USA, Canada and Europe(German and UK). They define some sections(Collection, Sharing, Choice, Access, Data retention, Data security, Policy change, Do not track, Purpose) according to the FTC and OECD FIP practices as well as recent work of Guntamukkala et al. (2015) and Wilson et al. (2016). They first use Tokenization, Stop word removal and Stemming to pre-process these privacy policy. They fed into LDA with keywords annotated by Guntamukkala et al. (2015) and Wilson et al. (2016) for LDA to extract more keywords for each section. They also studied the use of ambiguous words in privacy policies. This list is taken from Guntamukkala et al. (2015) and Reidenberg, Bhatia, Breaux, and Norton (2016). They analyzed coverage of sections in 2000 privacy policies, USA, Canada and UK, different domain. They calculated the word frequency of ambiguous words in the 2000 privacy policy. The five most commonly used words were *may*, *certain*, *for example*, *except*, and *like*. the top three ambiguous words in USA, Canada, UK and German policies are *may* , *will*, and *can*. The top 5 ambiguous words in 11 different domains are *may*, *share*, *certain*, *like*, and *for example*.

Then they analyze data protection regulation about UK, Canada, USA, Germany and different domains. For example, the UK restricts the retention of data, but few privacy policies mention relevant keywords. The UK does not recommend collecting *email*, *name*, and *addresss* information, but there are many privacy policies that mention these keywords. PIPEDA requires confirmation from the user before collecting user data. So Canada’s privacy policy uses a lot of *consent*keywords. In addition, Canada uses a lot of *update* and *delete* keywords. This shows that users have the right to access their data. Compared with other countries, the *security* keyword is also the most used in the privacy policy of Canada. The emphasis is on data transparency. Therefore, the keyword *retention*, *retain* appears very frequently, but the frequency of *delete* and *update* is not high. Germany’s privacy policy does not use the keywords *phone*, *share*, *retain*, *disclose* and *password*. The keywords *delete*, *access*, *email*, *update*, *retention*, and *notice* are rarely used. This may have a lot to do with the relevant German laws.

In healthcare domain, privacy often uses *name*, *age*, *address*. Most health care collects personal information. The *security policy numbers* and s*ocial security numbers*. However, the frequency of these keywords is not very high. In shopping domain, privacy policy often uses *payment* , *information*, *site analytics*, and *behavioral* *Tracking* these keywords, keywords like *name*, *email*, *address*, and *contact information* such as *phone number*, *mobile*, *location* are frequently used in e-commerce policies. In kids domain, privacy policy rarely collects *security*, *SSL*, *safeguard*, and *socket Layer* these keywords.

The above results are only part of the results of their analysis. This paper analyzes the privacy policies of different countries and different countries in detail, which can be used as a reference when writing privacy policies.



### Towards Automatic Classification of Privacy Policy Text

*Frederick Liu, Shomir Wilson, Peter Story, Sebastian Zimmeck and Norman Sadeh, **"Towards Automatic Classification of Privacy Policy Text"**, Carnegie Mellon University Technical Report CMU‐ISR‐17‐118R and CMU‐LTI‐17‐010, Institute for Software Research and Language Technologies Institute, School of Computer Science, Jun 2018*



#### Information:

一般隐私政策的内容非常冗长，用户阅读起来非常困难。作者使用 Wilson et al. 的研究成果（他们提供了一份关于隐私政策的语料库）作为他们的数据集， 使用 Support Vector Machines, Logistic Regression,  CNN 分别对隐私政策的文本进行Sentence子和Segment层级的分类。其中标签为 Wilson et al. 数据集中的 Privacy Practice Category分别为 *First Party Collection/Use*, *Third Party Sharing/Collection*, *User Choice/Control* , *User Access, Edit, & Deletion* , *Data Retention* , *Data Security*, *Policy Change*, *Do Not Track* , *International & Specific Audiences*.



#### Detail

在使用Wilson et al. 数据集时涉及到一个问题，就是将语料库转换为标签。在原本语料库中，每个标注信息的text span是不一样的，每个segment有可能含有多个标注信息。所以对于每个segment，如果有两个标注者或以上认为其含有同一个privacy policy category，则赋予该segment这一个privacy policy category作为标签。Sentence层级同理，如果有两个标注者或以上标注了这个sentence中任意部分为同一个privacy policy category，则赋予这个privacy policy category作为该sentence的一个标签。

在输入分类器做分类之前，用Tf-Idf作为文本的向量特征



####  Result

![1570362268967](F:\Desktop\MadBlackCat.github.io\assets\1570362268967.png)

如表所示，segment分类效果要比sentence好。sentence分类器中CNN最好， Segment分类器中LR最好。ACL16为 Wilson et al. 分类任务中效果最好的结果。



### An Empirical Analysis of Website Data Deletion and Opt-Out Choices

*H. Habib, Y. Zou, A. Jannu, C. Swoopes, A. Acquisti, L.F. Cranor, N. Sadeh, F. Schaub, **"An Empirical Analysis of Website Data Deletion and Opt-Out Choices"**, CHI 2018 Workshop on General Data Protection Regulation: An Opportunity for the HCI Community?, Apr 2018*

*ACM*

#### Information:

这篇文章主要目的是分析隐私政策中的data deletion, email,和 targeted advertising choices是以何种形式出现的。

作者手动分析了美国十个最受欢迎的网站Amazon，Craigslist，eBay，ESPN ，Facebook，Google，Tumblr，Twitter，Wikipedia和Yahoo。作者定制了一个标注模板来收集隐私政策中的data deletion, email,和 targeted advertising choices。标注的内容有choice所在的位置，到该choice需要访问超链接的个数，隐私政策中提到他的其他信息。

初步结果表明，关于流行网站隐私政策中的data deletion 和 consent的choices并不是都有。有一部分网站仅通过隐私政策提供广告的opt-out，其他的则是在用户设置中提供这个选项。在隐私政策中，用于描述包含选择退出的部分的术语在各个网站之间似乎也不一致。这些类型的不一致可能使用户更难找到隐私选择并对其采取行动。未来作者为隐私选择开发标准化平台，从而为用户简化此过程。

作者下一步将是使用注释模板和自动分析工具来分析更多网站的隐私选择。我们将主要关注Alexa全球500强网站，因为这些网站影响了大多数互联网用户。同时还计划包括一个较小的样本，该样本是从Alexa 500强至10,000个网站中随机选择的，以探讨隐私选择在不同网站上是否有所不同。最终开发一个关于用户隐私政策选项选择的平台。

```

（在本节中，我们根据Amazon Alexa排名靠前的网站的排名，介绍了在美国十个最受欢迎的网站上试用我们的数据收集模板的一些见解。3我们的试用版中包括的十个网站是Amazon，Craigslist，eBay，ESPN ，Facebook，Google，Tumblr，Twitter，Wikipedia和Yahoo。这些初步结果仅来自通过我们的分析模板收集的一部分数据。此外，由于该试验样本仅由受欢迎的网站组成，因此这些结果可能无法代表流量较少的网站以及整个Internet上可用的隐私选择。总体而言，我们发现这些网站中的大多数都提供隐私选项，但是网站在向用户展示它们的方式方面有所不同。

被评估的十个网站中有八个提供了帐户设置中的行销或电子邮件通讯选择退出。提供的大多数选择退出与网站营销有关，但某些网站还包括选择退出新闻通讯和活动更新的选项。根据我们的分析，其中一个网站Craigslist不会向用户发送任何营销信息。在这8个提供与电子邮件相关的选择退出的网站中，有7个网站的隐私权政策中包含有关选择退出通信的信息。四个网站还指定，电子邮件通信将在电子邮件中包含“取消订阅”功能。图2汇总了这些选择退出在网站上的位置。

要查看隐私政策在何处选择退出电子邮件通信，隐私政策中包含电子邮件选择退出的七个网站中有四个网站在策略中的标题下标有“选择”或“偏好”，而两个人在节标题中明确使用了“电子邮件”一词。与其他消息不同，Twitter在其隐私权政策的标题为“信息收集和使用”的部分描述了电子邮件的退出。

我们分析了相同的十个网站的与定向广告相关的退出服务。七个网站在其隐私权政策中提供了有关广告退出的信息。十个网站中的五个通过链接到首页的有关广告惯例的信息页（例如“关于广告”）展示了广告退出选项，其中五个在用户帐户设置中包含了广告退出设置。四个网站通过这三种方式提供了广告退出选择。维基百科和Craigslist在其隐私权政策中指出，他们不投放定向广告。图3总结了网站上广告退出的位置。

在提供与广告相关的选择退出的七个网站中，六个具有站点实施的广告选择退出功能。这六个中的三个也通过DAA或NAI退出工具提供了退出，而一个网站（ESPN）仅提供了指向DAA退出服务的链接。在隐私权政策中，描述广告退出的位置有所不同。其中四个网站以与“选择”相关的标题描述了它们，两个网站在标题中包含了“信息”，而一个网站（雅虎）在“个性化体验”下对其进行了描述。

总共分析的十个网站中有七个提供了至少一种机制供用户删除其帐户或与帐户有关的信息。四个网站在隐私策略和用户帐户设置中都提供了帐户删除机制，其中两个仅在帐户设置中提供了帐户删除机制，而Yahoo仅在隐私策略中提供了帐户删除选项。图4总结了这些选择退出在网站上的位置。五个网站中的四个在其隐私权政策中以“删除”或“修改”一词描述了帐户删除机制，而ESPN的政策则在“您的控制和选择”下描述了帐户删除机制。）

````

### Supervised and Unsupervised Methods for Robust Separation of Section Titles and Prose Text inWeb Documents



*Abhijith Athreya Mysore Gopinath, Shomir Wilson, and Norman Sadeh, **"Supervised and Unsupervised Methods for Robust Separation of Section Titles and Prose Text in Web Documents"**, Conference on Empirical Methods in Natural Language Processing (EMNLP), Brussels, Belgium, Nov 2018*



#### Information

目的是为了抽出文档中的标题。由于html的灵活性，在html中可以使用不同的代码来形成相同的标题格式，同时html中还包含了很多无关紧要的信息比如很多link，很难根据html代码去找到原始的标题与正文之间的关系。作者开发了一套系统ASDUS (Automatic Segment Detection using Unsupervised and Supervised learning)可以使用文本特征和标记结构自动区分标题和正文的结构。这套系统可以去除掉不相关的html并提供一个仅体现出标题和正文格式的简化版本的html。

#### Detail

数据集有3种，第一个是152个网站的privacy policies，80来自Amazon Alexa’s top 100 websites list，72来自Google Trends。第二个是www.randomlists.com随机生成200个网站，之后筛选出100个网站的英文terms of service。第三个，在Google上搜索特定领域的关键词，收集出现在前2-4个搜索结果网站页面。

这套系统有两种方法，一个是不依靠领域的无监督聚类方法Domain-Independent Approach (DI)，另一个是依靠领域的监督性的学习方法。在DI中，使用jsoup来抽取text以及text的xpath路径，使用文本长度、下一个文本的长度、标点符号的个数、句子个数、stop words的个数、discourse cues的个数、named entity slots的个数、单词的个数作为特征。其中，文本长度作为一个维度，其余特征作为另一个维度，形成最终的特征向量，聚类方法使用kmeans。DD方法中，手动标记100个隐私政策为标题，正文，不相关。使用word embedding分别给标题和正文建立embedding模型，并分别计算两 embedding后的segment text的log probability，将这两种log probability与文本长度放在一起作为前馈型神经网络的输入进行分类。

![1570432604742](F:\Desktop\MadBlackCat.github.io\assets\1570432604742.png)

![1570432626948](F:\Desktop\MadBlackCat.github.io\assets\1570432626948.png)

### Which Apps have Privacy Policies?

*Peter Story, Sebastian Zimmeck, Norman Sadeh, "Which Apps have Privacy Policies?", Annual Privacy Forum, Jun 2018* 

目前Google Play上面的应用有很多没有隐私政策的链接，根据作者收集的一百万个应用的数据，大约有一半的应用没有隐私政策链接。作者通过使用LR模型来预测一个应用有隐私政策的可能性。使用的特征是评分， 安装个数，app类别，app开发商的国家，发布日期， Editors' Choice， 价格， 评分人数。

结果：accuracy = 67.7%, precision = 65.1%, recall = 61.5%, F1 = 63.2%

### Semantic Incompleteness in Privacy Policy Goals

*J. Bhatia and T. D. Breaux, **"Semantic Incompleteness in Privacy Policy Goals"**, IEEE 26th International Requirements Engineering Conference (RE), Banff, AB, Canada, Aug 2018* 



作者手动分析了5个隐私政策，在4种data actions（collection, retention, usage, transfer）识别出来了不同的semantic roles与相应的values。在5个隐私政策中作者贡献出了281 个 data action，17 种semantic roles。主要目的是检测隐私政策中描述的不完整性。

描述不完整的例子：

- 使用用户的信息却没有写使用的目的。

17 种semantic roles：

- Subject: The entity which acts on the information. (Who is
performing the data action?)
- Object: The data on which the action is being performed. The
values of this role were information types in our study. (What
is being acted upon?)
- Purpose: The goal or justification for which the action is
performed. (Why is the information being acted upon?)
- Condition: The states or events under which the data action
will be performed on the information. (When will the data
action be performed?)
- Source: The provider of the information in a collection action.
(From whom is the information collected?)
- Target: The recipient of the information in the transfer action.

- Action location: The location where the action is performed.

- Comparison: Comparison of the action with other action(s).

- Constraint: The restrictions on the action.

- Duration: The duration for which the action will be performed.

- Exception: Describes an exception to the action.

- Retention property: This role describes how the information is
  retained. Example role value from Costco policy: separately from
  other member databases.

- Hypernymy: A more generic semantic role value with specific
  values.

- Instrument: The medium with which the action is performed.

- Negation: The presence of this role signals that the action will not be
  performed.

- Retention location: The location at which the object of the retention
  action is retained.

- Time of action: The time at which

#### Result

作者观察到近32％的Retention声明的semantic role是不完整的。另外，对于条件角色，有45％的Transfer不没有condition role，而对于目的角色，有19％的使用没有purpose role。



### Analyzing Privacy Policies at Scale: From Crowdsourcing to Automated Annotations

*Shomir Wilson, Florian Schaub, Frederick Liu, Kanthashree Mysore Sathyendra, Daniel Smullen, Sebastian Zimmeck, Rohan Ramanath, Peter Story, Fei Liu, Norman Sadeh, Noah A. Smith, **"Analyzing Privacy Policies at Scale: From Crowdsourcing to Automated Annotations"**, ACM Transactions on the Web, 13, 1, Dec 2018*



目的在于分析衡量众包注释隐私政策的准确性以及如何提高众包的标注生产率。

- 证明了一致性越高，准确率越高。
- 使用相关性模型高亮隐私政策中的一小部分，可以帮助标注者更快标注数据，而没有减少标注数据的准确性。
- 上一个方法展示了描述了半自动的标注方法，所以试一下全自动方方法即如何给隐私政策分类（使用的是Wilson 等人的方法）
- 自动找到隐私政策中的user choices（Kanthashree Mysore Sathyendra等人的方法）



# 2019

###  Natural Language Processing for Mobile App Privacy Compliance

*Peter Story, Sebastian Zimmeck, Abhilasha Ravichander, Daniel Smullen, Ziqi Wang, Joel Reidenberg, N. Cameron Russell, and Norman Sadeh, **"Natural Language Processing for Mobile App Privacy Compliance"**, AAAI Spring Symposium on Privacy Enhancing AI and Language Technologies (PAL 2019), Mar 2019*

### MAPS: Scaling Privacy Compliance Analysis to a Million Apps

*Sebastian Zimmeck, Peter Story, Daniel Smullen, Abhilasha Ravichander, Ziqi Wang, Joel Reidenberg, N. Cameron Russell, and Norman Sadeh, **"MAPS: Scaling Privacy Compliance Analysis to a Million Apps"**, Privacy Enhancing Technologies Symposium (PETS 2019), 3, Jul 2019* 

第一篇文章是第二篇文章的重要组成部分。主要都是检测app与隐私政策之间的不一致性。MAPS是一个可以在整个应用商店范围内评估安卓应用的系统，他的实现方法是Peter Story提供的方法。

作者标注了 350个隐私政策作为语料库。里面对应每个segment含有First Party/Third Party， 收集的信息， 正面收集还是负面收集三个信息。

作者使用SVM作为分类器对文本进行分类（(Identifier, Identifier IMSI, Identifier SIM Serial, and Identifier SSID BSSID四类数据使用的是基于关键词搜索的分类方法）。训练时，在训练集和验证集中加入了一些手动将正面收集更改为负面收集的数据用来平衡正面和负面收集的数据差。

app方面通过分析api和permission的调用来判断相关内容是否调用。验证时作者手动验证了100个隐私政策。从表一和表二中可以看出来，第三方收集的信息要更多并且与表一隐私政策分析的结果是不一致的。

下面三个表中中+为正面收集，-为不收集，？为人工解析失败的。表一为隐私政策分类结果，表二为app源码分析结果，测试集都是相同的100个app。表三是app一致性的结果。

![1570464064144](F:\Desktop\MadBlackCat.github.io\assets\1570464064144.png)

![1570464349525](F:\Documents\documents\img\1570464349525.png)

![1570464523535](F:\Documents\documents\img\1570464523535.png)





### Quantifying the Effect of In-Domain Distributed Word Representations: A Study of Privacy Policies

*Vinayshekhar Bannihatti Kumar, Abhilasha Ravichander, Peter Story, and Norman Sadeh, **"Quantifying the Effect of In-Domain Distributed Word Representations: A Study of Privacy Policies"**, AAAI Spring Symposium on Privacy Enhancing AI and Language Technologies (PAL 2019), Mar 2019* 



#### Information

Kumar et al.  目的为了证明，使用专门领域内的数据集训练过的词向量比网上训预练好的词向量效果要好。作者在150,000个隐私政策上使用fasttext训练得到100维和300维词向量，并将其与glove的预训练好的词向量分别将OPP-115转换为特征向量， 并输入SVM, Feed-forward network和Deep Convolutional Model 分类器在segment层级进行分类（转换标签的格式和Liu et al.相同）。

#### Result

对比几个模型，同样使用300维fasttext词向量下，Feed-forward network分类效果最好，并超过了Liu et al. 的分类效果。![1570379635691](F:\Desktop\MadBlackCat.github.io\assets\1570379635691.png)



对比100维和300维，无论是fasttext还是glove，结果显示使用300维词向量比100维词向量效果好。

同时，作者在训练fasttext词向量时使用不同数量的隐私政策，观察其最后效果如何，发现其效果均在20,000后保持相对稳定。

![1570380752936](F:\Desktop\MadBlackCat.github.io\assets\1570380752936.png)





### Challenges in Automated Question Answering for Privacy Policies



*Abhilasha Ravichander, Alan Black, Eduard Hovy, Joel Reidenberg, N. Cameron Russell, and Norman Sadeh, **"Challenges in Automated Question Answering for Privacy Policies"**, AAAI Spring Symposium on Privacy Enhancing AI and Language Technologies (PAL 2019), Mar 2019*



作者通过众包的方法分析了1350个用户可能提到的关于隐私政策的问题。并揭露了目前隐私政策中的自动Q/A系统将会面临的问题：

- 用户问的问题通常是模棱两可的，有时提出与隐私政策无关的问题
- 系统必须能够用其他信息来源（例如背景法律知识）来补充在隐私政策中发现（或缺少）的信息
- 用户有时会问的问题隐私政策描写的不清楚
- 用户问的问题隐私政策没有写



![1570439798941](F:\Desktop\MadBlackCat.github.io\assets\1570439798941.png)



### APIs and Your Privacy

*N. Cameron Russell, Florian Schaub, Allison McDonald, William Sierra-Rocafort, **"APIs and Your Privacy"**, Jan 2019*

本文目的在于帮助写隐私政策的人了解和清楚移动应用和网站是如何使用api来收集使用和分享数据的。

### An Empirical Analysis of Data Deletion and Opt-Out Choices on 150 Websites

*Hana Habib, Yixin Zou, Aditi Jannu, Neha Sridhar, Chelse Swoopes, Alessandro Acquisti, Lorrie Faith Cranor, Norman Sadeh, Florian Schaub, **"An Empirical Analysis of Data Deletion and Opt-Out Choices on 150 Websites"**, Fifteenth Symposium on Usable Privacy and Security (SOUPS 2019), Aug 2019* 

和An Empirical Analysis of Website Data Deletion and Opt-Out Choices目的相同，只不过这次数据集比较大。都是手动分析。





### Trustworthy Privacy Indicators: Grades, Labels, Certifications, and Dashboards

*Reidenberg, Joel R. and Russell, N. Cameron and Herta, Vlad and Sierra-Rocafort, William and Norton, Thomas, **"Trustworthy Privacy Indicators: Grades, Labels, Certifications and Dashboards"**, Washington University Law Review, 96, 6, Feb 2019*

介绍了写一篇隐私政策的目标和标准。







