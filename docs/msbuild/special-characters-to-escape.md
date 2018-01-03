---
title: "Caractères d’échappement spéciaux | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2fde39272a9e9ededafd28a26a13f8c3adb9aaaf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="special-characters-to-escape"></a>Caractères d'échappement spéciaux
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
 [Guide pratique pour utiliser des caractères spéciaux d’échappement dans MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)