---
title: 'CA2204 : les littéraux doivent être orthographiés correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ecf829251cbeab600cb95f8f0c0b0173cd7338d4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546274"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204 : Les littéraux doivent être orthographiés correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode passe une chaîne littérale à qui est utilisée dans un paramètre ou une propriété qui requiert une chaîne localisée et la chaîne littérale contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d’orthographe Microsoft.

## <a name="rule-description"></a>Description de la règle
 Cette règle vérifie une chaîne littérale transmise en tant que valeur à un paramètre ou à une propriété lorsqu’un ou plusieurs des cas suivants sont vrais :

- L' <xref:System.ComponentModel.LocalizableAttribute> attribut du paramètre ou de la propriété a la valeur true.

- Le nom du paramètre ou de la propriété contient « Text », « message » ou « Caption ».

- Le nom du paramètre de chaîne passé à une méthode Console. Write ou console. WriteLine est « value » ou « format ».

  Cette règle analyse la chaîne littérale en mots, en jetons des mots composés et vérifie l’orthographe de chaque mot/jeton. Pour plus d’informations sur l’algorithme d’analyse, consultez [CA1704 : les identificateurs doivent être orthographiés correctement](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Par défaut, la version anglaise (en) du vérificateur d’orthographe est utilisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, corrigez l’orthographe du mot ou ajoutez le mot à un dictionnaire personnalisé. Pour plus d’informations sur l’utilisation des dictionnaires personnalisés, consultez [Comment : personnaliser le dictionnaire d’analyse du code](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Les mots correctement orthographiés réduisent la courbe d’apprentissage requise pour les nouvelles bibliothèques logicielles.

## <a name="related-rules"></a>Règles associées
 [CA1704 : L'orthographe des identificateurs doit être correcte](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703 : L'orthographe des chaînes de ressources doit être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
