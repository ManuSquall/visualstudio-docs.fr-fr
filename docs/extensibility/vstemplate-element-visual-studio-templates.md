---
title: VSTemplate, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 899a8ac07d8e5b578c7619cceff173608b15792a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947021"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate, élément (modèles Visual Studio)
Contient toutes les métadonnées sur le modèle de projet, un modèle d’élément ou un starter kit.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
| Attribut | Description |
|-----------| - |
| `Type` | Identifie le modèle comme un modèle de projet ou un modèle d’élément. Cet attribut peut avoir une valeur de `Project` ou `Item`. |
| `Version` | Spécifie un numéro de version pour le modèle. Modèles dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] et [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ont un `Version` valeur d’attribut `3.0.0`. |
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie les données qui définit la catégorie du modèle et comment il s’affiche dans le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Élément requis.<br /><br /> Spécifie le contenu du modèle.|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Élément facultatif.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Élément facultatif.|  
  
### <a name="parent-elements"></a>Éléments parents  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 Le `VSTemplate` élément est l’élément racine de *.vstemplate* fichiers.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application.  
  
```xml  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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
 [Référence de schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)