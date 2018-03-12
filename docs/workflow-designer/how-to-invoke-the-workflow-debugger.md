---
title: "Comment : appeler le débogueur de flux de travail | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b84fad1bd0daf1f7163a06683f8c41ff0257a2e4
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Procédure : appeler le débogueur de workflow
En général, vous déboguez des workflows comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio. Vous pouvez démarrer le débogueur de workflow de plusieurs façons :

-   Sélectionnez **attacher au processus** sur la **déboguer** menu pour sélectionner le processus hôte en cours d’exécution pour votre instance de workflow. Cette procédure est identique à l'attachement à un processus hôte dans du code managé.

-   Appuyez sur **F5** pour démarrer une instance du flux de travail en cours d’exécution, ou pour continuer à exécuter après qu’un point d’arrêt a été atteint.

-   Utilisez le débogage distant. Pour plus d’informations sur l’utilisation du débogage à distance, consultez [Comment : activer le débogage à distance](http://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > Si l’application de flux de travail cible le x86 architecture et est hébergée sur un ordinateur exécutant un système d’exploitation 64 bits, le débogage distant ne fonctionne pas, sauf si [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] est installé sur l’ordinateur distant ou la cible de l’application de flux de travail est remplacée par **N’importe quelle UC**.

### <a name="stepping-through-code"></a>Exécution du code pas à pas

-   **Pas à pas détaillé**: vous pouvez exécuter dans une activité à l’aide de **F11**. Le débogueur exécute une commande pas à pas dans le gestionnaire défini. Si aucun gestionnaire n'est défini, vous passez outre l'activité ; pour les activités composites qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier.

-   **Pas à pas sortant :** vous pouvez sortir d’une activité à l’aide de **MAJ + F11**. La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités frères. Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours. Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.

-   **Pas à pas principal**: vous pouvez survol d’une activité à l’aide de **F10**. Lorsque vous effectuez un pas à pas sur une activité composite, le débogueur marque un arrêt sur le premier enfant exécutable de l'activité composite. Lorsque vous effectuez un pas à pas sur une activité non composite (sur une activité <xref:System.Activities.Statements.Assign>, par exemple), le débogueur exécute l'activité et ses gestionnaires associés, et marque un arrêt sur l'activité suivante. Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.

### <a name="debugging-with-f5"></a>Débogage avec la touche F5

-   Si vous générez un projet d’Application Console de Workflow, appuyez simplement sur **F5** pour commencer le débogage dans votre application et le flux de travail. Si vous générez une bibliothèque d'activités seule, vous devez posséder une application hôte exécutable comme projet de démarrage. Pour définir un projet de démarrage dans **l’Explorateur de solutions**, cliquez sur le nom du projet de l’hôte et sélectionnez **définir comme projet de démarrage**.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir des points d’arrêt dans les flux de travail](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Débogage de flux de travail à l’aide du Concepteur de flux de travail](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)