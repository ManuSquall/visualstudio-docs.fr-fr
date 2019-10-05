---
title: 'CA2204 : Les littéraux doivent être orthographiés correctement'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6763fd9f8999bd590511026f6571db6a747c43bc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231858"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204 : Les littéraux doivent être orthographiés correctement

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une chaîne littérale est transmise en tant qu’argument pour un paramètre localisable, ou à une propriété localisable, et la chaîne contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d’orthographe Microsoft.

## <a name="rule-description"></a>Description de la règle

Cette règle vérifie une chaîne littérale transmise en tant que valeur à un paramètre ou à une propriété lorsqu’un ou plusieurs des cas suivants sont vrais :

- L' <xref:System.ComponentModel.LocalizableAttribute> attribut du paramètre ou de la propriété a la valeur true.

- Le nom du paramètre ou de la propriété contient « Text », « message » ou « Caption ».

- Le nom de la variable de chaîne qui est passé à <xref:System.Console.Write%2A> une <xref:System.Console.WriteLine> méthode ou est « value » ou « format ».

Cette règle analyse la chaîne littérale en mots, en jetons des mots composés et vérifie l’orthographe de chaque mot ou jeton. Pour plus d’informations sur l’algorithme d' [analyse, consultez CA1704 : Les identificateurs doivent être correctement](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)orthographiés.

## <a name="language"></a>Langue

Le vérificateur d’orthographe ne vérifie actuellement que les dictionnaires de culture en anglais. Vous pouvez modifier la culture de votre projet dans le fichier projet, en ajoutant l’élément **CodeAnalysisCulture** .

Par exemple :

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Si vous définissez la culture sur une culture autre que l’anglais, cette règle d’analyse du code est désactivée en mode silencieux.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, corrigez l’orthographe du mot ou ajoutez le mot à un dictionnaire personnalisé. Pour plus d’informations sur l’utilisation des dictionnaires personnalisés [, consultez Procédure : Personnaliser le dictionnaire](../code-quality/how-to-customize-the-code-analysis-dictionary.md)d’analyse du code.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Les mots correctement orthographiés réduisent la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles.

## <a name="related-rules"></a>Règles associées

- [CA1704 Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703 L’orthographe des chaînes de ressources doit être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)