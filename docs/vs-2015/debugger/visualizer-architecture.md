---
title: Architecture du visualiseur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82dd990a44984d2e3cc1c84244fbe07ea519fdfc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189033"
---
# <a name="visualizer-architecture"></a>Architecture d'un visualiseur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'architecture d'un visualiseur du débogueur comporte deux parties :  
  
- Le *côté débogueur* s’exécute dans le débogueur Visual Studio. Le code côté débogueur crée et affiche l'interface utilisateur de votre visualiseur.  
  
- Le *côté élément débogué* s’exécute dans le processus que Visual Studio débogue (l’*élément débogué*).  
  
  Un visualiseur est un composant du débogueur qui permet à ce dernier d’afficher (de *visualiser*) le contenu d’un objet de données sous une forme explicite et compréhensible. Certains visualiseurs prennent également en charge la modification de l'objet de données. En écrivant des visualiseurs personnalisés, vous pouvez étendre les fonctionnalités du débogueur afin de gérer vos propres types de données personnalisés.  
  
  L’objet de données à visualiser réside dans le processus que vous déboguez (processus de l’*élément débogué*). L'interface utilisateur qui affiche les données est créée dans le processus du débogueur Visual Studio :  
  
|Processus du débogueur|Processus du programme débogué|  
|----------------------|----------------------|  
|Interface utilisateur du débogueur (DataTips, fenêtre Espion, Espion express)|Objet de données à visualiser|  
  
 Pour visualiser l'objet de données dans l'interface du débogueur, vous avez besoin de code afin d'établir une communication entre les deux processus. Par conséquent, l’architecture du visualiseur se compose de deux parties : code *côté débogueur* et code *côté élément débogué*.  
  
 Le code côté débogueur crée sa propre interface utilisateur, laquelle peut être appelée à partir de l'interface du débogueur, par exemple un DataTip, la fenêtre Espion ou l'Espion express. L'interface du visualiseur est créée via la classe <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> et l'interface <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>. Comme toutes les API du visualiseur, DialogDebuggerVisualizer et IDialogVisualizerService se trouvent dans l'espace de noms <xref:Microsoft.VisualStudio.DebuggerVisualizers>.  
  
|Côté débogueur|Côté élément débogué|  
|-------------------|-------------------|  
|Classe DialogDebuggerVisualizer<br /><br /> Interface IDialogVisualizerService|Objet de données|  
  
 L'interface utilisateur obtient les données à visualiser à partir d'un fournisseur d'objets, qui existe côté débogueur :  
  
|Côté débogueur|Côté élément débogué|  
|-------------------|-------------------|  
|Classe DialogDebuggerVisualizer<br /><br /> Interface IDialogVisualizerService|Objet de données|  
|Fournisseur d'objets (implémente <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||  
  
 Il y a un objet correspondant côté programme débogué, que l'on appelle source de l'objet :  
  
|Côté débogueur|Côté élément débogué|  
|-------------------|-------------------|  
|Classe DialogDebuggerVisualizer<br /><br /> Interface IDialogVisualizerService|Objet de données|  
|Fournisseur d'objets (implémente <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Source de l'objet (dérivée de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|  
  
 Le fournisseur d'objets fournit les données d'objet qui seront visualisées via l'interface utilisateur du visualiseur. Le fournisseur d'objets obtient les données d'objet à partir de la source de l'objet. Le fournisseur d'objets et la source de l'objet fournissent des API pour permettre la communication des données d'objet entre le débogueur et le programme débogué.  
  
 Chaque visualiseur doit obtenir l'objet de données à visualiser. Le tableau suivant affiche les API correspondantes utilisées à cet effet par le fournisseur d'objets et la source de l'objet :  
  
|Fournisseur d'objets|Source de l'objet|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> Ou<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 Notez que le fournisseur d'objets peut utiliser <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> ou <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Les deux API entraînent l'appel de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> sur la source de l'objet. Un appel à <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> remplit un [System. IO. Stream] (<!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->), qui représente une forme sérialisée de l’objet qui est visualisé.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> désérialise les données sous forme d’objet que vous pouvez ensuite afficher dans l’interface utilisateur créée à l’aide de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> remplit les données en tant que données brutes <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, que vous devez désérialiser vous-même. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> fonctionne en appelant <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> pour accéder au sérialisé <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, puis à désérialiser les données. Utilisez <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> lorsque l'objet n'est pas sérialisable par le .NET et qu'il requiert une sérialisation personnalisée. Dans ce cas, vous devez également substituer la méthode <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName>.  
  
 Si vous créez un visualiseur en lecture seule, une communication unidirectionnelle avec <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> ou <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> suffit. Si vous créez un visualiseur qui prend en charge la modification des objets de données, vous devez effectuer des tâches supplémentaires. Vous devez également être en mesure de renvoyer un objet de données du fournisseur d'objets à la source de l'objet. Le tableau suivant affiche les API utilisées à cet effet par le fournisseur d'objets et la source de l'objet :  
  
|Fournisseur d'objets|Source de l'objet|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> Ou<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 Notez à nouveau qu'il y a deux API utilisables par le fournisseur d'objets. Les données sont toujours envoyées du fournisseur d’objets à la source de l’objet en tant que <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, mais <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> requiert la sérialisation de l’objet dans un <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> test.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> prend un objet que vous fournissez, le sérialise dans un <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  -->, puis appelle <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> pour envoyer le <!-- TODO: review code entity reference <xref:assetId:///System.IO.Stream?qualifyHint=False&amp;autoUpgrade=True>  --> à <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.  
  
 L’utilisation de l’une des méthodes Replace entraîne la création d’un objet de données dans l’élément débogué, qui remplace l’objet visualisé. Si vous souhaitez modifier le contenu de l'objet d'origine sans le remplacer, utilisez l'une des méthodes Transfer figurant dans le tableau ci-après. Ces API transfèrent les données dans les deux sens et en même temps, sans remplacer l'objet visualisé :  
  
|Fournisseur d'objets|Source de l'objet|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> Ou<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : écrire un visualiseur](../debugger/how-to-write-a-visualizer.md)   
 [Procédure pas à pas : écriture d’un visualiseur en C #](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Procédure pas à pas : écriture d’un visualiseur dans Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Procédure pas à pas : écriture d’un visualiseur dans Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Considérations sur la sécurité du visualiseur](../debugger/visualizer-security-considerations.md)
