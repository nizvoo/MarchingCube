# MarchingCube
迷之Marching Cube算法，一开始以为只能用于基于CT的网格重构，结果发现拓展下还能作为很多数据形式的网格重构算法=。=
其实MC也可以有很多变种啦，但是这里大致演示一下过程:
-输入体素模型：这些体素模型就直接从预设好的外部文件读取，一共有一百来个文件，每个文件是一层体素（算是强行从CT切片里面提取的数据）。对于每一层，里面直接就是0x00和0xff的bytes，一个byte对应一个体素，512x512的二值化矩阵，0xff就表示当前位置有体素
-重构：使用MarchingCube算法重构出三角形网格，但是对于每一个cube，棱上生成的顶点先只考虑在棱的中点上(也就是(v_1+v_2)*0.5f)，所以如果不做体素降采样/滤波的话，生成的网格有锯齿是不能避免的（毕竟原始数据都是二值化的）
-输出STL：顺手输出.stl模型文件呗，可以拿其他软件查看重建结果
