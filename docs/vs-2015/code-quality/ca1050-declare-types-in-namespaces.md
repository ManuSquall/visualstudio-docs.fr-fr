---
title: 'CA1050 : Déclarer les types dans les espaces de noms | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ef0559cc727e7ffd667ee72ebe241a958fa57450
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588102"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050 : Déclarer les types dans des espaces de noms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1050 : déclarez les types dans les espaces de noms](https://docs.microsoft.com/visualstudio/code-quality/ca1050-declare-types-in-namespaces).

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé est défini en dehors de l’étendue d’un espace de noms nommé.

## <a name="rule-description"></a>Description de la règle
 Les types sont déclarés dans les espaces de noms pour empêcher les collisions de nom et comme un moyen d’organiser les types associés dans une hiérarchie d’objets. Les types qui sont en dehors de tout espace de noms nommé sont dans un espace de noms global qui ne peut pas être référencé dans le code.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, placez le type dans un espace de noms.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Bien que vous ayez jamais supprimer un avertissement de cette règle, il est possible pour ce faire, lorsque l’assembly ne sera jamais utilisé avec d’autres assemblys.

## <a name="example"></a>Exemple
 L’exemple suivant montre une bibliothèque qui a un type déclaré incorrectement hors d’un espace de noms et un type qui a le même nom déclaré dans un espace de noms.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Exemple
 L’application suivante utilise la bibliothèque qui a été définie précédemment. Notez que le type qui est déclaré en dehors d’un espace de noms est créé lorsque le nom `Test` n’est pas qualifié par un espace de noms. Notez également que pour accéder à la `Test` tapez `Goodspace`, le nom de l’espace de noms est obligatoire.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]



