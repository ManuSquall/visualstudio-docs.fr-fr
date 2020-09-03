---
title: Caractères d’échappement spéciaux | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: beeed84db240ecf57ca18dd9aef08622f14b06fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161357"
---
# <a name="special-characters-to-escape"></a>Caractères d'échappement spéciaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les caractères spéciaux doivent être échappés uniquement s'ils ont une signification spéciale dans le contexte dans lequel ils sont utilisés. Par exemple, l'astérisque (*) est un caractère spécial uniquement dans les attributs "Include" et "Exclude" d'une définition d'élément ou d'un appel à <xref:Microsoft.Build.Tasks.CreateItem>. Dans tous les autres cas, l'astérisque est traité comme un astérisque littéral. Même s'il n'est pas nécessaire d'échapper tous les astérisques des fichiers projet, cela ne peut pas faire de mal.  
  
 Utilisez la notation %*xx* à la place du caractère spécial, où *xx* représente la valeur hexadécimale du caractère ASCII. Par exemple, pour utiliser un astérisque (*) comme caractère littéral, utilisez la valeur `%2A`.  
  
 Voici la liste complète des caractères spéciaux d'échappement :  
  
|Caractère|Description|  
|---------------|-----------------|  
|%|Signe de pourcentage, utilisé pour référencer les métadonnées.|  
|$|Signe dollar, utilisé pour référencer des propriétés.|  
|@|Arobase, utilisée pour référencer des listes d'éléments.|  
|(|Parenthèse ouverte, utilisée dans les listes.|  
|)|Parenthèse fermée, utilisée dans les listes.|  
|`|Apostrophe (ou graduation), utilisée dans les conditions et autres expressions.|  
|;|Point-virgule, utilisé comme séparateur de liste.|  
|?|Point d'interrogation. Caractère générique pour la description d'une spécification de fichier dans la section Include/Exclude d'un élément.|  
|*|Astérisque. Caractère générique pour la description d'une spécification de fichier dans la section Include/Exclude d'un élément.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : échapper des caractères spéciaux dans MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)
