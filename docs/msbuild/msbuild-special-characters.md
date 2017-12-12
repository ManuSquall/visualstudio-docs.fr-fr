---
title: "Caractères spéciaux MSBuild │ Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 04b679ed649bc4fe01a2bccb08a8c5e137b6141d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-special-characters"></a>Caractères spéciaux MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] réserve certains caractères à une utilisation précise dans certains contextes. Pour les utiliser littéralement dans le contexte où ils sont réservés, il vous suffit de les placer dans une séquence d’échappement. Par exemple, un astérisque n’a une signification spéciale que dans les attributs `Include` et `Exclude` d’une définition d’élément, et dans les appels à `CreateItem`. Si vous souhaitez qu’un astérisque apparaisse comme un astérisque dans l’un de ces contextes, vous devez le placer dans une séquence d’échappement. Dans tous les autres contextes, tapez simplement l’astérisque là où vous souhaitez qu’il apparaisse.  
  
 Pour placer un caractère spécial dans une séquence d’échappement, utilisez la syntaxe %*xx*, où *xx* représente la valeur hexadécimale du caractère ASCII. Pour plus d’informations, consultez [Guide pratique pour utiliser des caractères spéciaux d’échappement dans MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Caractères spéciaux  
 Le tableau suivant répertorie les caractères spéciaux [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] :  
  
|**Caractère**|**ASCII**|**Utilisation réservée**|  
|-------------------|---------------|------------------------|  
|%|%25|Référencement des métadonnées|  
|$|%24|Référencement des propriétés|  
|@|%40|Référencement des listes d’éléments|  
|'|%27|Conditions et autres expressions|  
|;|%3B|Séparateur de liste|  
|?|%3F|Caractère générique pour les noms de fichiers des attributs `Include` et `Exclude`|  
|*|%2A|Caractère générique pour les noms de fichiers des attributs `Include` et `Exclude`|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)   
 [Éléments MSBuild](../msbuild/msbuild-items.md)