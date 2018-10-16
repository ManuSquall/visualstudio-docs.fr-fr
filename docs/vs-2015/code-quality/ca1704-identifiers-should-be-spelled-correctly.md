---
title: 'CA1704 : Les identificateurs doivent être correctement orthographiés | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a39b0a05efd70dcbfb611fba19c5e17250be5e78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263742"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704 : Les identificateurs doivent être correctement orthographiés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un identificateur contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque de vérificateur d’orthographe Microsoft. Cette règle ne pas vérifier les constructeurs ou les membres de dénomination spéciale telles que get et définir des accesseurs de propriété.

## <a name="rule-description"></a>Description de la règle
 Cette règle analyse l’identificateur dans des jetons et vérifie l’orthographe de chaque jeton. L’algorithme d’analyse effectue les transformations suivantes :

-   Les lettres majuscules démarrent un nouveau jeton. Par exemple, MonNomestJosé crée des jetons à « Mon », « Name », « Est », « Joe ».

-   Pour plusieurs lettres majuscules, la dernière lettre majuscule démarre un nouveau jeton. Par exemple, ÉditeurGUI crée des jetons à « Interface graphique utilisateur », « Éditeur ».

-   Début et de fin des apostrophes sont supprimés. Par exemple, 'sender' crée des jetons à « expéditeur ».

-   Traits de soulignement indiquent la fin d’un jeton et sont supprimés. Par exemple, Hello_world crée des jetons à « Hello », « world ».

-   Esperluettes incorporées sont supprimées. Par exemple, pour & mat crée des jetons pour « format ».

 Par défaut, la version anglaise (en) du vérificateur d’orthographe est utilisée. Aucun autre dictionnaire de langue n’est actuellement disponibles.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, corrigez l’orthographe du mot ou ajoutez le mot dans un dictionnaire personnalisé nommé CustomDictionary.xml. Placer le dictionnaire dans le répertoire d’installation de l’outil, le répertoire du projet, ou dans le répertoire associé à l’outil sous le profil de l’utilisateur (%USERPROFILE%\Application données\\...). Pour savoir comment ajouter le dictionnaire personnalisé à un projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consultez [Comment : personnaliser le dictionnaire d’analyse du Code](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

-   Ajouter des mots qui ne doivent pas provoquer une violation sous le chemin d’accès de mots/dictionnaire/reconnues.

-   Ajouter des mots qui doivent provoquer une violation sous le chemin d’accès de dictionnaire/mots/non reconnu.

-   Ajouter des mots qui doivent être marqués comme obsolète sous le chemin d’accès de mots/dictionnaire/déconseillées. Consultez la rubrique associée [CA1726 : utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)pour plus d’informations.

-   Ajoutez des exceptions aux règles de casse acronyme pour le chemin d’accès des acronymes/dictionnaire/CasingExceptions.

 Voici un exemple de la structure d’un fichier de dictionnaire personnalisé.

```
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement si le mot est intentionnellement mal orthographié et le mot s’applique à un ensemble limité de la bibliothèque. Mots épelés correctement réduisent la courbe d’apprentissage qui est requise pour les nouvelles bibliothèques de logiciels.

## <a name="related-rules"></a>Règles associées
 [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Voir aussi
 [Guide pratique pour personnaliser le dictionnaire d’analyse du code](../code-quality/how-to-customize-the-code-analysis-dictionary.md)



