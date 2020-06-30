---
title: 'CA1040 : Évitez les interfaces vides | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ef6dc666cbc3c26d58358c9b59264f93a7bf184
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548250"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040 : Éviter les interfaces vides
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 L’interface ne déclare aucun membre ni n’implémente plusieurs autres interfaces.

## <a name="rule-description"></a>Description de la règle
 Les interfaces définissent des membres qui fournissent un comportement ou un contrat d'utilisation. Les fonctionnalités décrites par l'interface peuvent être adoptées par tout type, indépendamment de l'endroit où le type figure dans la hiérarchie d'héritage. Un type implémente une interface en fournissant des implémentations pour les membres de celle-ci. Une interface vide ne définit aucun membre. Par conséquent, il ne définit pas un contrat qui peut être implémenté.

 Si votre conception comprend des interfaces vides que les types sont censés implémenter, vous utilisez probablement une interface comme marqueur ou un moyen d’identifier un groupe de types. Si cette identification se produit au moment de l’exécution, la bonne façon d’y parvenir consiste à utiliser un attribut personnalisé. Utilisez la présence ou l’absence de l’attribut, ou les propriétés de l’attribut, pour identifier les types cibles. Si l’identification doit se produire au moment de la compilation, il est acceptable d’utiliser une interface vide.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Supprimez l’interface ou ajoutez des membres à celle-ci. Si l’interface vide est utilisée pour étiqueter un ensemble de types, remplacez l’interface par un attribut personnalisé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle quand l’interface est utilisée pour identifier un ensemble de types au moment de la compilation.

## <a name="example"></a>Exemple
 L’exemple suivant illustre une interface vide.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
