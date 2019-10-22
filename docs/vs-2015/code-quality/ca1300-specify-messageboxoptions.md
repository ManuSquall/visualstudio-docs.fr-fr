---
title: 'CA1300 : spécifier MessageBoxOptions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3e21866fce69f768d927882d3ddd47ae3e431265
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663609"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300 : Spécifier MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode appelle une surcharge de la méthode <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> qui ne prend pas d’argument <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 Pour afficher correctement une boîte de message pour les cultures qui utilisent un ordre de lecture de droite à gauche, les membres <xref:System.Windows.Forms.MessageBoxOptions> et <xref:System.Windows.Forms.MessageBoxOptions> de l’énumération <xref:System.Windows.Forms.MessageBoxOptions> doivent être passés à la méthode <xref:System.Windows.Forms.MessageBox.Show%2A>. Examinez la propriété <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> du contrôle conteneur pour déterminer s’il faut utiliser un ordre de lecture de droite à gauche.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez une surcharge de la méthode <xref:System.Windows.Forms.MessageBox.Show%2A> qui accepte un argument <xref:System.Windows.Forms.MessageBoxOptions>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque la bibliothèque de code n’est pas localisée pour une culture qui utilise un ordre de lecture de droite à gauche.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui affiche une boîte de message qui contient des options appropriées pour l’ordre de lecture de la culture. Un fichier de ressources, qui n’est pas affiché, est requis pour générer l’exemple. Suivez les commentaires de l’exemple pour générer l’exemple sans fichier de ressources et pour tester la fonctionnalité de droite à gauche.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Voir aussi
 [ressources de <xref:System.Resources.ResourceManager?displayProperty=fullName> dans les applications de bureau](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
