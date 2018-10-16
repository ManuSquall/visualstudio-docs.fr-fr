---
title: 'CA1051 : Ne déclarez pas de champs d’instances visibles | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4c752b11a41bac148099042ff9c95845917a05ee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190908"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051 : Ne pas déclarer de champs d'instances visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type visible de l’extérieur a un champ d’instance extérieurement visible.

## <a name="rule-description"></a>Description de la règle
 Un champ s'utilise principalement en tant que détail d'implémentation. Les champs doivent être `private` ou `internal` et doivent être exposés à l’aide de propriétés. Il est aussi facile d’accéder à une propriété comme il est d’accéder à un champ, et le code dans les accesseurs d’une propriété peut changer lorsque les fonctionnalités du type évoluent sans introduire de modifications avec rupture. Propriétés qui retournent simplement la valeur d’un champ privé ou interne sont optimisées pour s’exécuter identiques à celles de l’accès à un champ ; très peu de gain de performances est associé à l’utilisation de champs extérieurement visibles sur les propriétés.

 Extérieurement visible fait référence à `public`, `protected`, et `protected internal` (`Public`, `Protected`, et `Protected Friend` en Visual Basic) niveaux d’accessibilité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez le champ `private` ou `internal` et l’exposer à l’aide d’une propriété visible de l’extérieur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Champs extérieurement visibles ne fournissent pas les avantages qui ne sont pas disponibles aux propriétés. En outre, les champs publics ne peuvent pas être protégés par [demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). Consultez [CA2112 : les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type (`BadPublicInstanceFields`) qui enfreint cette règle. `GoodPublicInstanceFields` Affiche le code corrigé.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Voir aussi
 [Demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



