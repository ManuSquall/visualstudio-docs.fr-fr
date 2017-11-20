---
title: ": Mots composés CA1702 doivent être correctement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c8606656b7ffe5f64c4c162b85d24bdbd9b1de0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702 : La casse des mots composés doit être correcte
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Avec rupture-lorsque déclenchée sur les assemblys.<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type.|  
  
## <a name="cause"></a>Cause  
 Le nom d’un identificateur contient plusieurs mots et au moins l’un des mots semble être un mot composé qui n’est pas correcte.  
  
## <a name="rule-description"></a>Description de la règle  
 Le nom de l’identificateur est fractionné en mots qui sont basées sur la casse. Chaque combinaison de deux mots contiguë est vérifiée par la bibliothèque du vérificateur d’orthographe Microsoft. S’il est reconnu, l’identificateur de produit une violation de la règle. Exemples de mots composés qui provoquent une violation sont « Somme de contrôle » et « MultiPart », la casse doit être en tant que « Somme de contrôle » et « Multipart », respectivement. En raison d’une utilisation commune précédente, plusieurs exceptions sont intégrées dans la règle et plusieurs mots entiers sont signalés, telles que « Toolbar » et « Filename », qui doit être celle de deux mots distincts (dans ce cas, « ToolBar » et « FileName »).  
  
 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Modifiez le nom afin qu’elle est correcte.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si les deux parties du mot composé sont reconnues par le dictionnaire d’orthographe et de l’objectif est d’utiliser les deux mots.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Affectation de noms](/dotnet/standard/design-guidelines/naming-guidelines)   
 [Conventions de mise en majuscules](/dotnet/standard/design-guidelines/capitalization-conventions)