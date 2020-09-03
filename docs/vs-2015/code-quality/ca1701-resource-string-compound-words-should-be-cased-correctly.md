---
title: 'Ca1701 : la casse des mots composés de chaînes de ressources doit être correcte | Microsoft Docs'
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
ms.openlocfilehash: 7c1c3b0fd6cf3a25d5db9e3039d4dc5d8364a18e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544103"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701 : La casse des mots composés de la chaîne de ressources doit être correcte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Category|Microsoft. Naming|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Une chaîne de ressource contient un mot composé qui ne semble pas avoir une casse correcte.

## <a name="rule-description"></a>Description de la règle
 Chaque mot de la chaîne de ressource est fractionné en jetons basés sur la casse. Chaque combinaison de deux jetons contiguë est vérifiée par la bibliothèque du correcteur orthographique Microsoft. S'il est reconnu, le mot produit une violation de la règle. Les exemples de mots composés qui provoquent une violation sont « CheckSum » et « multipart », qui doivent respecter la casse « checksum » et « multipart », respectivement. En raison de l’utilisation courante précédente, plusieurs exceptions sont intégrées à la règle, et plusieurs mots uniques sont signalés, tels que « Toolbar » et « filename », qui doivent respecter la casse de deux mots distincts. Dans cet exemple, « ToolBar » et « FileName » sont signalés.

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles et augmente la confiance des clients dans la mesure où la bibliothèque a été développée par une personne ayant une expertise dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Modifiez le mot de façon à ce qu’il respecte la casse.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si les deux parties du mot composé sont reconnues par le dictionnaire d’orthographe et si l’objectif est d’utiliser deux mots.

 Vous pouvez également ajouter des mots composés à un dictionnaire personnalisé pour le vérificateur d’orthographe. Les mots du dictionnaire personnalisé ne provoquent pas de violations. Pour plus d’informations, consultez [Comment : personnaliser le dictionnaire d’analyse du code](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Règles associées
 [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708 : Les identificateurs ne doivent pas différer uniquement par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Voir aussi
 [Capitalization Conventions](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [Recommandations](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) en matière de nommage des conventions de capitalisation
