# 配置数字翻牌器组件的回调ID {#concept_m2n_fy3_52b .concept}

在 DataV 中，回调ID是指某个组件在响应用户操作或者自动触发更新时向别的组件传递的参数，这个参数可以在别的组件中用于数据查询时的动态变量。

## 操作步骤 {#section_vqv_1kk_52b .section}

1.  选择数字翻牌器组件，单击编辑器右侧的**交互**页签。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17483/15347468639296_zh-CN.png)

    **说明：** 最新版本的 DataV 提供了一个回调ID的独立编辑区块，方便您清晰快速地使用回调ID功能。

2.  勾选**数字变化响应事件**右侧的**启用**。
3.  修改**绑定到变量**中的变量名称，如下图所示，将 value 修改为 income。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17483/15347468639297_zh-CN.png)

    这时在别的组件使用该变量时，就可以使用 income 来取得这个参数。

    **说明：** 使用这一特性，您可以给不同的组件设置不一样的变量名称，达到区分使用不同参数的目的。

4.  在数据源中使用`:变量名`（如`:income`），使用您已经配置的变量。示例如下：

    -   SQL:

        ```
        select :income as value
        select A from table where income = :income
        ```

    -   API:

        ```
        http://api.test?income=:income&id=:myid
        ```

    **说明：** 

    -   如果您的**数据源类型**为**静态数据**或者**CSV 文件**，则不支持回调ID的使用。
    -   DataV 提供了回调参数自动补全功能。在配置数据源时，只要键入`:`，编辑器将提示当前屏幕下所有已经配置过的变量名称。您可以使用上下键选择某个变量名称，完成后按 Enter 键确定。当屏幕中有大量交互组件的时候，这个功能可以帮助您方便快速地使用回调ID。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17483/15347468639300_zh-CN.png)


## 高级功能 {#section_id3_bcz_q2b .section}

-   **设置自定义字段**

    1.  单击数字翻牌器组件的数据页签。
    2.  在数据源中设置一个 id 字段，值为 123。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17483/15347468639298_zh-CN.png)

    3.  单击交互页签，返回组件的交互配置面板。
    4.  单击**新建一个字段**。
    5.  在**字段**列输入id，在**绑定到变量**列输入您要设置的变量名称。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17483/15347468639299_zh-CN.png)

        **说明：** 只有在同时填写了**字段**和**绑定到变量**后，这个变量才会生效。

-   **设置回调ID的默认值**

    您可以通过在url中设置请求参数的形式来设置回调ID的默认值，示例如下。

    ```
    http://datav.aliyun.com/screen/000000?myid=123
    注释：000000表示屏幕id
    ```

    通过这个url访问大屏时，在页面打开的时候，回调ID的 myid 的值已经设置为 123 了。

    多个回调ID之间使用“&”符号连接，如下的示例中同时设置了回调ID的 myid 和 income 的默认值。

    ```
    http://datav.aliyun.com/screen/000000?myid=123&income=1000
    注释：000000表示屏幕id
    ```


