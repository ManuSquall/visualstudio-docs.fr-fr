---
title: "TemplateGroupID, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID"
helpviewer_keywords: 
  - "<TemplateGroupID> (élément de modèles Visual Studio)"
  - "TemplateGroupID (élément de modèles Visual Studio)"
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# TemplateGroupID, &#233;l&#233;ment (mod&#232;les Visual&#160;Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie le genre de projet dans lequel les modèles d'élément doivent s'afficher.  Cet élément est important quand [ShowByDefault \(modèles Visual Studio\)](../extensibility/showbydefault-visual-studio-templates.md) a la valeur `false`.  Quand [ShowByDefault \(modèles Visual Studio\)](../extensibility/showbydefault-visual-studio-templates.md) a la valeur `true`, un modèle d'élément est disponible dans tous les types de projet.  
  
## Syntaxe  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle et comment il s'affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément**.|  
  
## Valeur texte  
 Une valeur texte est requise.  
  
 Le texte spécifie un identificateur pour une catégorie de modèles d'élément.  
  
## Notes  
 `TemplateGroupID` est un élément.  
  
 La valeur de l'élément `TemplateGroupID` est utilisée avec l'inscription système du projet \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<numéro de version\>*\\Projects\\\) pour filtrer les modèles qui s'affichent dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
|Valeur Visual C\+\+|Signification|  
|-------------------------|-------------------|  
|VC\-Native|Utilisé pour les projets natifs.  Correspond également à la valeur par défaut, s'il est impossible de déterminer un type de projet.|  
|VC\-Managed|Utilisé pour les projets managés \(\/clr\)|  
|VC\-Windows|Utilisé pour tous les projets qui ciblent la plateforme Windows \(natifs\/managés\/Store\)|  
|WinRT\-Native\-UAP|Utilisé pour les projets de Store Windows 10|  
|CodeSharing\-Native|Utilisé pour les projets d'éléments partagés|  
|WinRT\-Native\-6.3|Utilisé pour les projets de Store Windows 8.1|  
|WinRT\-Native\-Phone\-6.3|Utilisé pour les projets Windows Phone 8.1|  
|WinRT\-Native|Utilisé pour les projets de Store Windows 8.0|  
|VC\-Android|Utilisé pour les projets Android|  
  
## Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)