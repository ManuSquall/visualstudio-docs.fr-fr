---
title: "CA1703 : L'orthographe des chaînes de ressources doit être correcte"
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edd3945953a07b10aee5c2690a25aafe446e2c10
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234324"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703 : L'orthographe des chaînes de ressources doit être correcte

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Category|Microsoft.Naming|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une chaîne de ressource contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft.

## <a name="rule-description"></a>Description de la règle

Cette règle analyse la chaîne de ressource en mots (en jetons les mots composés) et vérifie l’orthographe de chaque mot/jeton. Pour plus d’informations sur l’algorithme d' [analyse, consultez CA1704 : Les identificateurs doivent être correctement](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)orthographiés.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, utilisez des mots complets correctement orthographiés ou ajoutez les mots à un dictionnaire personnalisé. Pour plus d’informations sur l’utilisation des dictionnaires personnalisés [, consultez CA1704 : Les identificateurs doivent être correctement](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)orthographiés.

## <a name="change-the-dictionary-language"></a>Modifier la langue du dictionnaire

Par défaut, la version anglaise (en) du vérificateur d’orthographe est utilisée. Si vous souhaitez modifier la langue du vérificateur d’orthographe, vous pouvez le faire en ajoutant l’un des attributs suivants à votre fichier *AssemblyInfo.cs* ou *AssemblyInfo. vb* :

- Utilisez <xref:System.Reflection.AssemblyCultureAttribute> pour spécifier la culture si vos ressources se trouvent dans un assembly satellite.
- Utilisez <xref:System.Resources.NeutralResourcesLanguageAttribute> pour spécifier la *culture neutre* de votre assembly si vos ressources se trouvent dans le même assembly que votre code.

> [!IMPORTANT]
> Si vous définissez la culture sur une culture autre que l’anglais, cette règle d’analyse du code est désactivée en mode silencieux.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Les mots correctement orthographiés réduisent le temps nécessaire pour apprendre les nouvelles bibliothèques logicielles.

## <a name="related-rules"></a>Règles associées

- [CA1701 La casse des mots composés de la chaîne de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704 Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204 Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)