---
title: "&#201;l&#233;ment CustomDataSignature (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<CustomDataSignature> (élément de modèles Visual Studio)"
  - "Élément CustomDataSignature (modèles Visual Studio)"
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# &#201;l&#233;ment CustomDataSignature (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie la signature de texte pour localiser les données personnalisées.  
  
## Syntaxe  
  
```  
<CustomDataSignature>"string"</CustomDataSignature>  
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
  
 Le texte est une chaîne qui possède la signature de texte requise pour localiser les données personnalisées.  
  
## Notes  
 `CustomDataSignature` est un élément facultatif.  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)