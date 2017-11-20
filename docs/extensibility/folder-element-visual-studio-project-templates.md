---
title: "Folder, élément (modèles de projet Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords: Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 677b705015b2b12ee484db7595d6cfd919ad61d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder, élément (modèles de projet Visual Studio)
Spécifie un dossier qui sera ajouté au projet.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<Dossier >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Attribut requis.<br /><br /> Le nom du dossier du projet.|  
|`TargetFolderName`|Attribut facultatif.<br /><br /> Spécifie le nom à donner au dossier lorsqu’un projet est créé à partir du modèle. Cet attribut est utile pour l’utilisation de remplacement de paramètre pour créer un nom de dossier ou nom d’un dossier avec une chaîne internationale qui ne peut pas être utilisée directement dans le fichier .zip.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`Folder`|Spécifie un dossier à ajouter au projet. `Folder`les éléments peuvent contenir des enfants `Folder` éléments.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Spécifie un fichier à ajouter au projet.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Élément enfant facultatif de [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Remarques  
 `Folder`est un enfant facultatif de `Project`.  
  
 Vous pouvez utiliser une des méthodes suivantes pour organiser les éléments de projet dans des dossiers dans un modèle :  
  
-   Inclure les dossiers dans le fichier .zip du modèle et les ajouter au projet dans le fichier .vstemplate en spécifiant le chemin d’accès au fichier dans le `ProjectItem` éléments, sans aucune `Folder` éléments. Il s’agit de la méthode recommandée. Exemple :  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Inclure les dossiers dans le fichier .zip du modèle et les ajouter au projet dans le fichier .vstemplate avec `Folder` éléments. Exemple :  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   N’incluez pas de dossiers dans le fichier .zip du modèle, mais ajouter des dossiers à l’aide de la `TargetFileName` attribut de la `ProjectItem` élément. Exemple :  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Élément ProjectItem (modèles d'élément Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)