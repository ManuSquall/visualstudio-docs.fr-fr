---
title: 'Comment : appeler le débogueur de flux de travail | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: acfbe34bc4a3d3c1139f8b1e821d9996fb8c712b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295735"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Procédure : appeler le débogueur de workflow
En général, vous déboguez des workflows comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio. Vous pouvez démarrer le débogueur de workflow de plusieurs façons :  
  
-   Sélectionnez **attacher au processus** sur le **déboguer** menu pour sélectionner le processus hôte en cours d’exécution pour votre instance de workflow. Cette procédure est identique à l'attachement à un processus hôte dans du code managé.  
  
-   Appuyez sur **F5** pour démarrer une instance du flux de travail en cours d’exécution, ou pour continuer à exécuter après qu’un point d’arrêt a été atteint.  
  
-   Utilisez le débogage distant. Pour plus d’informations sur l’utilisation du débogage à distance, consultez [Comment : activer le débogage à distance](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Si l’application de flux de travail cible le x86 architecture et est hébergée sur un ordinateur exécutant un système d’exploitation 64 bits, le débogage à distance ne fonctionnera pas, sauf si [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] est installé sur l’ordinateur distant ou la cible de l’application de workflow soit remplacée par **N’importe quelle UC**.  
  
### <a name="stepping-through-code"></a>Exécution du code pas à pas  
  
-   **Pas à pas détaillé**: vous pouvez exécuter dans une activité à l’aide **F11**. Le débogueur exécute une commande pas à pas dans le gestionnaire défini. Si aucun gestionnaire n'est défini, vous passez outre l'activité ; pour les activités composites qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier.  
  
-   **Hors de l’étape :** vous pouvez sortir d’une activité à l’aide **MAJ + F11**. La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités frères. Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours. Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.  
  
-   **Pas à pas principal**: vous pouvez exécuter une activité à l’aide **F10**. Lorsque vous effectuez un pas à pas sur une activité composite, le débogueur marque un arrêt sur le premier enfant exécutable de l'activité composite. Lorsque vous effectuez un pas à pas sur une activité non composite (sur une activité <xref:System.Activities.Statements.Assign>, par exemple), le débogueur exécute l'activité et ses gestionnaires associés, et marque un arrêt sur l'activité suivante. Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.  
  
### <a name="debugging-with-f5"></a>Débogage avec la touche F5  
  
-   Si vous générez un projet d’Application Console de Workflow, appuyez simplement sur **F5** pour commencer le débogage de votre application et le flux de travail. Si vous générez une bibliothèque d'activités seule, vous devez posséder une application hôte exécutable comme projet de démarrage. Pour définir un projet de démarrage dans **l’Explorateur de solutions**, cliquez sur le nom du projet de l’hôte et sélectionnez **définir comme projet de démarrage**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : définir des points d’arrêt dans les Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Débogage de flux de travail à l’aide du Concepteur de flux de travail](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)