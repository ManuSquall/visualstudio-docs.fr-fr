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
ms.openlocfilehash: 51427ec499c223c50fbe72523a3be44ed0ce9094
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449220"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041 : Fournir un message ObsoleteAttribute

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type ou un membre est marqué à l’aide d’un attribut <xref:System.ObsoleteAttribute?displayProperty=fullName> qui n’a pas sa propriété <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> spécifiée.

Par défaut, cette règle recherche uniquement les membres et les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

<xref:System.ObsoleteAttribute> est utilisé pour marquer les membres et les types de bibliothèque déconseillés. Les consommateurs de bibliothèque doivent éviter l’utilisation de n’importe quel type ou membre marqué comme obsolète. Cela est dû au fait qu’il n’est peut-être pas pris en charge et sera finalement supprimé des versions ultérieures de la bibliothèque. Lorsqu’un type ou membre marqué à l’aide de <xref:System.ObsoleteAttribute> est compilé, la propriété <xref:System.ObsoleteAttribute.Message%2A> de l’attribut est affichée. Cela fournit à l'utilisateur des informations sur le type ou le membre obsolète. Ces informations incluent généralement la durée pendant laquelle le type ou le membre obsolète sera pris en charge par les concepteurs de bibliothèques et le remplacement par défaut à utiliser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, ajoutez le paramètre `message` au constructeur <xref:System.ObsoleteAttribute>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un avertissement de cette règle, car la propriété <xref:System.ObsoleteAttribute.Message%2A> fournit des informations critiques sur le type ou le membre obsolète.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant montre un membre obsolète qui a un @no__t correctement déclaré.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Voir aussi

- <xref:System.ObsoleteAttribute?displayProperty=fullName>
