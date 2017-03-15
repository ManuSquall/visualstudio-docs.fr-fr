---
title: "MSBuild Special Characters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "escape characters"
  - "escape"
  - "MSBuild Escape Characters"
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# MSBuild Special Characters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] réserve des caractères pour une utilisation spéciale dans des contextes spécifiques.  Vous devez seulement placer ces caractères dans une séquence d'échappement si vous souhaitez les utiliser littéralement dans le contexte dans lequel ils sont réservés.  Par exemple, un astérisque a uniquement une signification spéciale dans les attributs `Include` et `Exclude` d'une définition d'élément, ainsi que dans les appels à `CreateItem`.  Si vous souhaitez qu'un astérisque apparaisse comme un astérisque dans l'un de ces contextes, vous devez le placer dans une séquence d'échappement.  Dans chaque autre contexte, tapez juste l'astérisque où vous souhaitez qu'il apparaisse.  
  
 Pour placer un caractère spécial dans une séquence d'échappement, utilisez la syntaxe %*xx*, où *xx* représente la valeur hexadécimale ASCII du caractère.  Pour plus d'informations, consultez [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## Caractères spéciaux  
 Le tableau suivant répertorie les caractères spéciaux [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] :  
  
|**Caractère**|**ASCII**|**Utilisation réservée**|  
|-------------------|---------------|------------------------------|  
|%|%25|Référencement des métadonnées|  
|$|%24|Propriétés du référencement|  
|@|%40|Listes d'éléments de référencement|  
|'|%27|Conditions et autres expressions|  
|;|%3B|Séparateur de liste|  
|?|%3F|Caractère générique pour les noms de fichiers dans les attributs `Include` et `Exclude`|  
|\*|%2A|Caractère générique à utiliser pour les noms de fichiers dans les attributs `Include` et `Exclude`|  
  
## Voir aussi  
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md)   
 [Items](../msbuild/msbuild-items.md)