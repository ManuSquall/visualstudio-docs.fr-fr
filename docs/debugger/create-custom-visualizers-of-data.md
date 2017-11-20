---
title: "Créer des visualiseurs personnalisés de données | Documents Microsoft"
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.visualizer.troubleshoot
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
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec31ea837c78fc1d47c3df02d129ac3c5f4f3657
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="create-custom-visualizers-of-data"></a>Créer des visualiseurs personnalisés de données
 Les visualiseurs sont des composants de la [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interface utilisateur du débogueur. A *visualiseur* crée une boîte de dialogue ou une autre interface pour afficher une variable ou un objet d’une manière qui convient à son type de données. Par exemple, un visualiseur HTML interprète une chaîne HTML et affiche le résultat tel qu'il apparaîtrait dans une fenêtre du navigateur ; un visualiseur bitmap interprète une structure bitmap et affiche le graphique représenté. Certains visualiseurs vous permettent de modifier et de consulter les données.

 Le débogueur [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] comprend six visualiseurs standard. Il s’agit de texte, les visualiseurs HTML, XML et JSON, qui fonctionnent sur les objets de chaîne ; le visualiseur de l’arborescence WPF, pour afficher les propriétés d’une arborescence d’objets visual WPF ; et du visualiseur dataset, utilisé pour les objets DataSet, DataView et DataTable. Des visualiseurs supplémentaires sont disponibles auprès de tiers et de la communauté. Vous pourrez en télécharger plus tard chez Microsoft Corporation. De plus, vous pouvez écrire vos propres visualiseurs et les installer dans le débogueur [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

 > [!NOTE]
 > Pour créer un visualiseur personnalisé pour le code natif, consultez le [visualiseur du débogueur natif SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) exemple. Dans les applications UWP et Windows 8.x, les visualiseurs personnalisés ne sont pas pris en charge.

 Dans le débogueur, les visualiseurs sont représentés par une icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur"). Lorsque vous voyez l’icône de loupe dans un **DataTip**, dans une fenêtre du débogueur, comme la **espion** fenêtre, ou dans le **Espion express** boîte de dialogue, vous pouvez cliquer sur la loupe pour sélectionner un visualiseur approprié au type de données de l’objet correspondant.

## <a name="overview-of-custom-visualizers"></a>Vue d’ensemble des visualiseurs personnalisés

Vous pouvez écrire un visualiseur personnalisé pour un objet de toute classe managée à l'exception de <xref:System.Object> ou <xref:System.Array>.  
  
 L'architecture d'un visualiseur du débogueur comporte deux parties :  
  
-   Le *côté débogueur* s’exécute dans le débogueur Visual Studio. Le code côté débogueur crée et affiche l'interface utilisateur de votre visualiseur.  
  
-   Le *côté programme débogué* s’exécute dans le processus que Visual Studio débogue (le *programme débogué*).  
  
 L’objet de données que vous souhaitez visualiser (un objet String, par exemple) existe dans le processus de l’élément débogué. Le côté élément débogué doit donc envoyer cet objet de données au côté débogueur qui peut alors l’afficher à l’aide d’une interface utilisateur que vous créez.  
  
 Le côté débogueur reçoit cet objet de données à visualiser à partir d’un *fournisseur d’objets* qui implémente le <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interface. Le côté programme débogué envoie l’objet de données via le *source de l’objet*, qui est dérivée de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Le fournisseur d'objets peut également renvoyer des données à la source d'objet, vous permettant d'écrire un visualiseur capable de modifier et d'afficher des données. Le fournisseur d'objets peut être substitué pour parler à l'évaluateur d'expression et, par conséquent, à la source de l'objet.  
  
 Le côté programme débogué et le côté débogueur communiquent entre eux via <xref:System.IO.Stream>. Des méthodes sont fournies pour sérialiser un objet de données dans un <xref:System.IO.Stream> et désérialiser le <xref:System.IO.Stream> dans un objet de données.  
  
 Le code côté programme débogué est spécifié à l'aide de l'attribut DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
 Pour créer l'interface utilisateur du visualiseur côté débogueur, vous devez créer une classe qui hérite de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> et substituer la méthode <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> pour afficher l'interface.  
  
 Vous pouvez utiliser <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> pour afficher des formulaires, des boîtes de dialogue et des contrôles Windows à partir de votre visualiseur.  
  
 La prise en charge des types génériques est limitée. Vous pouvez écrire un visualiseur pour une cible qui est un type générique uniquement si le type générique est un type ouvert. Cette restriction est identique à la restriction qui s'applique lorsque vous utilisez l'attribut `DebuggerTypeProxy`. Pour plus d’informations, consultez [DebuggerTypeProxy (attribut) à l’aide de](../debugger/using-debuggertypeproxy-attribute.md).  
  
 Les visualiseurs personnalisés peuvent avoir des exigences en matière de sécurité. Consultez [considérations de sécurité visualiseur](../debugger/visualizer-security-considerations.md).  
  
 Les procédures ci-après fournissent une vue d'ensemble de la marche à suivre pour créer un visualiseur. Pour une explication plus détaillée, consultez [procédure pas à pas : écriture d’un visualiseur en c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Pour créer le côté débogueur  
  
1.  Utilisez les méthodes <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> pour obtenir l'objet visualisé côté débogueur.  
  
2.  Créez une classe qui hérite de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Substituez la méthode <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> pour afficher votre interface. Les méthodes <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> vous permettent d'afficher des formulaires, des boîtes de dialogue et des contrôles Windows dans le cadre de votre interface.  
  
4.  Appliquez <xref:System.Diagnostics.DebuggerVisualizerAttribute>, en lui affectant un visualiseur (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Pour créer le côté débogué  
  
1.  Appliquez <xref:System.Diagnostics.DebuggerVisualizerAttribute>, en lui affectant un visualiseur (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) et une source d'objet (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Si vous omettez la source de l'objet, une source d'objet par défaut sera utilisée.  
  
2.  Si vous souhaitez que votre visualiseur modifie et affiche des objets de données, substituez les méthodes `TransferData` ou `CreateReplacementObject` de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="in-this-section"></a>Dans cette section
  
 [Procédure pas à pas : écriture d’un visualiseur en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Procédure pas à pas : écriture d’un visualiseur en Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Guide pratique pour installer un visualiseur](../debugger/how-to-install-a-visualizer.md)  
  
 [Guide pratique pour tester et déboguer un visualiseur](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Informations de référence sur l’API du visualiseur](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Afficher les données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)