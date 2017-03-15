---
title: "ProvideDefaultName, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName"
helpviewer_keywords: 
  - "ProvideDefaultName (élément de modèles de projet Visual Studio)"
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# ProvideDefaultName, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie si le système de projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] générera un nom par défaut pour le modèle dans la boîte de dialogue **Ajouter un nouvel élément** ou **Nouveau projet**.  
  
## Syntaxe  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 Le texte doit avoir la valeur `true` ou `false`, qui indique si oui ou non il y aura génération de nom de modèle par défaut dans la boîte de dialogue **Ajouter un nouvel élément** ou **Nouveau projet**.  
  
## Notes  
 `ProvideDefaultName` est un élément facultatif.  La valeur par défaut est `true`.  
  
 Si l'élément `ProvideDefaultName` a la valeur `false`, les zones **Nom** des boîtes de dialogue **Ajouter un nouvel élément** et **Nouveau projet** contiennent la valeur `<Entrer_nom>`.  
  
 Utilisez l'élément [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) pour spécifier le nom par défaut du projet ou de l'élément dans les boîtes de dialogue **Ajouter un nouvel élément** et **Nouveau projet**.  
  
## Exemple  
 L'exemple de code suivant donne à l'élément `ProvideDefaultName` la valeur `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)