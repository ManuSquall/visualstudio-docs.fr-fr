---
title: 'CA1724 : les noms de types ne doivent pas être identiques aux espaces de noms'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c178558743ca69fb3b62eccaf8164e4b49167ad3
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547566"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724 : les noms de types ne doivent pas être identiques aux espaces de noms
|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un nom de type correspond à un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] noms d’espace de noms dans une comparaison respectant la casse.

## <a name="rule-description"></a>Description de la règle
 Les noms de types ne doivent pas correspondre aux noms d'espaces de noms définis dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Enfreindre cette règle peut réduire la facilité d'utilisation de la bibliothèque.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sélectionnez un nom de type qui ne correspond pas au nom d’un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] espace de noms de bibliothèque.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour un nouveau développement, aucun connus scénarios se produisent où vous devez supprimer un avertissement de cette règle. Avant de pouvoir supprimer l’avertissement, étudiez attentivement la façon dont les utilisateurs de votre bibliothèque peuvent être désorientés par le nom correspondant. Pour livrer des bibliothèques, vous devrez peut-être supprimer un avertissement de cette règle.