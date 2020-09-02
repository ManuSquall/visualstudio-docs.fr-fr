---
title: 'CA1044 : les propriétés ne doivent pas être en écriture seule | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ca0fb61c0973553ee6d410bc8b2718d19aeb28c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546859"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044 : Les propriétés ne doivent pas être en écriture seule
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 La propriété publique ou protégée a un accesseur Set mais n’a pas d’accesseur Get.

## <a name="rule-description"></a>Description de la règle
 Les accesseurs d’accès fournissent un accès en lecture à une propriété et les accesseurs set fournissent un accès en écriture. Bien qu'il soit acceptable et souvent nécessaire de disposer d'une propriété en lecture seule, les règles de conception interdisent l'utilisation de propriétés en écriture seule. Cela est dû au fait que permettre à un utilisateur de définir une valeur et d’empêcher l’utilisateur d’afficher la valeur ne fournit aucune sécurité. De plus, sans accès en lecture, l'état des objets partagés ne peut s'afficher, ce qui limite leur utilité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez un accesseur get à la propriété. Sinon, si le comportement d’une propriété en écriture seule est nécessaire, envisagez de convertir cette propriété en méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est fortement recommandé de ne pas supprimer un avertissement de cette règle.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, `BadClassWithWriteOnlyProperty` est un type avec une propriété en écriture seule. `GoodClassWithReadWriteProperty` contient le code corrigé.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
