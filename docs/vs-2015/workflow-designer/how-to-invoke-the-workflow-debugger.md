---
title: 'Comment : appeler le débogueur de flux de travail | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e702b402d5350641aa01d341106634efe5f6c6c4
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849267"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Procédure : appeler le débogueur de workflow
En général, vous déboguez des workflows comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio. Vous pouvez démarrer le débogueur de workflow de plusieurs façons :

- Sélectionnez **attacher au processus** dans le menu **Déboguer** pour sélectionner le processus hôte en cours d’exécution pour votre instance de Workflow. Cette procédure est identique à l'attachement à un processus hôte dans du code managé.

- Appuyez sur **F5** pour commencer à exécuter une instance du workflow, ou pour continuer à s’exécuter après qu’un point d’arrêt a été atteint.

- Utilisez le débogage distant. Pour plus d’informations sur l’utilisation du débogage à distance, consultez [Comment : activer le débogage distant](https://msdn.microsoft.com/library/febz73k0.aspx).

    > [!NOTE]
    > Si l’application de workflow cible l’architecture x86 et est hébergée sur un ordinateur exécutant un système d’exploitation 64 bits, le débogage à distance ne fonctionnera pas, sauf si [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] est installé sur l’ordinateur distant ou si la cible de l’application de workflow est remplacée par **n’importe quel processeur**.

### <a name="stepping-through-code"></a>Exécution du code pas à pas

- **Pas à pas**détaillé : vous pouvez effectuer un pas à pas détaillé dans une activité à l’aide de **F11**. Le débogueur exécute une commande pas à pas dans le gestionnaire défini. Si aucun gestionnaire n'est défini, vous passez outre l'activité ; pour les activités composites qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier.

- **Pas à pas sortant :** Vous pouvez effectuer un pas à pas sortant d’une activité à l’aide de **Shift-F11**. La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités frères. Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours. Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.

- **Pas à pas principal**: vous pouvez effectuer un pas à pas principal dans une activité à l’aide de **F10**. Lorsque vous effectuez un pas à pas sur une activité composite, le débogueur marque un arrêt sur le premier enfant exécutable de l'activité composite. Lorsque vous effectuez un pas à pas sur une activité non composite (sur une activité <xref:System.Activities.Statements.Assign>, par exemple), le débogueur exécute l'activité et ses gestionnaires associés, et marque un arrêt sur l'activité suivante. Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.

### <a name="debugging-with-f5"></a>Débogage avec la touche F5

- Si vous générez un projet d’application console de workflow, appuyez simplement sur **F5** pour commencer le débogage dans votre application et votre flux de travail. Si vous générez une bibliothèque d'activités seule, vous devez posséder une application hôte exécutable comme projet de démarrage. Pour définir un projet de démarrage dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom de l’ordinateur hôte et sélectionnez **définir comme projet de démarrage**.

## <a name="see-also"></a>Voir aussi
 [Comment : définir des points d’arrêt dans les workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [débogage de flux de travail avec le concepteur de flux de travail](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
