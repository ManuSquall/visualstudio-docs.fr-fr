---
title: Débogage de workflows avec Workflow Designer
description: Découvrez comment le Concepteur de flux de travail permet de déboguer des flux de travail et des activités personnalisées à l’aide d’un processus similaire à celui du débogueur Visual Studio par défaut.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45219da52cdd1ff87b7243c3cc742bb4c97a74e7
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435858"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Déboguer des flux de travail avec le Concepteur de flux de travail

Le **Concepteur de flux de travail** permet de déboguer les workflows et les activités personnalisées. Le processus et le comportement sont similaires à ceux du débogueur Visual Studio par défaut.

## <a name="invoke-the-workflow-debugger"></a>Appeler le débogueur de flux de travail

En général, vous déboguez des workflows comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio. Vous pouvez démarrer le débogueur de workflow de plusieurs façons :

- Sélectionnez **attacher au processus** dans le menu **Déboguer** pour sélectionner le processus hôte en cours d’exécution pour votre instance de Workflow. Cette procédure est identique à l'attachement à un processus hôte dans du code managé.

- Appuyez sur **F5** pour commencer à exécuter une instance du workflow, ou pour continuer à s’exécuter après qu’un point d’arrêt a été atteint.

- Utilisez le débogage distant. Pour plus d’informations sur l’utilisation du débogage à distance, consultez [Comment : activer le débogage distant](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Si l’application de workflow cible l’architecture x86 et est hébergée sur un ordinateur exécutant un système d’exploitation 64 bits, le débogage à distance ne fonctionnera pas, sauf si Visual Studio est installé sur l’ordinateur distant ou si la cible de l’application de workflow est changée en **processeur**.

## <a name="step-through-code"></a>Exécuter le code pas à pas

- **Pas à pas** détaillé : pas à pas détaillé dans une activité en appuyant sur **F11**. Le débogueur exécute une commande pas à pas dans le gestionnaire défini. Si aucun gestionnaire n'est défini, vous passez outre l'activité ; pour les activités composites qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier.

- **Pas à pas sortant :** Pas à pas sortant d’une activité en appuyant sur **MAJ** + **F11**. La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités frères. Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours. Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.

- **Pas à pas principal** : pas à pas principal dans une activité en appuyant sur **F10**. Lorsque vous effectuez un pas à pas sur une activité composite, le débogueur marque un arrêt sur le premier enfant exécutable de l'activité composite. Lorsque vous effectuez un pas à pas sur une activité non composite (sur une activité <xref:System.Activities.Statements.Assign>, par exemple), le débogueur exécute l'activité et ses gestionnaires associés, et marque un arrêt sur l'activité suivante. Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.

## <a name="debug-with-f5"></a>Déboguer avec F5

Si vous générez une application console de workflow, appuyez simplement sur **F5** pour commencer le débogage dans votre application et votre flux de travail. Si vous générez une bibliothèque d’activités de manière autonome, vous devez spécifier une application hôte exécutable comme projet de démarrage. Pour définir un projet de démarrage dans **Explorateur de solutions** , cliquez avec le bouton droit sur le nom de l’ordinateur hôte et sélectionnez **définir comme projet de démarrage**.
