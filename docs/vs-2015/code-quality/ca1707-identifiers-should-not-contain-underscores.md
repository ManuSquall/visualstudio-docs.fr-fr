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
ms.openlocfilehash: 8ae59f396115f10a858c5bc31d8bcdbf967d1d80
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59001852"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [CA1707 : Identificateurs ne doivent pas contenir de traits de soulignement](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores) sur docs.microsoft.com.  
  
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
