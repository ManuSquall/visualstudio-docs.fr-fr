---
title: Project, élément (modèles Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ef09516237ad30a18f9790ddae40260d834af21
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139261"
---
# <a name="project-element-visual-studio-templates"></a>Project, élément (modèles Visual Studio)
Spécifie les fichiers ou répertoires à ajouter au projet.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`File`|Attribut requis.<br /><br /> Spécifie le nom du fichier projet dans le fichier .zip du modèle.|  
|`ReplaceParameters`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si le fichier projet comporte des valeurs de paramètre qui doivent être remplacés lorsqu’un projet est créé à partir du modèle. La valeur par défaut est `false`.|  
|`TargetFileName`|Attribut facultatif.<br /><br /> Spécifie le nom du fichier projet lorsqu’un projet est créé à partir du modèle.|  
|`IgnoreProjectParameter`|Attribut facultatif.<br /><br /> Spécifie si le projet doit être ajouté à la solution actuelle. Si la valeur de paramètre personnalisé, « $*myCustomParameter*$» existe dans le fichier de remplacement de paramètre, le projet est créé mais pas ajouté en tant que partie de la solution actuellement ouverte.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Dossier](../extensibility/folder-element-visual-studio-project-templates.md)|Élément facultatif.<br /><br /> Spécifie un dossier à ajouter au projet.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Élément facultatif.<br /><br /> Spécifie un fichier à ajouter à un projet.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Élément requis.|  
  
## <a name="remarks"></a>Notes  
 `Project` est un élément enfant facultatif de `TemplateContent`.  
  
 Le `Project` élément est utilisé pour spécifier un projet et par conséquent, est uniquement valide dans les modèles de projet.  
  
 `Project` les éléments peuvent avoir [dossier](../extensibility/folder-element-visual-studio-project-templates.md) éléments enfants ou [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) éléments enfants, mais pas une combinaison des deux `Folder` et `ProjectItem` les éléments enfants.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] renomme automatiquement le nom du fichier projet en fonction du nom entré par l’utilisateur dans le **nouveau projet** boîte de dialogue. Utilisez le `TargetFileName` si vous souhaitez fournir un autre nom de fichier pour les fichiers projet créés avec le modèle d’attribut.  
  
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
 [ProjectItem, élément (modèles de projet Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Élément Folder (modèles de projet Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)