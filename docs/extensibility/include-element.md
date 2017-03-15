---
title: "&#201;l&#233;ment Include | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Include"
helpviewer_keywords: 
  - "Inclure l'élément (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, Include"
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# &#201;l&#233;ment Include
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément Include spécifie un fichier qui peut être localisé sur fourni inclut le chemin d'accès pour l'insérer dans le fichier actuel.  Tous les symboles et les types définis feront partie du résultat compilé.  
  
## Syntaxe  
  
```c#  
<Include href="stdidcmd.h" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|href|Obligatoire. Le chemin d'accès au fichier d'en\-tête :<br /><br /> href\="stdidcmd.h »|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun|Aucun.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes, autrement dit, les éléments de menu, menus, barres d'outils et des zones de liste déroulante, assurant un VSPackage à l'IDE.|  
  
## Exemple  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)