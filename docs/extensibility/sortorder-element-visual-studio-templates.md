---
title: "SortOrder, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder"
helpviewer_keywords: 
  - "<SortOrder> (élément de modèles Visual Studio)"
  - "SortOrder (élément de modèles Visual Studio)"
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# SortOrder, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie une valeur utilisée pour organiser la façon dont le modèle, parmi d'autres modèles de la même catégorie, apparaît dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.  
  
## Syntaxe  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 `integer` qui représente l'ordre de tri.  
  
## Notes  
 `SortOrder` est un élément facultatif.  La valeur par défaut est 100 et toutes les valeurs doivent être des multiples de 10.  
  
 L'élément `SortOrder` est ignoré dans le cas de modèles créés par utilisateur.  Tous les modèles créés par l'utilisateur sont triés selon l'ordre alphabétique.  
  
 Les modèles portant les valeurs les plus basses dans l'ordre de tri apparaissent dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** avant les modèles portant les valeurs les plus élevées.  
  
## Exemple  
 L'exemple suivant illustre les métadonnées d'un modèle de classe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] standard.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Dans cet exemple, l'élément `SortOrder` est relativement haut.  D'autres modèles d'élément [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] auront probablement une valeur `SortOrder` inférieure à `290` et apparaîtront avant ce modèle dans la boîte de dialogue **Nouvel élément**.  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)