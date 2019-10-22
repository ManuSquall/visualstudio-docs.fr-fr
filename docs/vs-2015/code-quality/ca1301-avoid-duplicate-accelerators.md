---
title: 'CA1301 : éviter les accélérateurs en double | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 647fef2968971cddb6a14cc19e53eed979b9c151
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661516"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301 : Éviter les accélérateurs en double
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type étend <xref:System.Windows.Forms.Control?displayProperty=fullName> et contient au moins deux contrôles de niveau supérieur qui ont des clés d’accès identiques stockées dans un fichier de ressources.

## <a name="rule-description"></a>Description de la règle
 Une touche d'accès rapide, également connue sous le nom d'accélérateur, autorise l'accès à un contrôle par le biais du clavier, à l'aide de la touche ALT. Lorsque plusieurs contrôles présentent des touches d'accès rapide en doublon, le comportement de ces dernières n'est pas correctement défini. L’utilisateur peut ne pas être en mesure d’accéder au contrôle souhaité à l’aide de la clé d’accès et un contrôle autre que celui prévu peut être activé.

 L’implémentation actuelle de cette règle ignore les éléments de menu. Toutefois, les éléments de menu du même sous-menu ne doivent pas avoir des clés d’accès identiques.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, définissez des clés d’accès uniques pour tous les contrôles.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une forme minimale qui contient deux contrôles qui ont des clés d’accès identiques. Les clés sont stockées dans un fichier de ressources, qui n’est pas affiché ; Toutefois, leurs valeurs apparaissent dans les lignes commentées `checkBox.Text`. Le comportement des accélérateurs dupliqués peut être examiné en échangeant les lignes `checkBox.Text` avec les équivalents commentés. Toutefois, dans ce cas, l’exemple ne génère pas d’avertissement à partir de la règle.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Voir aussi
 [ressources de <xref:System.Resources.ResourceManager?displayProperty=fullName> dans les applications de bureau](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
