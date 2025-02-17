.. _cn_api_tensor_search_nonzero:

nonzero
-------------------------------

.. py:function:: paddle.nonzero(x, as_tuple=False)




该OP返回输入 ``x`` 中非零元素的坐标。如果输入 ``x`` 有 ``n`` 维，共包含 ``z`` 个非零元素，当 ``as_tuple = False`` 时，
返回结果是一个 ``shape`` 等于 ``[z x n]`` 的 ``Tensor`` , 第 ``i`` 行代表输入中第 ``i`` 个非零元素的坐标；当 ``as_tuple = True`` 时，
返回结果是由 ``n`` 个大小为 ``z`` 的 ``1-D Tensor`` 构成的元组，第 ``i`` 个 ``1-D Tensor`` 记录输入的非零元素在第 ``i`` 维的坐标。
        
参数
:::::::::

    - **x** （Tensor）– 输入张量。
    - **as_tuple** (bool, optinal) - 返回格式。是否以 ``1-D Tensor`` 构成的元组格式返回。

返回
:::::::::
    - **Tensor or tuple(1-D Tensor)**，数据类型为 **INT64** 。
     
代码示例
:::::::::

.. code-block:: python

        import paddle

        x1 = paddle.to_tensor([[1.0, 0.0, 0.0],
                                [0.0, 2.0, 0.0],
                                [0.0, 0.0, 3.0]])
        x2 = paddle.to_tensor([0.0, 1.0, 0.0, 3.0])
        out_z1 = paddle.nonzero(x1)
        print(out_z1)
        #[[0 0]
        # [1 1]
        # [2 2]]
        out_z1_tuple = paddle.nonzero(x1, as_tuple=True)
        for out in out_z1_tuple:
            print(out)
        #[[0]
        # [1]
        # [2]]
        #[[0]
        # [1]
        # [2]]
        out_z2 = paddle.nonzero(x2)
        print(out_z2)
        #[[1]
        # [3]]
        out_z2_tuple = paddle.nonzero(x2, as_tuple=True)
        for out in out_z2_tuple:
            print(out)
        #[[1]
        # [3]]         


