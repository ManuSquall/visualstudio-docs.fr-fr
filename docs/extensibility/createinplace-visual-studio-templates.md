---
title: "CreateInPlace (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace"
helpviewer_keywords: 
  - "<CreateInPlace> (élément de modèles Visual Studio)"
  - "CreateInPlace (élément de modèles Visual Studio)"
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# CreateInPlace (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie s'il faut créer le projet et effectuer le remplacement de paramètre à l'emplacement spécifié ou effectuer ce remplacement dans un emplacement temporaire, puis enregistrer le projet à l'emplacement spécifié.  
  
## Syntaxe  
  
```  
<CreateInPlace> true/false </CreateInPlace>  
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
 Une valeur texte est requise.  
  
 Ce texte doit être `true` ou `false`.  S'il a la valeur `true`, le projet est créé et le remplacement de paramètre est effectué à l'emplacement spécifié dans la boîte de dialogue **Nouveau projet**.  S'il a la valeur `false`, le remplacement de paramètre est effectué dans un emplacement temporaire, puis le projet est copié à l'emplacement spécifié.  
  
## Notes  
 `CreateInPlace` est un élément facultatif.  La valeur par défaut est `true`.  
  
## Exemple  
 L'exemple suivant illustre les métadonnées d'un modèle [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <CreateInPlace>false</CreateInPlace>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)