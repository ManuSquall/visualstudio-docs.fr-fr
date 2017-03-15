---
title: "&#201;l&#233;ment RequiredFrameworkVersion (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<RequiredFrameworkVersion> (modèles Visual Studio)"
  - "RequiredFrameworkVersion (modèles Visual Studio)"
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# &#201;l&#233;ment RequiredFrameworkVersion (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie la version minimale de .NET Framework qui est requise par la hiérarchie de schéma du modèle.  
  
## Syntaxe  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
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
  
 Le texte doit avoir le numéro de version minimal de .NET Framework qui soit requise pour le modèle.  
  
## Notes  
 `RequiredFrameworkVersion` est un élément facultatif.  Utilisez cet élément si le modèle ne prend en charge qu'une version minimale spécifique du .NET Framework et d'éventuelles versions ultérieures.  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Cibler une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)