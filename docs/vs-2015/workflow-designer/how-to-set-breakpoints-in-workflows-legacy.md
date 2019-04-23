---
title: 'Procédure : Définissez des points d’arrêt dans le flux de travail (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 92950247420f49c4a5295d25aec2c8697efb3534
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069963"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Procédure : Définir des points d’arrêt dans les workflows (hérités)
Cette rubrique décrit comment définir des points d'arrêt dans les applications [!INCLUDE[wf](../includes/wf-md.md)] générées à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque votre application [!INCLUDE[wf2](../includes/wf2-md.md)] doit cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Lorsque vous utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] pour générer une application [!INCLUDE[wf2](../includes/wf2-md.md)], vous pouvez définir des points d'arrêt en code C# et Visual Basic, tout comme vous le faites dans Visual Studio. Comme prévu, l'exécution de workflow s'arrête à chaque point d'arrêt que vous définissez.  
  
 Un point d’arrêt a trois états : *En attente*, *lié*, et *erreur*. Lorsque vous définissez un point d'arrêt, il porte l'état En attente et il est représenté par une icône rouge creuse. Lorsque l'exécution a chargé le type de workflow, il adopte l'état Dépendant et est représenté par une icône rouge unie. Si vous spécifiez un format incorrect pour le point d'arrêt (en indiquant un nom d'activité incorrect, par exemple), un message d'erreur apparaît. Le point d'arrêt est ajouté à la fenêtre de points d'arrêt, mais il est marqué d'un petit « x ».  
  
 Vous pouvez définir des points d'arrêt sur une activité de l'aire de conception de workflow comme suit :  
  
- Cliquez sur l’activité et sélectionnez **point d’arrêt \ insérer un point d’arrêt**.  
  
- Sélectionnez l'activité et appuyez sur F9.  
  
- Sélectionnez **nouveau point d’arrêt** à partir de la **déboguer** menu.  
  
     Vous pouvez également utiliser cette option pour définir un nouveau point d'arrêt pendant le débogage, lorsque le débogueur s'arrête à un point d'arrêt.  
  
    > [!NOTE]
    >  La définition des points d'arrêt sur les workflows appelés n'est pas prise en charge.  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Pour définir un point d'arrêt à l'aide de l'option Nouveau point d'arrêt du menu Débogage  
  
1. Sur le **déboguer** menu, sélectionnez **nouveau point d’arrêt**.  
  
2. Cliquez sur **interrompre à la fonction**.  
  
     Le **nouveau point d’arrêt** boîte de dialogue s’ouvre.  
  
3. Spécifiez le nom d’une activité dans le **fonction** zone de texte à l’aide de cette syntaxe : `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Si vous le souhaitez, plutôt que le nom de l’activité dans le **fonction** zone de texte, vous pouvez définir un point d’arrêt en spécifiant le chemin d’accès absolu de l’activité de flux de travail. Par exemple, supposons que vous disposez d’une solution de flux de travail nommée **WorkflowConsoleApplication1** et un flux de travail dans la solution nommée **Workflow1** qui utilise une activité nommée **Delay1**. Vous pouvez utiliser le nom de l’activité **Delay1** ou spécifiez le chemin d’accès en tant que **delay1 : workflowconsoleapplication1.Workflow1** ou **delay1 : workflowconsoleapplication1.Workflow1 : {} 6614886A-608E-412B-BF98-99FF1559DDDF}**.  
  
4. Sélectionnez le **utiliser IntelliSense** case à cocher pour vérifier le nom de fonction.  
  
     Si cette case à cocher n'est pas activée, aucune vérification du nom du point d'arrêt n'est exécutée.  
  
5. Sélectionnez **Workflow** à partir de la **langage** liste.  
  
6. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Workflows hérités](../workflow-designer/debugging-legacy-workflows.md)   
 [Appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)