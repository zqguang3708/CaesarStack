---
title: Ansys
date: 2022-04-05 18:03:00
---

# <mark>Ansys：有限元仿真</mark>

---

# 官网

# 高级操作

## 单机多核并行计算

### 查看本机配置

任务管理器-`性能`选项卡，里面可以看到插槽数量（CPU的个数）、内核（物理内核数，所有CPU的加起来）、逻辑处理器（超线程后的线程数）、内存大小和GPU型号。

Ansys选用的是物理核心数，为了保证其他程序的正确运行，一般比内核稍微少一点。例如，24核心48线程的服务器，一般Ansys设置为20。

### 配置方法

Workbench-Tools-Options：

- Appearance：Beta Options

- Solution Process：Default Execution Mode：Parallel

- Solution Process：Default Number of Processes：20

- Mechanical APDL：Database Memory：16384 M

- Mechanical APDL：Workspace Memory：32768 M

- Mechanical APDL：Processors：20

- Mechanical APDL：GPU Accelerator：NVIDIA

- Mechanical APDL：Number of GPUs per Machine：1

- Mechanical：Parallel Processing：Limit Number of Cores for Data Mapping and Post-Processing

- Mechanical：Maximum Number of Cores：20

Mechanical-Mesh：

- Advanced：Number of CPUs for Parallel Part Meshing：20

Mechanical-Solution：

- Solution：Number of Cores to Use(Beta)：20

# 工具配合

## 与SolidWorks配合

### Ansys与CAD集成设置

程序为：`CAD Configuration Manager 2022 R1`，位置一般在：

```cmd
C:\Program Files\ANSYS Inc\v221\commonfiles\CAD\bin\winx64\Ans.CadInt.CADConfigUtilityGUI.exe
```

> 其中v221代表版本号，选择对应的版本。

使用管理员身份运行。

在`CAD选择(CAD Selection)`选项卡，勾选`SolidWorks`，然后点选`Workbench关联接口(Workbench Associative Interface)`，在`CAD配置(CAD Configuration)`选项卡，选择`配置选定的CAD界面(Configure Selected CAD Interfaces)`。

如果提示Success，则代表配置成功，`退出(Exit)`即可。

经过以上方法配置后，就可以直接链接SolidWorks了。也可以直接导入SolidWorks的专属模型`.SLDPRT`和`.SLDASM`。

但是这种方法需要Ansys和SolidWorks的版本配合，有时候会出现一些斯巴达问题。

### 中间格式文件传递

SolidWorks转储为以下中间格式，然后Ansys读取这些格式的文件进行导入。

- .igs
  
  中文显示正常
  
  结构会被分割开

- .step
  
  中文名字会乱码
  
  结构完整

- .x_t
  
  中文显示正常
  
  结构完整
  
  **优先考虑**