---
title: "Proc&#233;dure&#160;: d&#233;finir des points d&#39;arr&#234;t dans les workflows (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "points d'arrêt, définir dans les workflows"
  - "débogage de workflows, définir des points d'arrêt"
  - "débogage, définir des points d'arrêt dans les workflows"
  - "workflows, définir des points d'arrêt"
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Proc&#233;dure&#160;: d&#233;finir des points d&#39;arr&#234;t dans les workflows (h&#233;rit&#233;e)
Cette rubrique décrit comment définir des points d'arrêt dans les applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] générées à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité.Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque votre application [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] doit cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Lorsque vous utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] pour générer une application [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)], vous pouvez définir des points d'arrêt en code C\# et Visual Basic, tout comme vous le faites dans Visual Studio.Comme prévu, l'exécution de workflow s'arrête à chaque point d'arrêt que vous définissez.  
  
 Un point d'arrêt a trois états : *En attente*, *Dépendant*, et *Erreur*.Lorsque vous définissez un point d'arrêt, il porte l'état En attente et il est représenté par une icône rouge creuse.Lorsque l'exécution a chargé le type de workflow, il adopte l'état Dépendant et est représenté par une icône rouge unie.Si vous spécifiez un format incorrect pour le point d'arrêt \(en indiquant un nom d'activité incorrect, par exemple\), un message d'erreur apparaît.Le point d'arrêt est ajouté à la fenêtre de points d'arrêt, mais il est marqué d'un petit « x ».  
  
 Vous pouvez définir des points d'arrêt sur une activité de l'aire de conception de workflow comme suit :  
  
-   Cliquez avec le bouton droit sur l'activité et sélectionnez **Point d'arrêt \\ Insérer le point d'arrêt**.  
  
-   Sélectionnez l'activité et appuyez sur F9.  
  
-   Dans le menu **Débogage**, sélectionnez la commande **Nouveau point d'arrêt**.  
  
     Vous pouvez également utiliser cette option pour définir un nouveau point d'arrêt pendant le débogage, lorsque le débogueur s'arrête à un point d'arrêt.  
  
    > [!NOTE]
    >  La définition des points d'arrêt sur les workflows appelés n'est pas prise en charge.  
  
### Pour définir un point d'arrêt à l'aide de l'option Nouveau point d'arrêt du menu Débogage  
  
1.  Dans le menu **Débogage**, sélectionnez **Nouveau point d'arrêt**.  
  
2.  Cliquez sur **Interrompre à la fonction**.  
  
     La boîte de dialogue **Nouveau point d'arrêt** s'affiche.  
  
3.  Spécifiez le nom d'une activité dans la zone de texte **Fonction** à l'aide de cette syntaxe: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Facultativement, vous pouvez définir un point d'arrêt en spécifiant le chemin d'accès absolu de l'activité de workflow au lieu d'utiliser le nom d'activité dans la zone de texte **Fonction**.Par exemple, supposons que vous ayez une solution de workflow nommée **WorkflowConsoleApplication1** et un workflow dans la solution nommée **Workflow1** qui utilise une activité appelée **Delay1**.Vous pouvez utiliser le nom d'activité **Delay1** ou spécifier le chemin d'accès **Delay1:WorkflowConsoleApplication1 .Workflow1** ou **Delay1:WorkflowConsoleApplication1 .Workflow1: {6614886A\-608E\-412B\-BF98\-99FF1559DDDF}**.  
  
4.  Activez la case à cocher **Utiliser IntelliSense** pour vérifier le nom de la fonction.  
  
     Si cette case à cocher n'est pas activée, aucune vérification du nom du point d'arrêt n'est exécutée.  
  
5.  Sélectionnez **Workflow** dans la liste **Langage**.  
  
6.  Cliquez sur **OK**.  
  
## Voir aussi  
 [Débogage de workflows hérités](../workflow-designer/debugging-legacy-workflows.md)   
 [Appel du débogueur Visual Studio pour Windows Workflow Foundation \(hérité\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)