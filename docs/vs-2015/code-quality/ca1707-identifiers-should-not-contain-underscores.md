---
title: 'CA1707 : Identificateurs ne doivent pas contenir de traits de soulignement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7973646aab545484287f5628eb0fa3cf3629db84
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651943"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [CA1707 : Identificateurs ne doivent pas contenir de traits de soulignement](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Rupture - lorsque déclenchée sur les assemblys<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type|  
  
## <a name="cause"></a>Cause  
 Le nom d’un identificateur contient le caractère de soulignement (_).  
  
## <a name="rule-description"></a>Description de la règle  
 Par convention, les noms d'identificateurs ne contiennent pas de trait de soulignement (_). La règle vérifie les espaces de noms, types, membres et paramètres.  
  
 Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Supprimez tous les traits de soulignement du nom.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs doivent différer par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
