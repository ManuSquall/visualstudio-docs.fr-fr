---
title: 'CA1702 : Mots composés doivent être correcte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 91a3945c6ef212ba664119a822123f326cdefc5c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676397"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702 : La casse des mots composés doit être correcte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [CA1702 : Mots composés doivent être correcte](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly).  
  
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Avec rupture-lorsque déclenchée sur les assemblys.<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type.|  
  
## <a name="cause"></a>Cause  
 Le nom d’un identificateur contient plusieurs mots et au moins un des mots semble être un mot composé qui n’est pas correcte.  
  
## <a name="rule-description"></a>Description de la règle  
 Le nom de l’identificateur est fractionné en mots qui sont basées sur la casse. Chaque combinaison de deux mots contiguë est vérifiée par la bibliothèque de vérificateur d’orthographe Microsoft. S’il est reconnu, l’identificateur de produit une violation de la règle. Exemples de mots composés qui enfreint sont « CheckSum » et « MultiPart », la casse doit être en tant que « Checksum » et « Multipart », respectivement. En raison d’une utilisation commune précédente, plusieurs exceptions sont intégrées dans la règle et plusieurs mots entiers sont signalés, telles que « Toolbar » et « Filename », qui doit être celle de deux mots distincts (dans ce cas, « Barre d’outils » et « FileName »).  
  
 Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Modifiez le nom afin qu’elle est correcte.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si les deux parties du mot composé sont reconnues par le dictionnaire d’orthographe et de l’objectif consiste à utiliser deux mots.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1701 : Mots composés de chaînes de ressources doivent être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709 : Identificateurs doivent être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs doivent différer par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de dénomination](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [Conventions de mise en majuscules](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
