---
title: 'CA1709 : Identificateurs doivent être correcte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4f2fff418e8d791898a4e5db00fe639b5d524d95
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59001849"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709 : La casse des identificateurs doit être correcte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [CA1709 : Identificateurs doivent être correcte](https://docs.microsoft.com/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly) sur docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Avec rupture - lorsque déclenchée sur les assemblys, espaces de noms, types, membres et paramètres.<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type générique.|  
  
## <a name="cause"></a>Cause  
 Le nom d’un identificateur n’est pas correcte.  
  
 \- ou -  
  
 Le nom d’un identificateur contient un acronyme de deux lettres et la deuxième lettre est en minuscule.  
  
 \- ou -  
  
 Le nom d’un identificateur contient un acronyme de trois lettres majuscules.  
  
## <a name="rule-description"></a>Description de la règle  
 Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
 Par convention, les noms de paramètres utilisent la casse mixte ; espace de noms, type, noms de membre et utilisent Pascal casse. Dans un nom de casse mixte, la première lettre est en minuscule et la première lettre de tout mot restant dans le nom est en majuscules. Exemples de noms de casse mixte sont « packetSniffer », « ioFile » et « fatalErrorCode ». Dans un nom de la casse Pascal, la première lettre est majuscule, et la première lettre de tout mot restant dans le nom est en majuscules. Exemples de noms de la casse Pascal sont « PacketSniffer », « IOFile » et « FatalErrorCode ».  
  
 Cette règle fractionne le nom en mots en fonction de la casse et vérifie les mots de deux lettres à une liste de mots à deux lettres communs, tels que « In » ou « My ». Si une correspondance est introuvable, le mot est censé pour être un acronyme. En outre, cette règle suppose qu’il a détecté un acronyme lorsque le nom contient quatre lettres majuscules dans une ligne ou trois lettres majuscules dans une ligne à la fin du nom.  
  
 Par convention, les acronymes de deux lettres utilisent toutes les lettres majuscules et les acronymes de trois caractères ou plus Pascal casse. Les exemples suivants utilisent cette convention d’affectation de noms : 'DB', 'CR', 'Cpa' et 'Ecma'. Les exemples suivants enfreignent la convention : « E/s », 'XML' et 'DoD', ainsi que pour les noms nonparameter, 'xp' et 'cpl'.  
  
 « ID » est de cas spéciaux pour provoquer une violation de cette règle. 'Id' n’est pas un acronyme mais une abréviation pour « identification ».  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Modifiez le nom afin qu’elle est correcte.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer cet avertissement si vous avez vos propres conventions d’affectation de noms, ou si l’identificateur représente un nom approprié, par exemple, le nom d’une société ou une technologie sans.  
  
 Vous pouvez également ajouter des termes, abréviations et acronymes à un dictionnaire d’analyse du code personnalisé. Termes spécifiés dans le dictionnaire personnalisé n’entraînent pas de violations de cette règle. Pour plus d'informations, voir [Procédure : Personnaliser le dictionnaire d’analyse du Code](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Règles associées  
 [CA1708 : Les identificateurs doivent différer par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
