---
title: 'CA1721 : Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bf16a9edf25132aa8b58702f01563b8d7ccf109a
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841491"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721 : Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Le nom d’un membre commence par 'Get' et sinon correspond au nom d’une propriété. Par exemple, un type qui contient une méthode nommée 'GetColor' et une propriété qui est nommée « Color » provoque une violation de règle.

Par défaut, cette règle examine uniquement les propriétés et les membres visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Les méthodes et propriétés « Get » doivent porter des noms distinguant clairement leur fonction.

Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cette cohérence réduit le temps nécessaire pour apprendre une nouvelle bibliothèque de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Modifiez le nom afin qu’il ne correspond pas au nom d’une méthode qui est précédé de 'Get'.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

> [!NOTE]
> Cet avertissement peut être exclu si la méthode « Get » est causée par l’implémentation de IExtenderProvider (interface).

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1721.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (d’affectation de noms). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant contient une méthode ou une propriété qui violent cette règle.

[!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
[!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Règles associées

- [CA1024 : Utiliser des propriétés lorsque nécessaire](../code-quality/ca1024-use-properties-where-appropriate.md)