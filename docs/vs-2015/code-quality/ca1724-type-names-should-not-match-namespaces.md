---
title: 'CA1724 : les noms de types ne doivent pas correspondre à des espaces de noms | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa0b73b6608f0dfd5daa4b770b7d780e64704c99
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544428"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724 : Les noms de types ne doivent pas être identiques aux espaces de noms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un nom de type correspond à un nom [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] d’espace de noms dans une comparaison qui ne respecte pas la casse.

## <a name="rule-description"></a>Description de la règle
 Les noms de types ne doivent pas correspondre aux noms d'espaces de noms définis dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Enfreindre cette règle peut réduire la facilité d'utilisation de la bibliothèque.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sélectionnez un nom de type qui ne correspond pas au nom d’un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] espace de noms de bibliothèque de classes.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour un nouveau développement, aucun scénario connu ne se produit lorsque vous devez supprimer un avertissement de cette règle. Avant de supprimer l’avertissement, réfléchissez bien à la façon dont les utilisateurs de votre bibliothèque peuvent être confondus par le nom correspondant. Pour les bibliothèques d’expédition, vous devrez peut-être supprimer un avertissement de cette règle.
