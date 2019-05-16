---
title: 'CA1300 : Spécifier MessageBoxOptions | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7d24298821895a8bbbe9d3743556007abe17c72
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686873"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300 : Spécifier MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode appelle une surcharge de la <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> méthode qui n’accepte pas un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argument.

## <a name="rule-description"></a>Description de la règle
 Pour afficher une boîte de message correctement pour les cultures qui utilisent un ordre de lecture de droite à gauche, le <xref:System.Windows.Forms.MessageBoxOptions> et <xref:System.Windows.Forms.MessageBoxOptions> membres de la <xref:System.Windows.Forms.MessageBoxOptions> énumération doit être passée à la <xref:System.Windows.Forms.MessageBox.Show%2A> (méthode). Examiner le <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> propriété du contrôle conteneur pour déterminer s’il faut utiliser un ordre de lecture de droite à gauche.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez une surcharge de la <xref:System.Windows.Forms.MessageBox.Show%2A> méthode qui prend un <xref:System.Windows.Forms.MessageBoxOptions> argument.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle lorsque la bibliothèque de code n’est pas localisée pour une culture qui utilise un ordre de lecture de droite à gauche.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui affiche une boîte de message comportant des options qui conviennent à l’ordre de lecture de la culture. Un fichier de ressources, ce qui n’est pas visible, est requis pour générer l’exemple. Suivez les commentaires dans l’exemple pour générer l’exemple sans fichier de ressources et à tester la fonctionnalité de droite à gauche.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Ressources dans les applications de bureau](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
