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
ms.openlocfilehash: 82146c2ac997a0202c20e15492becb89a293f427
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949445"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204 : Les littéraux doivent être orthographiés correctement

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une chaîne littérale est passée en tant qu’argument pour un paramètre localisable ou à une propriété localisable, et la chaîne contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque de vérificateur d’orthographe Microsoft.

## <a name="rule-description"></a>Description de la règle

Cette règle recherche une chaîne littérale qui est passée en tant que valeur à un paramètre ou une propriété lorsqu’un ou plusieurs des cas suivants est vrai :

- Le <xref:System.ComponentModel.LocalizableAttribute> attribut du paramètre ou de propriété est définie sur true.

- Le nom de paramètre ou une propriété contient « Text », « Message » ou « Caption ».

- Le nom de la variable de chaîne qui est passée à un <xref:System.Console.Write%2A> ou <xref:System.Console.WriteLine> méthode est « value » ou « format ».

Cette règle analyse la chaîne littérale en mots, jetons de mots composés et vérifie l’orthographe de chaque mot ou le jeton. Pour plus d’informations sur l’algorithme d’analyse, consultez [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Langue

Actuellement, le vérificateur d’orthographe vérifie uniquement à des dictionnaires de culture en anglais. Vous pouvez modifier la culture de votre projet dans le fichier projet, en ajoutant le **CodeAnalysisCulture** élément.

Exemple :

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Si vous définissez la culture sur autre chose qu’une culture en anglais, cette règle d’analyse du code est désactivée en mode silencieux.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, corrigez l’orthographe du mot ou ajoutez le mot au dictionnaire personnalisé. Pour plus d’informations sur l’utilisation des dictionnaires personnalisés, consultez [Comment : Personnaliser le dictionnaire d’analyse du Code](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Mots épelés correctement réduisent la courbe d’apprentissage nécessaire pour les nouvelles bibliothèques de logiciels.

## <a name="related-rules"></a>Règles associées

- [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703 : Chaînes de ressources doivent être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)