---
title: "SolutionFolder, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder"
helpviewer_keywords: 
  - "<SolutionFolder> (élément de modèles Visual Studio)"
  - "SolutionFolder (élément de modèles Visual Studio)"
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SolutionFolder, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Groupe des projets dans des modèles à plusieurs projets.  
  
## Syntaxe  
  
```  
<SolutionFolder Name="DirectoryName">  
    ...  
</SolutionFolder>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Attribut requis.<br /><br /> Nom du dossier de solution.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie le chemin d'accès au fichier .vstemplate d'un projet dans un modèle à plusieurs projets.|  
|`SolutionFolder`|Élément facultatif.<br /><br /> Groupe des projets dans des modèles à plusieurs projets.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Spécifie l'organisation et le contenu de modèles à plusieurs projets.|  
|`SolutionFolder`|Groupe des projets dans des modèles à plusieurs projets.|  
  
## Notes  
 Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets.  L'élément `SolutionFolder` permet d'organiser les projets du modèle par groupes.  Les dossiers spécifiés par les éléments `SolutionFolder` sont créés comme dossiers de solution du projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pour plus d'informations sur les modèles à plusieurs projets, consultez [Comment : créer des modèles à plusieurs projets](../ide/how-to-create-multi-project-templates.md).  
  
## Exemple  
 Cet exemple utilise l'élément `SolutionFolder` pour répartir le modèle à plusieurs projets en deux groupes, `Math Classes` et `Graphics Classes`.  Le modèle contient quatre projets, dont deux sont placés dans chaque dossier de solution.  
  
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
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Comment : créer des modèles à plusieurs projets](../ide/how-to-create-multi-project-templates.md)