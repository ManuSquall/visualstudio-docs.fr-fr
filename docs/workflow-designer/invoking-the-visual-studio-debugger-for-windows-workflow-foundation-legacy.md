---
title: Concepteur de flux de travail - appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a326f8b6dc482c2adfc2caba797c38094a99f8c5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)

Cette rubrique décrit comment utiliser le débogueur Visual Studio pour déboguer des applications de Windows Workflow Foundation (WF) dans le Concepteur de flux de travail Windows hérité. Utilisez le Concepteur de flux de travail hérité lorsque vous avez besoin cibler le .NET Framework version 3.5 ou du WinFX.

En général, vous déboguez les workflows hérités comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio. Vous pouvez démarrer Visual Studio débogueur pour Windows Workflow Foundation comme suit :

-   Sélectionnez **attacher au processus** sur la **déboguer** menu pour sélectionner une instance de workflow en cours d’exécution des processus disponibles.

-   Appuyez sur **F5** pour démarrer une instance du flux de travail en cours d’exécution, ou pour continuer à exécuter après qu’un point d’arrêt a été atteint.

## <a name="stepping-through-code"></a>Exécution pas à pas du code

Le débogueur prend en charge l'une des procédures de débogage les plus courantes : l'exécution pas à pas, qui consiste à exécuter le code ligne par ligne. Il existe trois commandes d'exécution pas à pas du code :

-   **Pas à pas détaillé**: vous pouvez exécuter dans une activité à l’aide de **F11**. Le débogueur exécute une commande pas à pas dans le gestionnaire défini. Si aucun gestionnaire n'est défini, vous passez outre l'activité ; pour les activités composites qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier. Pas à pas détaillé dans les gestionnaires de code à partir du concepteur n’est pas prise en charge pour les activités suivantes : **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**, ou **ReplicatorActivity**. Pour déboguer les gestionnaires associés à ces activités, vous devez placer des points d'arrêt explicites dans le code.

-   **Pas à pas sortant**: vous pouvez sortir d’une activité à l’aide de **MAJ + F11**. La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités frères. Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours. Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.

-   **Pas à pas principal**: vous pouvez survol d’une activité à l’aide de **F10**. Lorsque vous effectuez un pas à pas sur une activité composite. le débogueur s'arrête sur le premier enfant exécutable de l'activité composite. Lorsque le survol d’une non composites, comme un **CodeActivity** activité, le débogueur exécute l’activité et ses gestionnaires associés sauts sur l’activité suivante. Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.

## <a name="attaching-to-a-process"></a>Attachement à un processus
 Pour déboguer un flux de travail via un attachement à un processus, sélectionnez le processus disponible à partir de la **processus disponibles** zone de liste dans le **attacher au processus** boîte de dialogue. Si **automatique : Code de flux de travail** ne figure pas dans le **attacher à** texte zone, puis cliquez sur **sélectionnez**. Dans le **sélectionner le Type de Code** boîte de dialogue, cliquez sur **déboguer ces types de codes** et sélectionnez **Workflow**. Puis cliquez sur **OK** et cliquez sur **attacher**.

## <a name="debugging-with-f5"></a>Débogage avec la touche F5
 Si une application hôte du workflow et la DLL de workflow sont situés dans différents projets Visual Studio, par exemple, lorsque vous utilisez une bibliothèque d’activités de flux de travail, vous devez définir le projet de DLL de workflow comme projet de démarrage de solution Visual Studio pour déboguer le flux de travail à l’aide de **F5**. Vous devez également définir le chemin d’accès à l’application hôte dans le projet DLL de flux de travail **démarrer le programme externe** propriété.

 Pour définir un projet de démarrage dans l’Explorateur de solutions, cliquez sur le nom du projet et sélectionnez **définir comme projet de démarrage**. Pour définir le chemin d’accès à l’hôte dans le **démarrer le programme externe** propriété, double-cliquez sur le projet de workflow **propriétés** nœud dans l’Explorateur de solutions, puis sélectionnez le **déboguer** onglet. Sous **Action de démarrage**, sélectionnez **démarrer le programme externe** et entrez le chemin d’accès au fichier .exe qui héberge le flux de travail que vous souhaitez déboguer.

 Si l’application hôte est définie comme projet de démarrage, seul le débogueur Visual Studio est appelé pour le débogage ; Visual Studio débogueur pour Windows Workflow Foundation n’est pas appelée. Si le débogueur Visual Studio est utilisé, seuls les points d'arrêt de code C# ou Visual Basic sont atteints ; les points d'arrêt définis dans le concepteur de workflow ne sont pas atteints. Par exemple, un point d’arrêt que vous définissez sur un <xref:System.Workflow.Activities.ParallelActivity> activité dans le concepteur est atteint si Visual Studio débogueur pour Windows Workflow Foundation est utilisée, mais pas lorsque vous utilisez le débogueur Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir des points d’arrêt dans les flux de travail (hérité)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)