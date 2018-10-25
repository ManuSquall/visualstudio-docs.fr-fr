---
title: 'CA1301 : Éviter les accélérateurs en double | Microsoft Docs'
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
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 92c5baefff76626a42553d6ba5380fd07448b109
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886644"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301 : Éviter les accélérateurs en double
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type étend <xref:System.Windows.Forms.Control?displayProperty=fullName> et contient deux ou plusieurs contrôles de niveau supérieur qui ont des clés d’accès identiques qui sont stockés dans un fichier de ressources.

## <a name="rule-description"></a>Description de la règle
 Une touche d'accès rapide, également connue sous le nom d'accélérateur, autorise l'accès à un contrôle par le biais du clavier, à l'aide de la touche ALT. Lorsque plusieurs contrôles présentent des touches d'accès rapide en doublon, le comportement de ces dernières n'est pas correctement défini. L’utilisateur ne peut pas être en mesure d’accéder au contrôle prévu à l’aide de la clé d’accès et un contrôle autre que celui qui est prévu peut être activé.

 L’implémentation actuelle de cette règle ignore les éléments de menu. Toutefois, les éléments de menu dans le même sous-menu ne doivent pas avoir les clés d’accès identiques.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, définissez les clés d’accès unique pour tous les contrôles.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant présente un formulaire minimal qui contient deux contrôles qui ont des clés d’accès identiques. Les clés sont stockées dans un fichier de ressources, ce qui n’est pas visible ; Toutefois, leurs valeurs s’affichent dans les out `checkBox.Text` lignes. Le comportement d’accélérateurs en doublon peut être examiné en échangeant les `checkBox.Text` lignes avec leurs équivalents commentés. Toutefois, dans ce cas, l’exemple ne génère pas un avertissement à partir de la règle.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Ressources dans les applications de bureau](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



