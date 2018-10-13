---
title: 'CA1719 : Les noms de paramètres ne doivent pas correspondre aux noms de membres | Microsoft Docs'
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
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 13a6326391e543ef8220725ae982b8cfa75abb1b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216690"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un membre extérieurement visible correspond, dans une comparaison respectant la casse, le nom d’un de ses paramètres.

## <a name="rule-description"></a>Description de la règle
 Un nom de paramètre doit véhiculer la signification du paramètre et un nom de membre celle du membre. Un design où ceux-ci sont identiques est rare. Donner à un paramètre le même que son membre n'est pas une méthode intuitive et rend la bibliothèque difficile à utiliser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sélectionnez un nom de paramètre qui ne correspond pas le nom du membre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour un nouveau développement, aucun connus scénarios se produisent où vous devez supprimer un avertissement de cette règle. Pour livrer des bibliothèques, vous devrez peut-être supprimer un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)



