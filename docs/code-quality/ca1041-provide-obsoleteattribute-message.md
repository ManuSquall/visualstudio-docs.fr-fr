---
title: 'CA1041 : Fournir un message ObsoleteAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a0545503b80e2f256593012e06cdf7ccd8b3b5b1
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547633"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041 : Fournir un message ObsoleteAttribute

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type ou un membre est marqué à l' <xref:System.ObsoleteAttribute?displayProperty=fullName> aide d’un attribut dont la <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propriété n’est pas spécifiée.

Par défaut, cette règle recherche uniquement les membres et les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

<xref:System.ObsoleteAttribute>est utilisé pour marquer les membres et les types de bibliothèque déconseillés. Les consommateurs de bibliothèque doivent éviter l’utilisation de n’importe quel type ou membre marqué comme obsolète. Cela est dû au fait qu’il n’est peut-être pas pris en charge et sera finalement supprimé des versions ultérieures de la bibliothèque. Lorsqu’un type ou membre marqué à l' <xref:System.ObsoleteAttribute> aide de est compilé <xref:System.ObsoleteAttribute.Message%2A> , la propriété de l’attribut est affichée. Cela fournit à l'utilisateur des informations sur le type ou le membre obsolète. Ces informations incluent généralement la durée pendant laquelle le type ou le membre obsolète sera pris en charge par les concepteurs de bibliothèques et le remplacement par défaut à utiliser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, ajoutez le `message` paramètre <xref:System.ObsoleteAttribute> au constructeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un avertissement de cette règle, <xref:System.ObsoleteAttribute.Message%2A> car la propriété fournit des informations critiques sur le type ou le membre obsolète.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un membre obsolète qui a un déclaré <xref:System.ObsoleteAttribute>correctement.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Voir aussi

- <xref:System.ObsoleteAttribute?displayProperty=fullName>