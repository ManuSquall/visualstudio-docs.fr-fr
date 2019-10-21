---
title: Débogage des flux de travail hérités | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ae0a08e1623e1b90046d164d8bfe04eaf67229
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656865"
---
# <a name="debugging-legacy-workflows"></a>Débogage de workflows hérités
Si vous utilisez le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité dans [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pour créer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ciblent le .NET Framework 3.0 ou 3.5, vous pouvez déboguer vos workflows comme tout autre programme en définissant des points d'arrêt, en créant des attachements à des processus et en examinant les threads et la pile des appels. Vous avez également la possibilité d'effectuer un débogage à distance.

> [!NOTE]
> Si plusieurs versions de Visual Studio ont été installées et désinstallées sur votre ordinateur, le débogage WF3 peut échouer pour l'une des raisons suivantes :
>
> - Les points d'arrêt ne sont pas atteints.
>   - Le message suivant s'affiche :
>
>   **Impossible de démarrer le débogage sur le serveur Web. Le débogueur n’est pas correctement installé.  Impossible de déboguer le type de code demandé.  Exécutez le programme d’installation pour installer ou réparer le débogueur.**
>
>   Si l'un de ces scénarios se produit lors du débogage de workflows .NET Framework 3.0 ou 3.5, réparez l'installation de Visual Studio.

 [!INCLUDE[wf2](../includes/wf2-md.md)] intègre les fenêtres de débogage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] standard suivantes :

- **Point d’arrêt**: fonctionne comme prévu, mais vous spécifiez une activité pour le nom de la fonction.

- **Pile des appels**: modifiée pour fournir un plan des activités qui ont été exécutées dans une instance de Workflow. Les entrées de la fenêtre **pile des appels** sont une recherche à profondeur prioritaire des activités en cours d’exécution. Vous pouvez double-cliquer sur une entrée pour placer le focus sur l'activité sélectionnée.

- **Threads**: fournit l’ID d’instance de l’instance de flux de travail en cours de débogage.

  Visual Studio pour Windows Workflow Foundation ne prend pas en charge les fonctionnalités de débogage suivantes :

- Points d'arrêt conditionnels sur l'aire du concepteur.

- Espion express.

- Définir l'instruction suivante.

- Exécuter jusqu'au curseur.

- Modifier &amp ; Continuer.

- Débogage juste-à-temps.

- Débogage en mode mixte.

## <a name="in-this-section"></a>Dans cette section
 [Appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Désactivation du débogueur Visual Studio pour Windows Workflow Foundation (hérité)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Guide pratique pour déboguer des flux de travail basés sur ASP.NET (hérité)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)

 [Guide pratique pour définir des points d’arrêt dans les flux de travail (hérité)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)

 [Débogage de flux de travail depuis un ordinateur distant (hérité)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)

 [Options de débogage pas à pas (hérité)](../workflow-designer/debug-stepping-options-legacy.md)

 [Guide pratique pour modifier l’option de débogage pas à pas (hérité)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)