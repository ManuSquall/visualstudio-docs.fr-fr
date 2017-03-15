---
title: "Icon, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, icône"
  - "Icon, élément (schéma XML de VSCT)"
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Icon, &#233;l&#233;ment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'attribut guid de la balise de l'icône est le guid de la bitmap défini.  L'attribut id sélectionne l'emplacement de la bande de la bitmap. Cet élément est facultatif.  L'absence de cet élément la valeur de **guidOfficeIcon:msotcidNoIcon** est impliquée.  
  
## Syntaxe  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|GUID|Obligatoire. Le guid de la bitmap défini.|  
|ID|Obligatoire. Sélectionne l'emplacement de la bande de la bitmap.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun|Aucun.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de boutons](../extensibility/buttons-element.md)||  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)