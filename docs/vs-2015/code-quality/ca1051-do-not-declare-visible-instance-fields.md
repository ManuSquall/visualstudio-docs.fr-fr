---
title: 'CA1051 : ne pas déclarer les champs d’instance visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 41332ab7d729f7b2187ccace6b05fe2d17763a0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672515"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051 : Ne pas déclarer de champs d'instances visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type visible de l’extérieur contient un champ d’instance visible de l’extérieur.

## <a name="rule-description"></a>Description de la règle
 Un champ s'utilise principalement en tant que détail d'implémentation. Les champs doivent être `private` ou `internal` et doivent être exposés à l’aide de propriétés. Il est aussi facile d’accéder à une propriété que d’accéder à un champ, et le code des accesseurs d’une propriété peut changer à mesure que les fonctionnalités du type se développent sans introduire de modifications avec rupture. Les propriétés qui retournent simplement la valeur d’un champ privé ou interne sont optimisées pour s’exécuter sur les avec l’accès à un champ ; un gain de performances très faible est associé à l’utilisation de champs visibles de l’extérieur sur les propriétés.

 En externe, fait référence aux niveaux d’accessibilité `public`, `protected` et `protected internal` (`Public`, `Protected` et `Protected Friend` dans Visual Basic).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, définissez le champ `private` ou `internal` et exposez-le à l’aide d’une propriété visible de l’extérieur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Les champs visibles de l’extérieur ne fournissent aucun avantage qui ne sont pas disponibles pour les propriétés. En outre, les champs publics ne peuvent pas être protégés par des [demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). Consultez [CA2112 : les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Exemple
 L’exemple suivant montre un type (`BadPublicInstanceFields`) qui enfreint cette règle. `GoodPublicInstanceFields` affiche le code corrigé.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Voir aussi
 [Demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
