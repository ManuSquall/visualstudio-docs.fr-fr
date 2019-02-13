---
title: Caractères spéciaux MSBuild │ Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a96831650e09b1018c6cffc8149a9a0020edc90b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793098"
---
# <a name="msbuild-special-characters"></a>Caractères spéciaux MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] réserve certains caractères à une utilisation précise dans certains contextes. Pour les utiliser littéralement dans le contexte où ils sont réservés, il vous suffit de les placer dans une séquence d’échappement. Par exemple, un astérisque n’a une signification spéciale que dans les attributs `Include` et `Exclude` d’une définition d’élément, et dans les appels à `CreateItem`. Si vous souhaitez qu’un astérisque apparaisse comme un astérisque dans l’un de ces contextes, vous devez le placer dans une séquence d’échappement. Dans tous les autres contextes, tapez simplement l’astérisque là où vous souhaitez qu’il apparaisse.  
  
 Pour placer un caractère spécial dans une séquence d’échappement, utilisez la syntaxe %*xx*, où *xx* représente la valeur hexadécimale du caractère ASCII. Pour plus d’informations, consultez [Guide pratique pour utiliser des caractères spéciaux d’échappement dans MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Caractères spéciaux  
 Le tableau suivant répertorie les caractères spéciaux [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] :  
  
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
 [Éléments](../msbuild/msbuild-items.md)
