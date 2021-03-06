# 基于 Apache Flink 的工作流引擎系统

## 1 概述


1.1 什么是工作流引擎（Workflow Engine）


工作流（Workflow）就是“业务过程的部分或整体在计算机应用环境下的自动化”，它主要解决的是“使在多个参与者之间按照某种预定义的规则传递文档、信息或任务的过程自动进行，从而实现某个预期的业务目标，或者促使此目标的实现”。

自动化（Automation）是指机器设备、系统或过程（生产、管理过程）在没有人或较少人的直接参与下，按照人的要求，经过自动检测、信息处理、分析判断、操纵控制，实现预期的目标的过程。工作流是服务于自动化的目的的。

工作流引擎系统（Workflow Engine System）是一个软件系统，它完成工作量的定义和管理，并按照在系统中预先定义好的工作流逻辑进行工作流实例的执行。工作流引擎系统不是企业的业务系统，而是为企业的业务系统的运行提供了一个软件的支撑环境。

简单理解：数据（Data）通过一系列处理节点（Activity Node）的处理，最终达到信息加工的目的。这一系列处理节点联结起来的过程（Process）就是工作流，而提供工作流的软件系统就是工作流引擎。

在一个企业或组织里，流程（Process 或 Flow）定义的数目是有限的，而要加工的数据是近乎无限的。因此可以通过定义有限的流程系统（Workflow Schema）提供无限的任务处理（数据加工）能力。

可以把工作流看作是制造工厂（Manufactory）里的流水线（Assembly Line），数据相当于待组装加工的“零件（Machine Parts）”。这些“零件”从流水线的一端流入，经过一系列加工环节的处理最后形成加工好的产品（Artifact），在流水线的末端流出。

类似流水线上的每个加工的环节，工作流上的执行数据加工处理的节点称为活动（Activity 或 Execution），加工的内容称为任务（Task）。任务有属于一个批次的，也有不同批次的，用批次号（Serial No.）标识。

从工作流的角度看，任务就是流转在流程上的一组信息实体。


1.2 工作流定义


一个无环的有向图称做有向无环图（Directed Acyclic Graph），简称 DAG 图。有向无环图是描述一项工程或系统的进行过程的有效工具，除最简单的情况之外，几乎所有的工程（Project）都可分为若干个称作活动（Activity）的子工程，而这些子工程之间，通常受着一定条件的约束，如其中某些子工程的开始必须在另一些子工程完成之后。

因此用 DAG 来描述工作流的流程结构（Workflow Schema）是合适的。可扩展标记语言 XML（eXtensible Markup Language），是一种允许用户对自己的标记语言进行定义的源语言。由于 XML 的树形结构的特点，使其非常适合用于存取 DAG 结构数据，因此流程结构描述文件是一个 XML 格式的文件。

