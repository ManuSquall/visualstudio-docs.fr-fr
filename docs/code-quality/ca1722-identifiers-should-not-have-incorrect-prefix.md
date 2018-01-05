---
title: "CA1722 : Les identificateurs ne doivent pas porter un préfixe incorrect | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 141adcf6e21c7e0c8d737411988e73fbfbece805
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722 : Les identificateurs ne doivent pas porter un préfixe incorrect
|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un identificateur a un préfixe incorrect.  
  
## <a name="rule-description"></a>Description de la règle  
 Par convention, seuls certains éléments de programmation présentent des noms qui commencent par un préfixe spécifique.  
  
 Noms de types n’ont pas un préfixe spécifique et ne doivent pas être préfixés par un « C ». Cette règle rapporte des violations pour les noms de types tels que 'CMyClass' et ne signale pas les violations pour les noms de types tels que 'Cache'.  
  
 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Supprimez le préfixe de l’identificateur.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1715 : Les identificateurs doivent avoir un préfixe correct](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)