---
title: "CA1709 : La casse des identificateurs doivent être correctement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9332359228d657e9155996443822a5d1c11ad01
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709 : La casse des identificateurs doit être correcte
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Avec rupture - lorsque déclenchée sur les assemblys, espaces de noms, types, membres et paramètres.<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type générique.|  
  
## <a name="cause"></a>Cause  
 Le nom d’un identificateur n’est pas correcte.  
  
 \- ou -  
  
 Le nom d’un identificateur contient un acronyme de deux lettres, et la deuxième lettre est en minuscule.  
  
 \- ou -  
  
 Le nom d’un identificateur contient un acronyme de trois lettres majuscules.  
  
## <a name="rule-description"></a>Description de la règle  
 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage qui est requis pour les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
 Par convention, les noms de paramètres utilisent la casse mixte ; Pascal les noms d’espace de noms, type et membre utilisent la casse. Dans un nom en casse Pascal, la première lettre est en minuscule et la première lettre des mots restants dans le nom est en majuscules. Exemples de noms de casse mixte sont « packetSniffer », « ioFile » et « fatalErrorCode ». Dans un nom de la casse Pascal, la première lettre est en majuscule, et la première lettre des mots restants dans le nom est en majuscules. Exemples de noms de la casse Pascal sont « PacketSniffer », « IOFile » et « FatalErrorCode ».  
  
 Cette règle fractionne le nom en mots en fonction de la casse et vérifie tous les mots à deux lettres à une liste de mots de deux lettres communs, tels que « In » ou « My ». Si une correspondance est introuvable, le mot est considéré comme un acronyme. En outre, cette règle suppose qu’il a détecté un acronyme lorsque le nom contient quatre lettres majuscules dans une ligne ou trois lettres majuscules dans une ligne à la fin du nom.  
  
 Par convention, les acronymes de deux lettres utilisent toutes les lettres majuscules et les acronymes de trois caractères ou plus Pascal casse. Les exemples suivants utilisent cette convention d’affectation de noms : 'DB', 'CR', 'ACP' et 'Ecma'. Les exemples suivants enfreignent la convention : 'Io', 'XML' et 'DoD' et les noms nonparameter, 'xp' et 'du Panneau de configuration'.  
  
 'ID' est d’une casse particulière pour provoquer une violation de cette règle. 'Id' n’est pas un acronyme mais une abréviation pour « identification ».  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Modifiez le nom afin qu’elle est correcte.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer cet avertissement si vous avez vos propres conventions d’affectation de noms, ou si l’identificateur représente un nom approprié, par exemple, le nom d’une société ou une technologie.  
  
 Vous pouvez également ajouter des termes spécifiques, les acronymes et les abréviations que pour un dictionnaire d’analyse du code personnalisé. Termes spécifiés dans le dictionnaire personnalisé n’entraînent pas de violations de cette règle. Pour plus d’informations, consultez [Comment : personnaliser le dictionnaire d’analyse du Code](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Règles associées  
 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)