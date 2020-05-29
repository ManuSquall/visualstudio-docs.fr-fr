---
title: Créer des visualiseurs de données personnalisés | Microsoft Docs
ms.date: 05/27/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c16b603f1c38eeb3e71718937e7c669ae8ebc9
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184547"
---
# <a name="create-custom-data-visualizers"></a>Créer des visualiseurs de données personnalisés
 Un *visualiseur* fait partie de l' [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interface utilisateur du débogueur qui affiche une variable ou un objet de manière appropriée à son type de données. Par exemple, un visualiseur HTML interprète une chaîne HTML et affiche le résultat tel qu’il apparaîtrait dans une fenêtre de navigateur. Un visualiseur bitmap interprète une structure bitmap et affiche le graphique qu’il représente. Certains visualiseurs vous permettent de modifier et d’afficher les données.

 Le débogueur [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] comprend six visualiseurs standard. Les visualiseurs de texte, HTML, XML et JSON fonctionnent sur les objets String. Le visualiseur de l’arborescence WPF affiche les propriétés d’une arborescence d’éléments visuels d’objets WPF. Le visualiseur de DataSet fonctionne pour les objets DataSet, DataView et DataTable.

D’autres visualiseurs peuvent être téléchargés à partir de Microsoft, de tiers et de la communauté. Vous pouvez également écrire vos propres visualiseurs et les installer dans le [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] débogueur.

Dans le débogueur, un visualiseur est représenté par une icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icône de visualiseur"). Vous pouvez sélectionner l’icône dans un **DataTip**, dans la fenêtre **Espion** du débogueur ou dans la boîte de dialogue **Espion express** , puis sélectionner le visualiseur approprié pour l’objet correspondant.

## <a name="write-custom-visualizers"></a>Écrire des visualiseurs personnalisés

 > [!NOTE]
 > Pour créer un visualiseur personnalisé pour le code natif, consultez l’exemple du [visualiseur du débogueur natif SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) . Les visualiseurs personnalisés ne sont pas pris en charge pour les applications UWP et Windows 8. x.

Vous pouvez écrire un visualiseur personnalisé pour un objet de toute classe managée à l’exception de <xref:System.Object> et <xref:System.Array>.

L'architecture d'un visualiseur du débogueur comporte deux parties :

- Le *côté débogueur* s’exécute dans le débogueur Visual Studio et crée et affiche l’interface utilisateur du visualiseur.

- Le *côté élément débogué* s’exécute dans le processus que Visual Studio débogue (l’*élément débogué*). L’objet de données à visualiser (par exemple, un objet String) existe dans le processus du programme débogué. Le côté programme débogué envoie l’objet au côté débogueur, qui l’affiche dans l’interface utilisateur que vous créez.

Le côté débogueur reçoit l’objet de données d’un *fournisseur d’objets* qui implémente l' <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interface. Le côté programme débogué envoie l’objet via la source de l' *objet*, dérivée de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

Le fournisseur d’objets peut également renvoyer des données à la source de l’objet, ce qui vous permet d’écrire un visualiseur capable de modifier les données. Vous substituez le fournisseur d’objets pour communiquer avec l’évaluateur d’expression et la source de l’objet.

Le côté débogué et le côté débogueur communiquent entre eux par le biais de <xref:System.IO.Stream> méthodes qui sérialisent un objet de données dans un <xref:System.IO.Stream> objet et désérialisent le <xref:System.IO.Stream> retour dans un objet de données.

Vous pouvez écrire un visualiseur pour un type générique uniquement si le type est un type ouvert. Cette restriction est identique à la restriction qui s'applique lorsque vous utilisez l'attribut `DebuggerTypeProxy`. Pour plus d’informations, consultez [utiliser l’attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

Les visualiseurs personnalisés peuvent avoir des exigences en matière de sécurité. Consultez [Considérations sur la sécurité du visualiseur](../debugger/visualizer-security-considerations.md).

Les étapes suivantes fournissent une vue d’ensemble globale de la création du visualiseur. Pour obtenir des instructions détaillées, consultez [procédure pas à pas : écrire un visualiseur en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) ou [procédure pas à pas : écrire un visualiseur dans Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Pour créer le côté débogueur

Pour créer l’interface utilisateur du visualiseur côté débogueur, vous créez une classe qui hérite de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> et substituez la <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> méthode pour afficher l’interface. Vous pouvez utiliser <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> pour afficher des Windows Forms, des boîtes de dialogue et des contrôles dans votre visualiseur.

1. Utilisez les méthodes <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> pour obtenir l'objet visualisé côté débogueur.

1. Créez une classe qui hérite de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.

1. Substituez la méthode <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> pour afficher votre interface. Utilisez des <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> méthodes pour afficher des Windows Forms, des boîtes de dialogue et des contrôles dans votre interface.

4. Appliquez <xref:System.Diagnostics.DebuggerVisualizerAttribute> , en lui donnant le visualiseur à afficher ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ).

### <a name="to-create-the-visualizer-object-source-for-the-debuggee-side"></a>Pour créer la source de l’objet du visualiseur pour le côté débogué

Vous spécifiez le type à visualiser (la source de l’objet côté débogué) à l’aide <xref:System.Diagnostics.DebuggerVisualizerAttribute> de dans le code côté débogueur.

1. Dans le code côté débogueur, modifiez le <xref:System.Diagnostics.DebuggerVisualizerAttribute> , en lui donnant la source de l’objet ( <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> ). La `Target` propriété définit la source de l’objet. Si vous omettez la source de l’objet, le visualiseur utilise une source d’objet par défaut.

1. Pour permettre au visualiseur de modifier et d’afficher des objets de données, substituez les `TransferData` `CreateReplacementObject` méthodes ou de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Écrire un visualiseur dans C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Procédure pas à pas : Écrire un visualiseur dans Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Guide pratique pour installer un visualiseur](../debugger/how-to-install-a-visualizer.md)
- [Guide pratique pour tester et déboguer un visualiseur](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Informations de référence sur l’API du visualiseur](../debugger/visualizer-api-reference.md)
- [Afficher les données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)