---
title: 'CA1704 : les identificateurs doivent être correctement orthographiés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56ac5e60964621859c77bf53dc4f6c14480b4a83
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669237"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704 : Les identificateurs doivent être correctement orthographiés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un identificateur contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d’orthographe Microsoft. Cette règle ne vérifie pas les constructeurs ou les membres nommés spéciaux, tels que les accesseurs de propriété d’extraction et de définition.

## <a name="rule-description"></a>Description de la règle
 Cette règle analyse l’identificateur dans des jetons et vérifie l’orthographe de chaque jeton. L’algorithme d’analyse effectue les transformations suivantes :

- Les lettres majuscules démarrent un nouveau jeton. Par exemple, MyNameIsJoe régit « My », « Name », « is », « Joe ».

- Pour plusieurs lettres majuscules, la dernière lettre majuscule démarre un nouveau jeton. Par exemple, GUIEditor régit « GUI », « éditeur ».

- Les apostrophes de début et de fin sont supprimées. Par exemple, « sender » régit « sender ».

- Les traits de soulignement signifient la fin d’un jeton et sont supprimés. Par exemple, Hello_world régit « Hello », « World ».

- Les perluète incorporées sont supprimées. Par exemple, pour & tapis régit sous forme de « format ».

  Par défaut, la version anglaise (en) du vérificateur d’orthographe est utilisée. Aucun autre dictionnaire de langue n’est actuellement disponible.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, corrigez l’orthographe du mot ou ajoutez le mot à un dictionnaire personnalisé nommé CustomDictionary. Xml. Placez le dictionnaire dans le répertoire d’installation de l’outil, dans le répertoire du projet ou dans le répertoire associé à l’outil sous le profil de l’utilisateur (%USERPROFILE%\Application Data \\...). Pour savoir comment ajouter le dictionnaire personnalisé à un projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consultez [Comment : personnaliser le dictionnaire d’analyse du code](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Ajoutez des mots qui ne doivent pas provoquer une violation sous le dictionnaire/mots/chemin d’accès reconnu.

- Ajoutez des mots qui doivent provoquer une violation sous le dictionnaire/mots/chemin non reconnu.

- Ajoutez les mots qui doivent être signalés comme obsolètes sous le chemin Dictionary/Words/Deprecated. Pour plus d’informations, consultez la rubrique relative à la règle associée [CA1726 : utiliser les termes préférés](../code-quality/ca1726-use-preferred-terms.md).

- Ajoutez des exceptions aux règles de casse des acronymes au chemin dictionary/acronymes/CasingExceptions.

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
 Supprimez un avertissement de cette règle uniquement si le mot est intentionnellement mal orthographié et que le mot s’applique à un ensemble limité de la bibliothèque. Les mots correctement orthographiés réduisent la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles.

## <a name="related-rules"></a>Règles associées
 [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Voir aussi
 [Guide pratique pour personnaliser le dictionnaire d’analyse du code](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
