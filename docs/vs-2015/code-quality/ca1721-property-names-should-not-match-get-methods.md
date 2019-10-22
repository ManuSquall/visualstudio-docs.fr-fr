---
title: 'Ca1721 : les noms de propriété ne doivent pas correspondre à des méthodes d’extraction | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 366932c83328c6810e0103308db1c73a3e3076cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671605"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721 : Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Category|Microsoft. Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un membre public ou protégé commence par’obtenir’et correspond au nom d’une propriété publique ou protégée. Par exemple, un type qui contient une méthode nommée’GetColor’et une propriété nommée’Color’ne respecte pas cette règle.

## <a name="rule-description"></a>Description de la règle
 Les méthodes et les propriétés d’obtenir doivent avoir des noms qui distinguent clairement leur fonction.

 Les conventions d’affectation de noms fournissent une recherche commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit le temps nécessaire à l’apprentissage d’une nouvelle bibliothèque de logiciels et augmente la confiance des clients dans le développement de la bibliothèque par une personne expérimentée dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Modifiez le nom afin qu’il ne corresponde pas au nom d’une méthode ayant pour préfixe’obtenir'.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

> [!NOTE]
> Cet avertissement peut être exclu si la méthode d’extraction est provoquée par l’implémentation de l’interface IExtenderProvider.

## <a name="example"></a>Exemple
 L’exemple suivant contient une méthode et une propriété qui violent cette règle.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1024 : Utilisez des propriétés quand c’est approprié](../code-quality/ca1024-use-properties-where-appropriate.md)
