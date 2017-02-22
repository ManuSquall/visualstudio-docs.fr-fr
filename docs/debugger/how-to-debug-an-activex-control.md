---
title: "Comment&#160;: d&#233;boguer un contr&#244;le ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogage du conteneur de contrôle ActiveX (Visual Studio)"
  - "contrôles ActiveX, débogage"
  - "conteneurs, spécifier pour les sessions de débogage"
  - "contrôles liés aux données, ActiveX"
  - "déboguer des contrôles ActiveX"
  - "conteneur de test"
  - "tester (Visual Studio), contrôles ActiveX"
  - "tester (Visual Studio), conteneurs de test"
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Comment&#160;: d&#233;boguer un contr&#244;le ActiveX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Pour déboguer votre contrôle ActiveX, vous devez spécifier un conteneur \(exécutable\) à utiliser pour l'exécution du contrôle.  
  
### Pour spécifier un conteneur pour une session de débogage  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet.  
  
2.  Dans le menu **Affichage**, choisissez **Pages de propriétés**.  
  
3.  Dans la boîte de dialogue **Pages de propriété de projet**, ouvrez le dossier **Propriétés de configuration** et sélectionnez **Débogage**.  
  
4.  Dans la catégorie **Débogage**, recherchez la propriété **Commande**.  
  
5.  Spécifiez le nom de chemin pour le conteneur.  Par exemple, C:\\Program Files\\Internet Explorer\\IEXPLORE.EXE.  
  
6.  Si vous spécifiez Internet Explorer comme conteneur et que vous utilisez Active Desktop, tapez `/new`  dans la zone **Arguments de la commande**.  
  
7.  Cliquez sur **OK**.  
  
     Si vous ne spécifiez pas un conteneur dans la boîte de dialogue **Pages de propriétés de projet**, vous pourrez spécifier le conteneur lorsque vous commencerez à déboguer.  Lorsque vous sélectionnez une commande d'exécution pour commencer le débogage, la [boîte de dialogue Exécutable pour la session de débogage](../debugger/executable-for-debugging-session-dialog-box.md) s'affiche.  Spécifiez le nom de chemin du conteneur dans la boîte de dialogue.  
  
## Voir aussi  
 [Contrôles ActiveX](/visual-cpp/mfc/activex-controls)   
 [Test des propriétés et des événements avec le conteneur de test](/visual-cpp/mfc/testing-properties-and-events-with-test-container)   
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)