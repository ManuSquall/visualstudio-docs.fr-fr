---
title: "CA1724 : Les noms de types ne doivent pas correspondre aux espaces de noms | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 556fd9eee1bc453d4f9782459050367e18a3193b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724 : les noms de types ne doivent pas être identiques aux espaces de noms
|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un nom de type correspond à un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] noms d’espace de noms dans une comparaison respectant la casse.  
  
## <a name="rule-description"></a>Description de la règle  
 Les noms de types ne doivent pas correspondre aux noms d'espaces de noms définis dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Enfreindre cette règle peut réduire la facilité d'utilisation de la bibliothèque.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Sélectionnez un nom de type qui ne correspond pas à celui d’un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] espace de noms de bibliothèque.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Pour un nouveau développement, aucun autre scénarios se produisent lorsque vous devez supprimer un avertissement de cette règle. Avant de pouvoir supprimer l’avertissement, étudiez attentivement la façon dont les utilisateurs de votre bibliothèque peuvent être perdus par le nom correspondant. Pour livrer des bibliothèques, vous devrez peut-être supprimer un avertissement de cette règle.