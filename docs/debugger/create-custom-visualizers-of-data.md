---
title: Créer des visualiseurs de données personnalisées | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5f505bfa8032b0f7d59f348835e1e4969b2648
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607820"
---
# <a name="create-custom-data-visualizers"></a>Créer des visualiseurs de données personnalisées 
 Un *visualiseur* fait partie de la [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interface utilisateur du débogueur qui affiche une variable ou un objet d’une manière adaptée à son type de données. Par exemple, un visualiseur HTML interprète une chaîne HTML et affiche le résultat, telle qu’affichée dans une fenêtre de navigateur. Un visualiseur bitmap interprète une structure bitmap et affiche le graphique représenté. Certains visualiseurs vous permettent de modifier, ainsi que d’afficher les données.

 Le débogueur [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] comprend six visualiseurs standard. Le texte HTML, XML et JSON visualiseurs fonctionnent sur les objets de chaîne. Le visualiseur de l’arborescence WPF affiche les propriétés d’une arborescence visuelle d’objet WPF. Le visualiseur dataset fonctionne pour les objets DataSet, DataView et DataTable. 

Les visualiseurs plus peuvent être disponibles en téléchargement à partir de Microsoft, des tiers et la Communauté. Vous pouvez également écrire vos propres visualiseurs et les installer dans le [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] débogueur.

Dans le débogueur, un visualiseur est représenté par une icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur"). Vous pouvez sélectionner l’icône dans un **DataTip**, débogueur **espion** fenêtre, ou **Espion express** boîte de dialogue et sélectionnez le visualiseur approprié pour l’objet correspondant.

## <a name="write-custom-visualizers"></a>Écrire les visualiseurs personnalisés

 > [!NOTE]
 > Pour créer un visualiseur personnalisé pour le code natif, consultez le [visualiseur du débogueur natif SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) exemple. Les visualiseurs personnalisés ne sont pas pris en charge pour les applications 8.x UWP et Windows.

Vous pouvez écrire un visualiseur personnalisé pour un objet de toute classe managée à l’exception de <xref:System.Object> et <xref:System.Array>.  
  
L'architecture d'un visualiseur du débogueur comporte deux parties :  
  
- Le *côté débogueur* s’exécute dans le débogueur Visual Studio et crée et affiche l’interface utilisateur du visualiseur.  
  
- Le *côté programme débogué* s’exécute dans le processus de débogage de Visual Studio (le *programme débogué*). L’objet de données à visualiser (par exemple, il s’agit d’un objet String) existe dans le processus du programme débogué. Le côté programme débogué envoie l’objet vers le côté débogueur, qui l’affiche dans l’interface utilisateur que vous créez.  

Le côté débogueur reçoit l’objet de données à partir d’un *fournisseur d’objets* qui implémente le <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interface. Le côté programme débogué envoie l’objet via le *source de l’objet*, qui est dérivée de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. 

Le fournisseur d’objets peut également renvoyer des données à la source de l’objet, qui vous permet d’écrire un visualiseur qui peut modifier des données. Vous substituez le fournisseur d’objets pour communiquer avec l’évaluateur d’expression et de la source de l’objet.  
  
Le côté programme débogué et le côté débogueur communiquent entre eux via <xref:System.IO.Stream> méthodes qui sérialisent les données de l’objet dans un <xref:System.IO.Stream> et désérialiser les <xref:System.IO.Stream> dans un objet de données.  

Vous pouvez écrire un visualiseur pour un type générique uniquement si le type est un type ouvert. Cette restriction est identique à la restriction qui s'applique lorsque vous utilisez l'attribut `DebuggerTypeProxy`. Pour plus d’informations, consultez [utiliser l’attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
Les visualiseurs personnalisés peuvent avoir des exigences en matière de sécurité. Consultez [considérations de sécurité visualiseur](../debugger/visualizer-security-considerations.md).  
  
La procédure suivante donne une vue d’ensemble de la création du visualiseur. Pour obtenir des instructions détaillées, consultez [procédure pas à pas : écrire un visualiseur en C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) ou [procédure pas à pas : écrire un visualiseur en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).  
  
### <a name="to-create-the-debugger-side"></a>Pour créer le côté débogueur  
  
Pour créer l’interface utilisateur du visualiseur côté débogueur, vous créez une classe qui hérite de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>et remplacer le <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> méthode pour afficher l’interface. Vous pouvez utiliser <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> pour afficher des formulaires, des boîtes de dialogue et des contrôles Windows dans votre visualiseur.  
  
1.  Utilisez les méthodes <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> pour obtenir l'objet visualisé côté débogueur.  
  
1.  Créez une classe qui hérite de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
1.  Substituez la méthode <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> pour afficher votre interface. Utilisez <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> méthodes pour afficher des formulaires Windows, les boîtes de dialogue et les contrôles dans votre interface.  
  
4.  Appliquer <xref:System.Diagnostics.DebuggerVisualizerAttribute>, en lui attribuant le visualiseur pour afficher (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Pour créer le côté élément débogué  
  
Vous spécifiez le code côté programme débogué à l’aide de la <xref:System.Diagnostics.DebuggerVisualizerAttribute>.  
  
1.  Appliquez <xref:System.Diagnostics.DebuggerVisualizerAttribute>, en lui affectant un visualiseur (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) et une source d'objet (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Si vous omettez la source d’objet, le visualiseur utilise une source d’objet par défaut.  
  
1.  Pour permettre le visualiseur à modifier, ainsi que d’afficher les objets de données, substituez le `TransferData` ou `CreateReplacementObject` méthodes à partir de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="see-also"></a>Voir aussi
  
 [Procédure pas à pas : écrire un visualiseur en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Procédure pas à pas : écrire un visualiseur en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Guide pratique pour installer un visualiseur](../debugger/how-to-install-a-visualizer.md)  
  
 [Guide pratique pour tester et déboguer un visualiseur](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Informations de référence sur l’API du visualiseur](../debugger/visualizer-api-reference.md)  
  
 [Afficher les données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)