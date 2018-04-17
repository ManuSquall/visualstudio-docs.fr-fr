---
title: 'CA1719 : Les noms de paramètres ne doivent pas correspondre aux noms de membres | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 402744debf3ad94ff303a5d27a39b67d41faa341
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres
|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Le nom d’un membre extérieurement visible correspond, dans une comparaison respectant la casse, le nom de l’un de ses paramètres.  
  
## <a name="rule-description"></a>Description de la règle  
 Un nom de paramètre doit véhiculer la signification du paramètre et un nom de membre celle du membre. Un design où ceux-ci sont identiques est rare. Donner à un paramètre le même que son membre n'est pas une méthode intuitive et rend la bibliothèque difficile à utiliser.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Sélectionnez un nom de paramètre qui ne correspond pas le nom du membre.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Pour un nouveau développement, aucun autre scénarios se produisent lorsque vous devez supprimer un avertissement de cette règle. Pour livrer des bibliothèques, vous devrez peut-être supprimer un avertissement de cette règle.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)