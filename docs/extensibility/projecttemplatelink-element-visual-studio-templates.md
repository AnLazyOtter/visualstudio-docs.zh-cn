---
title: ProjectTemplateLink 元素 （Visual Studio 模板） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10ebc56e03a6582ab37126097db5f79ed9c5f2a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink 元素（Visual Studio 模板）
指定多项目模板中一个项目的 .vstemplate 文件的路径。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<ProjectTemplateLink >  
-或-  
\<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<SolutionFolder >  
 \<ProjectTemplateLink >  
  
## <a name="syntax"></a>语法  
  
```  
<ProjectTemplateLink ProjectName="Name">  
    PathToTemplateFile  
</ProjectTemplateLink>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下各部分描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`ProjectName`|可选特性。<br /><br /> 指定多项目模板中每一个项目的名称。 **新项目**对话框中不能向单个项目分配名称。|  
|`CopyParameters`|使主要组模板中的所有变量可复制到每个链接模板。<br /><br /> 链接模板中的参数具有前缀 `"$ext_*$"`。 例如，如果在父组模板参数`$projectname$`具有值**exampleproject1 则轮到**，当链接的模板获取其启用可执行，它将获取参数`$ext_projectname$`，这是一份`$projectname$`父组模板中的参数。<br /><br /> 这使链接模板能够共享一些只能在父组模板中方便地创建的公用参数。<br /><br /> 此特性为可选特性，未包含此特性时，它将自动默认为 `false`。<br /><br /> 在 Visual Studio 2013 Update 2 中引入。 若要引用正确的产品版本，请参阅[Visual Studio 2013 SDK Update 2 中引用程序集提供](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb)。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|指定多项目模板的组织和内容。|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|对多项目模板中的项目进行分组。|  
  
## <a name="text-value"></a>文本值  
 需要一个文本值。  
  
 此文本指定模板的 .vstemplate 文件的路径。  
  
## <a name="remarks"></a>备注  
 多项目模板用作两个或多个项目的容器。 `ProjectTemplateLink` 元素用于指定模板中一个项目的 .vstemplate 文件的位置。 对于多项目模板中的每个项目，此模板的 .vstemplate 文件中都含有一个对应的 `ProjectTemplateLink` 元素。 有关多项目模板的详细信息，请参阅[如何： 创建多项目模板](../ide/how-to-create-multi-project-templates.md)。  
  
## <a name="example"></a>示例  
 此示例演示一个简单的多项目 .vstemplate 根文件。 在此示例中，模板包含两个项目：`My Windows Application` 和 `My Class Library`。 `ProjectName` 元素的 `ProjectTemplateLink` 特性可为 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置要分配给此项目的名称。 如果不存在 `ProjectName` 特性，则会使用 .vstemplate 文件的名称作为项目名称。  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)   
 [如何：创建多项目模板](../ide/how-to-create-multi-project-templates.md)