---
title: "ProjectType, élément (modèles Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords: ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb177139491236cf518aba4e7f2effd213c1a469
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType, élément (modèles Visual Studio)
Catégorie du modèle de projet afin qu’il apparaisse sous le groupe spécifié dans le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.  
  
> [!WARNING]
>  Modèles de projet sont pris en charge pour C++ à partir de Visual Studio 2012. Elles ne sont pas prises en charge de C++ dans Visual Studio 2010 et les versions antérieures.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectType >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Cette valeur spécifie le type de projet que le modèle créera et doit contenir l’une des valeurs suivantes :  
  
-   `CSharp`: Spécifie que le modèle crée un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projet ou un élément.  
  
-   `VisualBasic`: Spécifie que le modèle crée un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projet ou un élément.  
  
-   `Web`: Spécifie que le modèle crée un projet Web ou un élément. Si le `ProjectType` élément contient cette valeur, le langage du projet ou de l’élément est défini dans le [ProjectSubType, élément (modèles Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Remarques  
 `ProjectType` est un élément enfant obligatoire de `TemplateData`.  
  
 La valeur de la `ProjectType` élément spécifie où le modèle se trouve dans le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue. Par exemple, un modèle avec un `ProjectType` valeur `CSharp` apparaît sous le **Visual C#** nœud dans le **nouveau projet** boîte de dialogue.  
  
 Un sous-type de modèle peut être spécifié à l’aide de la [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) élément.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Élément ProjectSubType (modèles Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)