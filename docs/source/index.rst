欢迎来到 AICodingAssistant 的文档!
^^^^^^^^

.. **Lumache** (/lu'make/) is a Python library for cooks and food lovers
.. that creates recipes mixing random ingredients.
.. It pulls data from the `Open Food Facts database <https://world.openfoodfacts.org/>`_
.. and offers a *simple* and *intuitive* API.

.. Check out the :doc:`usage` section for further information, including
.. how to :ref:`installation` the project.


.. note::

   本项目是一个基于GPT-3的编码助手，目前支持根据编码框架对MOOC论坛中话题下的回帖数据进行编码。  
   当前项目还在开发中，以后会提供更多的功能，敬请期待。  

【目标用户】
^^^^^^^^

- **研究者** 
  本项目可以帮助研究者快速对论坛中的回帖数据进行编码，提高编码效率，减少编码错误。


【操作流程图】
^^^^^^^^

.. image:: ./_static/images/structure.jpg
   :alt: Structure
   :align: center

【项目目录结构】
^^^^^^^^

root
   |_ api_key.txt

   |_ coding_scheme
      |_ coding_scheme.csv
   |_ input
      |_ reply.csv

      |_ topic.csv
   |_ output
      |_ coding_error.txt

      |_ coding_result.txt

      |_ coding_result_current_date.csv
   |_ AICodingAssistant.exe

【使用说明】
^^^^^^^^

「编码前的准备工作」
^^^^^^^^

1 **在开始编码之前，你需要准备以下数据**: 

1.1 **API_key，放在api_key.txt文件中**: 

- 申请API_key，用于调用编码接口。

- 申请地址：https://api2d.com/

- API_key查看地址：https://api2d.com/forward_key/list

- API_key示例：fk203018-8OyNua...

- 复制API_key到剪贴板，然后将其粘贴到api_key.txt文件中。

1.2 **输入数据，放在input文件夹下的topic.csv和reply.csv中**:

.. csv-table:: 回帖数据：reply.csv
   :align: left
   :header: "字段", "类型", "描述"
   :widths: 15, 10, 30

   "index", int, "待编码文本的唯一标识符，是回帖ID"
   "user_id", int, "回帖的用户ID"
   "user_name", str, "回帖的用户昵称"
   "reply_content", str, "回帖内容"
   "topic_id", int, "回帖的话题ID"
   "reply_id", int, "回帖ID"
   "to_reply_id", int, "回帖的父级回帖ID"
   "reason", str, "编码理由，这一列可以空着"

.. csv-table:: 话题数据：topic.csv
   :align: left
   :header: "字段", "类型", "描述"
   :widths: 15, 10, 30

   "topic_id", int, "话题ID"
   "topic_title", str, "话题标题"
   "topic_content", str, "话题内容，一半是话题的详细描述，这里可以空着"

1.3 **编码规则，放在coding_scheme文件夹下的coding_scheme.csv中**:

.. csv-table:: 编码规则：coding_scheme.csv
   :align: left
   :header: "字段", "类型", "描述"
   :widths: 15, 10, 30

   "category", str, "编码分类"
   "code", str, "编码指标代码"
   "indicators", str, "编码指标"
   "example", str, "指标的示例（这一列可以不要）"


「编码过程中的错误处理」
^^^^^^^^

2 **编码过程中，GPT的回复可能会出现错误，错误信息和错误处理方式如下**: 

2.1 **错误信息处理方式**:

- 查看output文件夹下面coding_error.txt文件，如果有编码错误，需要手动处理。

- 复制coding_error.txt中的每一行数据，到coding_result.txt文件中搜索，找到对应的数据，然后手动处理将其更正为标准数据格式。

- 处理完毕后，删除coding_error.txt文件或删除文件中的所有数据。

- ⚠️推荐使用vs code 打开coding_result.txt文件，它可以高亮显示大部分错误。

标准的数据格式如下:

.. code-block:: console

   {"reply_id":"557092","tags":["E-3"],"reason":["回帖中提到了对教师备课的重要作用，这符合编码表中的建议和思考（E-3），即对建议进行考虑"]}


2.2 **常见的错误有：**

- 末尾缺少一个“}”，请补充。

- reason中有英文的引号，请在英文引号前添加转义符“\”。

- 末尾多了一个逗号，请删除。

- 一行数据包含了多个结果，如{...},{...}，请将其拆分为多行。

- 一样数据包含多个结果，但其中一个结果是错误的，如{...},reply_id...}，显然，reply_id前缺少一个“{”，请将错误的结果补全并拆分。


「编码后的结果」
^^^^^^^^

.. csv-table:: 编码结果：coding_result_current_date.csv中
   :align: left
   :header: "字段", "类型", "描述"
   :widths: 15, 10, 30

   "user_id", int, "回帖的用户ID"
   "user_name", str, "回帖的用户昵称"
   "reply_content", str, "回帖内容"
   "topic_id", int, "回帖的话题ID"
   "reply_id", int, "回帖ID"
   "to_reply_id", int, "回帖的父级回帖ID"
   "reason", str, "编码理由"
   "code_indicator 1", int, "0或1，1表示这一条回帖中包含了编码指标1"
   "code_indicator 2", int, "0或1，1表示这一条回帖中包含了编码指标2"
   "...", int, "0或1，1表示这一条回帖中包含了编码指标..."
   "code_indicator n", int, "0或1，1表示这一条回帖中包含了编码指标n"


【联系方式】
^^^^^^^^
暂时写这么多吧，应该够用了，有问题可以联系我，谢谢！

- **微信：** etshaw8888

- **微信公众号：** EdTech肖建军

- **邮箱：** et_shaw@126.com

- **地址：** 北京师范大学科技楼C区1005A室

.. image:: ./_static/images/shaw.png
   :alt: Structure
   :align: left
   :width: 200
   :height: 100

【下载地址】
^^^^^^^^

- **师大云盘**：https://pan.bnu.edu.cn/l/31Xy5N