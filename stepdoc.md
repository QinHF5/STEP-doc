# 1 什么是STEP文件？
STEP：产品模型数据交换标准（STandard Exchange of Product data model），1988年ISO制定的描述整个产品生命周期内产品信息的标准，它提供了一种不依赖具体系统的中性机制，旨在实现产品数据的交换和共享。这种描述的性质使得它不仅适合于交换文件，也适合于作为执行和分享产品数据库和存档的基础。发达国家已经把STEP标准推向了工业应用。它的应用显著降低了产品生命周期内的信息交换成本，提高了产品研发效率，成为制造业进行国际合作、参与国际竞争的重要基础标准，是保持企业竞争力的重要工具。
# 2 STEP中性文件
上文提到，STEP标准提供了不同的产品数据交换实现方法，用于产品数据的可供选择的实现方法有：中性文件、数据库、数据存取和知识库。
其中最常用的一种是文件交换(Fil e exchange)。它为STEP应用协议的产品数据提供一种可读写的文件交换描述方法，即一种清楚易懂的正文编码
形式(C1ear text encoding)。
## 2.1 STEP 中性文件的基本概念和设定
中性文件交换结构由无二义性的、上下文无关的，又便于软件解释的语法来描述。这种语法用WSN(Wirth Syntax Notation)来表达。用交换结构描述的产品数据形式是通过EXPRESS语言变换而来。这种结构独立于任何专门的应用。
## 2.2 交换文件的总体结构
交换结构(exchange structure)是用易懂的正文编码书写的顺序文件。它有两部分组成：标题段(Header section)和数据段(Data section)。

每一个交换结构中都有三个标题变量：文件描述(fil e descriptiOn)，文件名称(file—name)和文件模式(file—schema)。在这三个标题变量之后，可以设置用户自己定义的标题元素，其出现顺序没有严格规定。标题元素定义句法也用WSN。

数据段包括由交换结构传输的数据产品。数据段包含的元素实例与标题段中的EXPRESS模式相一致，此模式控制交换结构。数据段以专门标记“DATA”开始，而以“ENDSEC”结束。

## 2.3 STEP 中性文件格式
举个例子：
> ISO-10303-21(指明中交换文件的是吸纳方法/正文编码形式)
> 
> HEADER;
> 
> ....（FILE—DESCRIPTION、FILE—NAME和
FILE—SCHEMA）
> 
> ENDSEC;
> 
> DATA;
> 
> ...
> 
> ENDSEC;
> 
> END-ISO-10303-21;

### 2.3.1 STEP文件中的几何描述
STEP几何模式实体定义的拓扑元素主要包括顶点(VERTEX)、边(EDGE)、路径(PATH)、环(LOO多)、面(FACE)等，这些实例中又包含自己的子实例的定义。

从STEP中性交换文件结构分析可得出，STEP中型交换文件的语句间
存在明显的层次关系，这种分层的组合关系是一个典型的拓扑结构。而且，STEP文件通过相应的实例关键词进行组合，成为一组语句来实现特定的功能，再由多组语句组合来表达一个完整的产品数据模型。例如，通过下面的几条语句中实体闻的拓扑组合。可以完成球面信息的表达功能。
>#30=CARTESIAN—POINT(”，(0．，0．，0．))：／+定义点的三维坐标{／
>
>#3i=DIRECTION(”．(6．123031769I i 189E-017，0．，1．))：
>
>#32=DIRECTION(”，(1．，0．，0．))：／％定义点的法向矢量十／
>
>#33=AXIS2一PLACEMENT一3D(”，#30，#3l，#32)：／}确定点及其所在面}／
>
>#34=SPHERICAL—SURFACE(“，#33，5．)：／丰产生球面的实例丰／

上面STEP文件数据节中，提供了球体数据信息的语句间的关系.

```mermaid
    graph LR
    #37-->#36
    #36-->#35
    #35-->#34
    #34-->#33
    #33-->#31
    #33-->#32
    #35-->#29
    #29-->#28
    #28-->#27
    #27-->#26
```
