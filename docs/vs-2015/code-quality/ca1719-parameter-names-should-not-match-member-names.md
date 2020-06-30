---
title: 'Ca1719 : les noms des paramètres ne doivent pas correspondre aux noms des membres | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5024d2ddb7f31593c8eaedfc2fb421b4a0e9b0a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545364"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un membre visible de l’extérieur correspond, dans une comparaison qui ne respecte pas la casse, au nom de l’un de ses paramètres.

## <a name="rule-description"></a>Description de la règle
 Un nom de paramètre doit véhiculer la signification du paramètre et un nom de membre celle du membre. Un design où ceux-ci sont identiques est rare. Donner à un paramètre le même que son membre n'est pas une méthode intuitive et rend la bibliothèque difficile à utiliser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sélectionnez un nom de paramètre qui ne correspond pas au nom du membre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour un nouveau développement, aucun scénario connu ne se produit lorsque vous devez supprimer un avertissement de cette règle. Pour les bibliothèques d’expédition, vous devrez peut-être supprimer un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs ne doivent pas différer uniquement par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
