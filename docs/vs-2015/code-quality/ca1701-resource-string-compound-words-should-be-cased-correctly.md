---
title: 'CA1701 : La casse des mots composés de la chaîne de ressources doit être correcte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7610852f6d9fbea2fbd2dd10d478ad2d1a0da899
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669272"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701 : La casse des mots composés de la chaîne de ressources doit être correcte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Catégorie|Microsoft. Naming|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une chaîne de ressource contient un mot composé qui ne semble pas avoir une casse correcte.

## <a name="rule-description"></a>Description de la règle
 Chaque mot de la chaîne de ressource est fractionné en jetons basés sur la casse. Chaque combinaison de deux jetons contiguë est vérifiée par la bibliothèque du correcteur orthographique Microsoft. S'il est reconnu, le mot produit une violation de la règle. Les exemples de mots composés qui provoquent une violation sont « CheckSum » et « multipart », qui doivent respecter la casse « checksum » et « multipart », respectivement. En raison de l’utilisation courante précédente, plusieurs exceptions sont intégrées à la règle, et plusieurs mots uniques sont signalés, tels que « Toolbar » et « filename », qui doivent respecter la casse de deux mots distincts. Dans cet exemple, « ToolBar » et « FileName » sont signalés.

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Modifiez le mot de façon à ce qu’il respecte la casse.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si les deux parties du mot composé sont reconnues par le dictionnaire d’orthographe et si l’objectif est d’utiliser deux mots.

 Vous pouvez également ajouter des mots composés à un dictionnaire personnalisé pour le vérificateur d’orthographe. Les mots du dictionnaire personnalisé ne provoquent pas de violations. Pour plus d’informations, consultez [Guide pratique pour Personnaliser le ](../code-quality/how-to-customize-the-code-analysis-dictionary.md) du dictionnaire d’analyse du code.

## <a name="related-rules"></a>Règles associées
 [CA1702 : La casse des mots composés doit être correcte ](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709 : La casse des identificateurs doit être correcte ](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs ne doivent pas différer uniquement par la casse ](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Voir aussi
 [Conventions de mise en majuscules](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [Indications concernant l’attribution d’un nom](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
