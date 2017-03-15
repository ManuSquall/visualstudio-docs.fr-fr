---
title: "ProjectSubType, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType"
helpviewer_keywords: 
  - "<ProjectSubType> (élément de modèles Visual Studio)"
  - "ProjectSubType (élément de modèles Visual Studio)"
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# ProjectSubType, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Classe le modèle dans une sous\-catégorie de la valeur spécifiée dans l'élément `ProjectType`.  
  
## Syntaxe  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle dans une catégorie et définit la façon dont il s'affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
 Cette valeur spécifie la sous\-catégorie du modèle.  
  
## Notes  
 `ProjectSubType` est un élément enfant facultatif de `TemplateData`.  
  
 L'élément `ProjectSubType` fournit une sous\-catégorie à l'élément [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md).  Cette valeur peut inclure :  
  
-   `SmartDevice-NETCFv1` Spécifie que le modèle concerne la version 1.0 du [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  
  
-   `SmartDevice-NETCFv2` : Spécifie que le modèle concerne la version 2.0 du [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  
  
 Si un modèle contient un élément `ProjectType` dont la valeur est `Web`, l'élément `ProjectSubType` spécifie le langage de programmation du modèle.  Cet élément peut avoir les valeurs suivantes :  
  
-   `CSharp` Spécifie que le modèle crée un projet ou élément Web [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
-   `VisualBasic` Spécifie que le modèle crée un projet ou élément Web [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Exemple  
 L'exemple suivant affiche les métadonnées d'un modèle de projet pour une application [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] concernant la version 2.0 du [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
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
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [ProjectType, élément \(modèles Visual Studio\)](../extensibility/projecttype-element-visual-studio-templates.md)