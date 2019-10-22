---
title: 'Ca1050 : déclarer des types dans des espaces de noms | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c56de70daeabd05215f68024339d5855686d529b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653836"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050 : Déclarer les types dans des espaces de noms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé est défini en dehors de la portée d’un espace de noms nommé.

## <a name="rule-description"></a>Description de la règle
 Les types sont déclarés dans les espaces de noms pour empêcher les conflits de noms, et comme un moyen d’organiser les types associés dans une hiérarchie d’objets. Les types qui se trouvent en dehors de tout espace de noms nommé se trouvent dans un espace de noms global qui ne peut pas être référencé dans le code.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, placez le type dans un espace de noms.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Bien que vous n’ayez jamais à supprimer un avertissement de cette règle, il est possible de le faire lorsque l’assembly ne sera jamais utilisé avec d’autres assemblys.

## <a name="example"></a>Exemple
 L’exemple suivant montre une bibliothèque dont le type est déclaré de manière incorrecte en dehors d’un espace de noms, et un type qui a le même nom déclaré dans un espace de noms.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Exemple
 L’application suivante utilise la bibliothèque qui a été définie précédemment. Notez que le type déclaré en dehors d’un espace de noms est créé lorsque le nom `Test` n’est pas qualifié par un espace de noms. Notez également que pour accéder au type `Test` dans `Goodspace`, le nom de l’espace de noms est requis.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
