---
title: 'Comment : écrire un visualiseur | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c7f1fa96bba40e5e56ca7f054b683b3243de65b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724897"
---
# <a name="how-to-write-a-visualizer"></a>Comment : écrire un visualiseur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez écrire un visualiseur personnalisé pour un objet de toute classe managée à l'exception de <xref:System.Object> ou <xref:System.Array>.  
  
> [!NOTE]
>  Dans **Store** applications, seul le texte standard, les visualiseurs HTML, XML et JSON sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.  
  
 L'architecture d'un visualiseur du débogueur comporte deux parties :  
  
- Le *côté débogueur* s’exécute dans le débogueur Visual Studio. Le code côté débogueur crée et affiche l'interface utilisateur de votre visualiseur.  
  
- Le *côté programme débogué* s’exécute dans le processus de débogage de Visual Studio (le *programme débogué*).  
  
  L’objet de données que vous souhaitez visualiser (un objet String, par exemple) existe dans le processus de l’élément débogué. Le côté élément débogué doit donc envoyer cet objet de données au côté débogueur qui peut alors l’afficher à l’aide d’une interface utilisateur que vous créez.  
  
  Le côté débogueur reçoit cet objet de données à visualiser à partir d’un *fournisseur d’objets* qui implémente le <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interface. Le côté programme débogué envoie l’objet de données via le *source de l’objet*, qui est dérivée de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Le fournisseur d'objets peut également renvoyer des données à la source d'objet, vous permettant d'écrire un visualiseur capable de modifier et d'afficher des données. Le fournisseur d'objets peut être substitué pour parler à l'évaluateur d'expression et, par conséquent, à la source de l'objet.  
  
  Le côté programme débogué et le côté débogueur communiquent entre eux via <xref:System.IO.Stream>. Des méthodes sont fournies pour sérialiser un objet de données dans un <xref:System.IO.Stream> et désérialiser le <xref:System.IO.Stream> dans un objet de données.  
  
  Le code côté programme débogué est spécifié à l'aide de l'attribut DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
  Pour créer l'interface utilisateur du visualiseur côté débogueur, vous devez créer une classe qui hérite de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> et substituer la méthode <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> pour afficher l'interface.  
  
  Vous pouvez utiliser <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> pour afficher des formulaires, des boîtes de dialogue et des contrôles Windows à partir de votre visualiseur.  
  
  La prise en charge des types génériques est limitée. Vous pouvez écrire un visualiseur pour une cible qui est un type générique uniquement si le type générique est un type ouvert. Cette restriction est identique à la restriction qui s'applique lorsque vous utilisez l'attribut `DebuggerTypeProxy`. Pour plus d’informations, consultez [à l’aide de l’attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
  Les visualiseurs personnalisés peuvent avoir des exigences en matière de sécurité. Consultez [considérations de sécurité visualiseur](../debugger/visualizer-security-considerations.md).  
  
  Les procédures ci-après fournissent une vue d'ensemble de la marche à suivre pour créer un visualiseur. Pour obtenir une explication plus détaillée, consultez [procédure pas à pas : écriture d’un visualiseur en c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Pour créer le côté débogueur  
  
1.  Utilisez les méthodes <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> pour obtenir l'objet visualisé côté débogueur.  
  
2.  Créez une classe qui hérite de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Substituez la méthode <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> pour afficher votre interface. Les méthodes <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> vous permettent d'afficher des formulaires, des boîtes de dialogue et des contrôles Windows dans le cadre de votre interface.  
  
4.  Appliquez <xref:System.Diagnostics.DebuggerVisualizerAttribute>, en lui affectant un visualiseur (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Pour créer le côté débogué  
  
1.  Appliquez <xref:System.Diagnostics.DebuggerVisualizerAttribute>, en lui affectant un visualiseur (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) et une source d'objet (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Si vous omettez la source de l'objet, une source d'objet par défaut sera utilisée.  
  
2.  Si vous souhaitez que votre visualiseur modifie et affiche des objets de données, substituez les méthodes `TransferData` ou `CreateReplacementObject` de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   
 [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)   
 [Comment : tester et déboguer un visualiseur](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Considérations sur la sécurité du visualiseur](../debugger/visualizer-security-considerations.md)



