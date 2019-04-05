---
title: 'CA1724 : Noms de types ne doivent pas correspondre aux espaces de noms | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7fe95e08d2265baf06c6da265996ffcd579f0d1f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950058"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724 : Les noms de types ne doivent pas être identiques aux espaces de noms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un nom de type correspond à un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] noms d’espace de noms dans une comparaison respectant la casse.

## <a name="rule-description"></a>Description de la règle
 Les noms de types ne doivent pas correspondre aux noms d'espaces de noms définis dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Enfreindre cette règle peut réduire la facilité d'utilisation de la bibliothèque.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sélectionnez un nom de type qui ne correspond pas au nom d’un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] espace de noms de bibliothèque.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour un nouveau développement, aucun connus scénarios se produisent où vous devez supprimer un avertissement de cette règle. Avant de pouvoir supprimer l’avertissement, étudiez attentivement la façon dont les utilisateurs de votre bibliothèque peuvent être désorientés par le nom correspondant. Pour livrer des bibliothèques, vous devrez peut-être supprimer un avertissement de cette règle.
