---
title: Caractères d’échappement spéciaux | Microsoft Docs
description: En savoir plus sur les caractères spéciaux qui doivent être échappés uniquement s’ils ont une signification particulière dans le contexte dans lequel ils sont utilisés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 433e762bf68b6a3956616e0ccccc229bca8f86b9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048266"
---
# <a name="special-characters-to-escape"></a>Caractères d’échappement spéciaux

Les caractères spéciaux doivent être échappés uniquement s'ils ont une signification spéciale dans le contexte dans lequel ils sont utilisés. Par exemple, l'astérisque (*) est un caractère spécial uniquement dans les attributs "Include" et "Exclude" d'une définition d'élément ou d'un appel à <xref:Microsoft.Build.Tasks.CreateItem>. Dans tous les autres cas, l'astérisque est traité comme un astérisque littéral. Même s'il n'est pas nécessaire d'échapper tous les astérisques des fichiers projet, cela ne peut pas faire de mal.

 Utilisez la notation% \<xx> à la place du caractère spécial, où \<xx> représente la valeur hexadécimale du caractère ASCII. Par exemple, pour utiliser un astérisque (*) comme caractère littéral, utilisez la valeur `%2A`.

 Voici la liste complète des caractères spéciaux d'échappement :

|Caractère|Encodage ASCII|Description|
|---------|----------|-----------|
|%|%25|Signe de pourcentage, utilisé pour référencer les métadonnées.|
|$|%24|Signe dollar, utilisé pour référencer des propriétés.|
|@|%40|Arobase, utilisée pour référencer des listes d'éléments.|
|(|%28|Parenthèse ouverte, utilisée dans les listes.|
|)|%29|Parenthèse fermée, utilisée dans les listes.|
|;|%3B|Point-virgule, utilisé comme séparateur de liste.|
|?|%3F|Point d'interrogation. Caractère générique pour la description d'une spécification de fichier dans la section Include/Exclude d'un élément.|
|* |%2A|Astérisque. Caractère générique pour la description d'une spécification de fichier dans la section Include/Exclude d'un élément.|

> [!NOTE]
> Dans certains scénarios, vous devrez peut-être placer des caractères de guillemet double ("), par exemple lors de l’utilisation d’une `Exec` tâche.

## <a name="see-also"></a>Voir aussi

- [Comment : échapper des caractères spéciaux dans MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
