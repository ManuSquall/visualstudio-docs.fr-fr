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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 82532fc2864bcb4c19b0cf122e60fd9a64b2dbf9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113064"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)
Cette rubrique décrit comment utiliser le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour déboguer des applications [!INCLUDE[wf](../includes/wf-md.md)] dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 En général, vous déboguez les workflows hérités comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio. Vous pouvez démarrer le débogueur [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pour Windows Workflow Foundation comme suit :

- Sélectionnez **attacher au processus** sur le **déboguer** menu pour sélectionner une instance de workflow en cours d’exécution dans les processus disponibles.

- Appuyez sur **F5** pour démarrer une instance du flux de travail en cours d’exécution, ou pour continuer à exécuter après qu’un point d’arrêt a été atteint.

## <a name="stepping-through-code"></a>Exécution pas à pas du code
 Le débogueur prend en charge l'une des procédures de débogage les plus courantes : l'exécution pas à pas, qui consiste à exécuter le code ligne par ligne. Il existe trois commandes d'exécution pas à pas du code :

- **L’étape**: Vous pouvez exécuter dans une activité à l’aide **F11**. Le débogueur exécute une commande pas à pas dans le gestionnaire défini. Si aucun gestionnaire n'est défini, vous passez outre l'activité ; pour les activités composites qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier. Pas à pas détaillé dans les gestionnaires de code à partir du concepteur n’est pas pris en charge pour les activités suivantes : **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**, ou le **ReplicatorActivity**. Pour déboguer les gestionnaires associés à ces activités, vous devez placer des points d'arrêt explicites dans le code.

- **Pas à pas sortant**: Vous pouvez sortir d’une activité à l’aide **MAJ + F11**. La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités frères. Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours. Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.

- **Pas à pas principal**: Vous pouvez exécuter une activité à l’aide **F10**. Lorsque vous effectuez un pas à pas sur une activité composite. le débogueur s'arrête sur le premier enfant exécutable de l'activité composite. Lorsque le survol d’une non composites, tels qu’un **CodeActivity** activité, le débogueur exécute l’activité et ses gestionnaires associés et les sauts sur l’activité suivante. Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.

## <a name="attaching-to-a-process"></a>Attachement à un processus
 Pour déboguer un flux de travail via un attachement à un processus, sélectionnez le processus disponible dans le **processus disponibles** zone de liste dans le **attacher au processus** boîte de dialogue. Si **automatique : Code de flux de travail** ne figure pas dans le **attacher à** texte zone, puis cliquez sur **sélectionnez**. Dans le **sélectionner le Type de Code** boîte de dialogue, cliquez sur **déboguer ces types de codes** et sélectionnez **Workflow**. Puis cliquez sur **OK** et cliquez sur **attacher**.

## <a name="debugging-with-f5"></a>Débogage avec la touche F5
 Si une application hôte du workflow et les DLL de workflow sont situés dans différents projets Visual Studio, par exemple, lorsque vous utilisez une bibliothèque d’activités de flux de travail, vous devez définir le projet de DLL de workflow en projet de démarrage de la solution Visual Studio pour déboguer le flux de travail à l’aide de **F5**. Vous devez également définir le chemin d’accès à l’application hôte dans le projet DLL de workflow **démarrer le programme externe** propriété.

 Pour définir un projet de démarrage dans l’Explorateur de solutions, cliquez sur le nom du projet et sélectionnez **définir comme projet de démarrage**. Pour définir le chemin d’accès à l’hôte dans le **démarrer le programme externe** propriété, double-cliquez sur le projet de workflow **propriétés** nœud dans l’Explorateur de solutions, puis sélectionnez le **déboguer** onglet. Sous **Action de démarrage**, sélectionnez **démarrer le programme externe** et entrez le chemin d’accès au fichier .exe qui héberge le flux de travail que vous souhaitez déboguer.

 Si l'application hôte est définie comme projet de démarrage, seul le débogueur Visual Studio est appelé pour déboguer (le débogueur [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pour Windows Workflow Foundation n'est pas appelé). Si le débogueur Visual Studio est utilisé, seuls les points d'arrêt de code C# ou Visual Basic sont atteints ; les points d'arrêt définis dans le concepteur de workflow ne sont pas atteints. Par exemple, un point d'arrêt défini sur une activité <xref:System.Workflow.Activities.ParallelActivity> dans le concepteur est atteint si le débogueur [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pour Windows Workflow Foundation est utilisé, mais ne l'est pas lorsque vous utilisez le débogueur Visual Studio.

## <a name="see-also"></a>Voir aussi
 [Guide pratique pour Définissez des points d’arrêt dans le flux de travail (hérité)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [débogage de Workflows hérités](../workflow-designer/debugging-legacy-workflows.md)