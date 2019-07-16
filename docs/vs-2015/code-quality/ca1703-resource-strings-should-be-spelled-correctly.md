---
title: 'CA1703 : Chaînes de ressources doivent être correctement orthographiés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1ff5a2600a4f40673f7d38dfe551ab9ac8cfe29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189215"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703 : L'orthographe des chaînes de ressources doit être correcte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Catégorie|Microsoft.Naming|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une chaîne de ressource contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft.

## <a name="rule-description"></a>Description de la règle
 Cette règle analyse la chaîne de ressource en mots (jetons de mots composés) et vérifie l’orthographe de chaque mot/jeton. Pour plus d’informations sur l’algorithme d’analyse, consultez [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Par défaut, la version anglaise (en) du vérificateur d’orthographe est utilisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, utilisez des mots entiers qui sont correctement orthographiés ou ajoutent les mots dans un dictionnaire personnalisé. Pour plus d’informations sur l’utilisation des dictionnaires personnalisés, consultez [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Mots épelés correctement réduisent le temps nécessaire pour apprendre les nouvelles bibliothèques de logiciels.

## <a name="related-rules"></a>Règles associées
 [CA1701 : Mots composés de chaînes de ressources doivent être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
