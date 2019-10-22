---
title: Appel du débogueur pour Windows Workflow Foundation (hérité) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcceca362f3c2a891d36f8f4e8071d0e35c8f164
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658976"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)
Cette rubrique décrit comment utiliser le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour déboguer des applications [!INCLUDE[wf](../includes/wf-md.md)] dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 En général, vous déboguez les workflows hérités comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio. Vous pouvez démarrer le débogueur [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pour Windows Workflow Foundation comme suit :

- Sélectionnez **attacher au processus** dans le menu **Déboguer** pour sélectionner une instance de workflow en cours d’exécution parmi les processus disponibles.

- Appuyez sur **F5** pour commencer à exécuter une instance du workflow, ou pour continuer à s’exécuter après qu’un point d’arrêt a été atteint.

## <a name="stepping-through-code"></a>Exécution pas à pas du code
 Le débogueur prend en charge l'une des procédures de débogage les plus courantes : l'exécution pas à pas, qui consiste à exécuter le code ligne par ligne. Il existe trois commandes d'exécution pas à pas du code :

- **Pas à pas**détaillé : vous pouvez effectuer un pas à pas détaillé dans une activité à l’aide de **F11**. Le débogueur exécute une commande pas à pas dans le gestionnaire défini. Si aucun gestionnaire n'est défini, vous passez outre l'activité ; pour les activités composites qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier. Le pas à pas détaillé dans les gestionnaires de code du concepteur n’est pas pris en charge pour les activités suivantes : **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**ou **ReplicatorActivity**. Pour déboguer les gestionnaires associés à ces activités, vous devez placer des points d'arrêt explicites dans le code.

- **Pas à pas sortant**: vous pouvez effectuer un pas à pas sortant d’une activité à l’aide de **Shift-F11**. La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités frères. Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours. Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.

- **Pas à pas principal**: vous pouvez effectuer un pas à pas principal dans une activité à l’aide de **F10**. Lorsque vous effectuez un pas à pas sur une activité composite. le débogueur s'arrête sur le premier enfant exécutable de l'activité composite. Quand vous effectuez un pas à pas principal sur un non composite, tel qu’une activité **CodeActivity** , le débogueur exécute l’activité et ses gestionnaires associés, et s’arrête sur l’activité suivante. Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.

## <a name="attaching-to-a-process"></a>Attachement à un processus
 Pour déboguer un workflow en l’attachant à un processus, sélectionnez le processus disponible dans la zone de liste **processus disponibles** de la boîte de dialogue **attacher au processus** . Si **automatique : le code de workflow** n’est pas affiché dans la zone de texte **attacher à** , puis cliquez sur **Sélectionner**. Dans la boîte de dialogue **Sélectionner le type de code** , cliquez sur **Déboguer ces types de codes** et sélectionnez flux de **travail**. Cliquez ensuite sur **OK** , puis sur **attacher**.

## <a name="debugging-with-f5"></a>Débogage avec la touche F5
 Si une application hôte de workflow et une DLL de workflow se trouvent dans des projets Visual Studio différents, par exemple, lorsque vous utilisez une bibliothèque d’activité de workflow, vous devez définir le projet de DLL de workflow comme projet de démarrage de la solution Visual Studio pour déboguer le flux de travail. en appuyant sur **F5**. Vous devez également définir le chemin d’accès à l’application hôte dans la propriété **Démarrer le programme externe** du projet de dll de Workflow.

 Pour définir un projet de démarrage dans Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet et sélectionnez **définir comme projet de démarrage**. Pour définir le chemin d’accès à l’ordinateur hôte dans la propriété **Démarrer le programme externe** , double-cliquez sur le nœud **Propriétés** du projet de workflow dans Explorateur de solutions puis sélectionnez l’onglet **Déboguer** . Sous **action de démarrage**, sélectionnez **Démarrer le programme externe** et entrez le chemin d’accès au fichier. exe qui héberge le workflow que vous souhaitez déboguer.

 Si l'application hôte est définie comme projet de démarrage, seul le débogueur Visual Studio est appelé pour déboguer (le débogueur [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pour Windows Workflow Foundation n'est pas appelé). Si le débogueur Visual Studio est utilisé, seuls les points d'arrêt de code C# ou Visual Basic sont atteints ; les points d'arrêt définis dans le concepteur de workflow ne sont pas atteints. Par exemple, un point d'arrêt défini sur une activité <xref:System.Workflow.Activities.ParallelActivity> dans le concepteur est atteint si le débogueur [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pour Windows Workflow Foundation est utilisé, mais ne l'est pas lorsque vous utilisez le débogueur Visual Studio.

## <a name="see-also"></a>Voir aussi
 [Comment : définir des points d’arrêt dans les workflows (hérité)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)