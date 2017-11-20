---
title: "Comment : déboguer un contrôle ActiveX | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 932ccf7bdbea8fa68d0c2883d0ae8fd77eedf5bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-an-activex-control"></a>Comment : déboguer un contrôle ActiveX
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Pour déboguer votre contrôle ActiveX, vous devez spécifier un conteneur (exécutable) à utiliser pour l'exécution du contrôle.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Pour spécifier un conteneur pour une session de débogage  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet.  
  
2.  À partir de la **vue** menu, choisissez **Pages de propriétés**.  
  
3.  Dans le **les Pages de propriétés de projet** boîte de dialogue, ouvrez le **propriétés de Configuration** dossier, puis sélectionnez **débogage**.  
  
4.  Sous le **débogage** catégorie, recherchez le **commande** propriété.  
  
5.  Spécifiez le nom de chemin pour le conteneur. Par exemple, C:\Program Files\Internet Explorer\IEXPLORE.EXE.  
  
6.  Si vous spécifiez Internet Explorer comme conteneur et que vous utilisez Active Desktop, tapez `/new` dans les **Arguments de commande** boîte.  
  
7.  Cliquez sur **OK**.  
  
     Si vous ne spécifiez pas un conteneur dans le **les Pages de propriétés de projet** boîte de dialogue, vous pouvez spécifier le conteneur lorsque vous commencerez le débogage. Lorsque vous sélectionnez une commande d’exécution pour démarrer le débogage, la [exécutable pour la boîte de dialogue de Session de débogage](../debugger/executable-for-debugging-session-dialog-box.md) s’affiche. Spécifiez le nom de chemin du conteneur dans la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX](/cpp/mfc/activex-controls)   
 [Test des propriétés et des événements avec le conteneur de Test](/cpp/mfc/testing-properties-and-events-with-test-container)   
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Débogage dans Visual Studio](../debugger/index.md)  
 [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)