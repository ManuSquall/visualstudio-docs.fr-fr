---
title: "Description, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Description (élément de modèles de projet Visual Studio)"
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Description, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie la description du modèle tel qu'elle apparaît dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.  
  
## Syntaxe  
  
```  
<Description>  
    Template Description  
</Description>  
```  
  
```  
<Description Package="{PackageID}" ID="ResourceID" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Package`|Attribut facultatif, pour les scénarios complexes.<br /><br /> GUID qui spécifie l'ID du package Visual Studio.|  
|`ID`|Attribut facultatif, pour les scénarios complexes.<br /><br /> Spécifie l'ID de ressource Visual Studio.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle dans une catégorie et définit la façon dont il s'affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.|  
  
## Valeur texte  
 Une valeur texte est requise, sauf en cas d'utilisation des attributs `Package` et `ID`.  
  
 Le texte fournit une description du modèle.  
  
## Notes  
 L'élément `Description` est un enfant obligatoire de l'élément `TemplateData`.  
  
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