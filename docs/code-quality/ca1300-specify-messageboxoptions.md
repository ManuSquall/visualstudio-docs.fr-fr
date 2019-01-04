---
title: 'CA1300 : Spécifier MessageBoxOptions'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6b72d40bbb2f83eeb8a402b2d389a941f64bfef2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845374"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300 : Spécifier MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode appelle une surcharge de la <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> méthode qui n’accepte pas un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argument.

## <a name="rule-description"></a>Description de la règle

Pour afficher une boîte de message correctement pour les cultures qui utilisent un ordre de lecture de droite à gauche, passer le [MessageBoxOptions.RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) et [MessageBoxOptions.RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) champs à la <xref:System.Windows.Forms.MessageBox.Show%2A> méthode. Examiner le <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> propriété du contrôle conteneur pour déterminer s’il faut utiliser un ordre de lecture de droite à gauche.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appelez une surcharge de la <xref:System.Windows.Forms.MessageBox.Show%2A> méthode qui prend un <xref:System.Windows.Forms.MessageBoxOptions> argument.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle lorsque la bibliothèque de code n’est pas localisée pour une culture qui utilise un ordre de lecture de droite à gauche.

## <a name="example"></a>Exemple

L’exemple suivant montre une méthode qui affiche une boîte de message comportant des options qui conviennent à l’ordre de lecture de la culture. Un fichier de ressources, ce qui n’est pas visible, est requis pour générer l’exemple. Suivez les commentaires dans l’exemple pour générer l’exemple sans fichier de ressources et à tester la fonctionnalité de droite à gauche.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ressources dans les applications de bureau (.NET Framework)](/dotnet/framework/resources/index)