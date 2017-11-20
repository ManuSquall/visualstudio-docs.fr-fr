---
title: ": Chaînes de ressources CA1703 doivent être correctement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c7828aa218933208408a285510e998921d6f032
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703 : L'orthographe des chaînes de ressources doit être correcte
|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une chaîne de ressource contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle analyse la chaîne de ressource en mots (jetons de mots composés) et vérifie l’orthographe de chaque mot/jeton. Pour plus d’informations sur l’algorithme d’analyse, consultez [CA1704 : les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Par défaut, la version anglaise (en) du vérificateur d’orthographe est utilisée.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, utilisez des mots entiers qui sont correctement orthographiés ou les ajouter à un dictionnaire personnalisé. Pour plus d’informations sur l’utilisation des dictionnaires personnalisés, consultez [CA1704 : les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Les mots orthographiés correctement réduisent le temps nécessaire pour apprendre les nouvelles bibliothèques de logiciels.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)