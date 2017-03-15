---
title: "NumberOfParentCategoriesToRollUp (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp"
helpviewer_keywords: 
  - "<NumberOfParentCategoriesToRollUp> (élément de modèles Visual Studio)"
  - "NumberOfParentCategoriesToRollUp (élément de modèles Visual Studio)"
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# NumberOfParentCategoriesToRollUp (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie le nombre de catégories parentes qui afficheront le modèle dans la boîte de dialogue **Nouveau projet**.  
  
## Syntaxe  
  
```  
<NumberOfParentCategoriesToRollUp>  
    1  
</NumberOfParentCategoriesToRollUp>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classe le modèle dans une catégorie et définit la façon dont il s'affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.|  
  
## Valeur texte  
 Une valeur `integer` est obligatoire.  
  
 Spécifie le nombre de catégories parentes qui afficheront le modèle dans la boîte de dialogue **Nouveau projet**.  
  
## Notes  
 `NumberOfParentCategoriesToRollUp` est un élément facultatif.  
  
## Exemple  
 Cet exemple illustre les métadonnées d'une application Windows [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  Si un modèle avec ces métadonnées est placé deux niveaux de dossiers en dessous du nœud [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] de niveau supérieur, le modèle s'affichera dans le nœud de niveau supérieur dans la boîte de dialogue **Nouveau projet**.  Si le `NumberOfParentCategoriesToRollUp` n'est pas défini, le modèle apparaît seulement dans le nœud où il se trouve physiquement.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>  
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