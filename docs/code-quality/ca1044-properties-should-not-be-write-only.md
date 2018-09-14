---
title: 'CA1044 : Les propriétés ne doivent pas être en écriture seule'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6018957bc6de32668cbaf0a719f2a603dc7f496f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550984"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044 : Les propriétés ne doivent pas être en écriture seule

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 La propriété publique ou protégée a un accesseur set, mais n’a pas d’accesseur get.

## <a name="rule-description"></a>Description de la règle
 Obtenir des accesseurs fournissent un accès en lecture à une propriété et accesseurs set fournissent un accès en écriture. Bien qu'il soit acceptable et souvent nécessaire de disposer d'une propriété en lecture seule, les règles de conception interdisent l'utilisation de propriétés en écriture seule. C’est parce que de permettre à un utilisateur de définir une valeur et empêcher ensuite l’affichage de la valeur de l’utilisateur ne fournit pas de toute la sécurité. De plus, sans accès en lecture, l'état des objets partagés ne peut s'afficher, ce qui limite leur utilité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez un accesseur get à la propriété. Ou bien, si le comportement d’une propriété en écriture seule est nécessaire, convertissez cette propriété à une méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est recommandé que vous ne supprimez pas un avertissement de cette règle.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, `BadClassWithWriteOnlyProperty` est un type avec une propriété en écriture seule. `GoodClassWithReadWriteProperty` contient le code corrigé.

 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]