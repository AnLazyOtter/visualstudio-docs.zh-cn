---
title: 快速入门 - 使用模板创建 Python 项目
description: 在此快速入门教程中，使用基本 Flask 应用的内置模板创建适合 Python 的 Visual Studio 项目。
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: dca1e37a0cde89a2a531d3fceea4337bb9e348dd
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>快速入门：从 Visual Studio 中的模板创建 Python 项目

[在 Visual Studio 2017 中安装 Python 支持](installing-python-support-in-visual-studio.md)后，就可以使用各种模板轻松创建新的 Python 项目。 在此快速入门教程中，使用模板创建简单的 Flask 应用。 生成的项目与按照[快速入门 - 通过 Flask 创建 Web 应用](../ide/quickstart-python.md)手动创建的项目相似。

1. 启动 Visual Studio 2017。

1. 在顶部菜单栏中，依次选择“文件”、“新建”和“项目...”，然后在“新建项目”对话框中搜索“空白 Flask”，在中间列表中选择“空白 Flask Web 项目”模板，指定项目的名称，最后选择“确定”：

    ![使用“空白 Flask Web 项目”模板新建项目](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio 中显示对话框，提示“此项目需要外部包。” 显示此对话框的原因是模板包括指定 Flask 依赖项的 `requirements.txt` 文件。 Visual Studio 可自动安装包，且让你能够在虚拟环境中安装这些包。 安装到全局环境时建议使用虚拟环境，因此选择“安装到虚拟环境”继续操作。

    ![将 Flask 安装到虚拟环境](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio 随即显示“添加虚拟环境”对话框。 接受默认设置并选择“创建”，然后同意任意升级请求。

    > [!Tip]
    > 开始一个项目时，强烈建议立即创建虚拟环境，因为大多数 Visual Studio 模板均有此项提示。 在你添加和删除库时，虚拟环境随之保证项目的确切需求。 然后，可轻松生成 `requirements.txt` 文件。在其他开发计算机上重新安装这些依赖项时使用此文件（因为此时使用源代码管理功能集），将项目部署到生产服务器时也使用此文件。 有关虚拟环境及其优势的详细信息，请参阅[使用虚拟环境](../python/selecting-a-python-environment-for-a-project.md#using-virtual-environments)和[使用 requirements.txt 管理所需的包](../python/managing-required-packages-with-requirements-txt.md)。

1. Visual Studio 创建该环境后，在解决方案资源管理器中查看是否已具备 `app.py` 和 `requirements.txt`。 打开 `app.py`，可看到模板提供了类似[快速入门 - 使用 Flask 创建 Web 应用](../ide/quickstart-python.md)中的代码，还增添了两个部分。

    第一个部分是行 `wsgi_app = app.wsgi_app`，可在将应用部署到 Web 主机时使用它。

    第二个部分是启动代码，它可用于通过环境变量设置主机和端口，而不是硬编码它们。 此类代码可让你轻松控制开发和生产计算机上的配置，而无需更改代码：

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. 依次选择“调试”和“开始执行(不调试)”，以运行应用并打开指向`localhost:5555` 的浏览器。

**问：Visual Studio 还提供哪些 Python 模板？**

**答**：在安装了 Python 工作负载的情况下，Visual Studio 提供多种项目模板，其中包括用于 [Flask、Bottle 和 Django Web 框架](../python/python-web-application-project-templates.md)、Azure 云服务以及不同机器学习方案的模板，甚至还有一个模板用于根据带 Python 应用的现有文件夹结构创建项目。 要访问模板，可选择“Python”语言节点及其子节点，再依次单击“文件”、“新建”和“项目...”。

Visual Studio 还提供各种文件或项模板，用于快速创建 Python 类、Python 包、Python 单元测试、`web.config` 文件等内容。 如果打开了 Python 项目，可依次单击“项目”和“添加新项”菜单命令来访问项模板。 请参阅[项模板](python-item-templates.md)引用。

开始项目或创建文件时，使用模板可节省大量时间，这还是一个了解不同应用类型和代码结构的好方法。 最好先花几分钟基于不同模板创建项目和项，熟悉模板的功能。

**问：我还能使用 Cookiecutter 模板吗？**

**答**：能！ 事实上，Visual Studio 提供与 Cookiecutter 的直接集成（详情请参见[快速入门：使用 Cookiecutter 模板创建项目](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md)）。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [教程：在 Visual Studio 中使用 Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>请参阅

- [手动标识现有的 Python 解释器](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)。
- [在 Visual Studio 2015 及更早版本中安装 Python 支持](installing-python-support-in-visual-studio.md)。
- [安装位置](installing-python-support-in-visual-studio.md#install-locations)。
