---
title: "CA1701 : La casse des mots composés de chaînes de ressources doivent être correctement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0b4b154d6e959e636ee75481816a2424d5ea2e18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: La casse des mots composés de chaînes de ressources doit être correcte
|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une chaîne de ressource contient un mot composé qui ne semble pas être correcte.  
  
## <a name="rule-description"></a>Description de la règle  
 Chaque mot dans la chaîne de ressource est fractionné en jetons basés sur la casse. Chaque combinaison de deux jetons contiguë est vérifiée par la bibliothèque du correcteur orthographique Microsoft. S'il est reconnu, le mot produit une violation de la règle. Exemples de mots composés qui provoquent une violation sont « Somme de contrôle » et « MultiPart », la casse doit être en tant que « Somme de contrôle » et « Multipart », respectivement. En raison d’une utilisation commune précédente, plusieurs exceptions sont intégrées dans la règle et plusieurs mots entiers sont signalés, tels que « Toolbar » et « Filename », qui doit être celle de deux mots distincts. Dans cet exemple, « ToolBar » et « FileName » doivent être signalés.  
  
 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Modifier le mot afin qu’elle est correcte.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si les deux parties du mot composé sont reconnues par le dictionnaire d’orthographe et de l’objectif est d’utiliser les deux mots.  
  
 Vous pouvez également ajouter des mots composés à un dictionnaire personnalisé pour le vérificateur d’orthographe. Les mots dans le dictionnaire personnalisé ne provoquent pas de violations. Pour plus d’informations, consultez [Comment : personnaliser le dictionnaire d’analyse du Code](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="related-rules"></a>Règles associées  
 [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions de mise en majuscules](/dotnet/standard/design-guidelines/capitalization-conventions)   
 [Directives de nommage](/dotnet/standard/design-guidelines/naming-guidelines)