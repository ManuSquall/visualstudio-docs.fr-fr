---
title: "TemplateContent, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent"
helpviewer_keywords: 
  - "TemplateContent (élément de modèles de projet Visual Studio)"
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# TemplateContent, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie le contenu du modèle.  
  
## Syntaxe  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Spécifie s'il faut générer la solution lorsqu'un projet est créé à partir du modèle.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie l'organisation et le contenu de modèles à plusieurs projets.|  
|[Projet](../extensibility/project-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie les fichiers ou répertoires à ajouter au projet.|  
|[Références](../extensibility/references-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie les références d'assembly requises pour un modèle d'élément.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Élément facultatif.<br /><br /> Spécifie un fichier contenu dans le modèle.|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Spécifie les paramètres personnalisés qui doivent être utilisés lorsqu'un projet ou un élément est créé à partir de le modèle.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Élément requis.<br /><br /> Contient toutes les métadonnées du modèle de projet ou d'élément ou du Starter Kit.|  
  
## Notes  
 `TemplateContent` est un élément obligatoire.  
  
## Exemple  
 L'exemple suivant affiche les métadonnées d'un modèle de projet pour une application [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
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
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)