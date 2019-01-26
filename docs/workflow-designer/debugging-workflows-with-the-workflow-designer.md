---
title: Débogage de workflows avec Workflow Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b06ee7101dcb6b227f8e7f0228730fb0668695b4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998844"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Déboguer des workflows avec Workflow Designer

Le **Concepteur de Workflow** offre la possibilité de déboguer des workflows et des activités personnalisées. Les processus et le comportement sont similaires à celle du débogueur Visual Studio par défaut.

## <a name="invoke-the-workflow-debugger"></a>Appelez le débogueur de flux de travail

En général, vous déboguez des workflows comme vous déboguez des programmes écrits dans d'autres langages de programmation Visual Studio. Vous pouvez démarrer le débogueur de workflow de plusieurs façons :

- Sélectionnez **attacher au processus** sur le **déboguer** menu pour sélectionner le processus hôte en cours d’exécution pour votre instance de workflow. Cette procédure est identique à l'attachement à un processus hôte dans du code managé.

- Appuyez sur **F5** pour démarrer une instance du flux de travail en cours d’exécution, ou pour continuer à exécuter après qu’un point d’arrêt a été atteint.

- Utilisez le débogage distant. Pour plus d’informations sur l’utilisation du débogage à distance, consultez [Comment : Activer le débogage distant](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Si l’application de flux de travail cible le x86 architecture et est hébergée sur un ordinateur exécutant un système d’exploitation 64 bits, le débogage à distance ne fonctionne pas si Visual Studio est installé sur l’ordinateur distant ou la cible pour l’application de flux de travail est remplacée par  **N’importe quelle UC**.

## <a name="step-through-code"></a>Exécuter le code pas à pas

- **L’étape**: Étape dans une activité en appuyant sur **F11**. Le débogueur exécute une commande pas à pas dans le gestionnaire défini. Si aucun gestionnaire n'est défini, vous passez outre l'activité ; pour les activités composites qui contiennent d'autres activités, vous effectuez un pas à pas dans l'activité exécutée en premier.

- **Pas à pas sortant :** Sortir d’une activité en appuyant sur **MAJ**+**F11**. La commande de pas à pas sortant permet d'exécuter totalement l'activité en cours et toutes ses activités frères. Le débogueur marque ensuite un arrêt sur le parent de l'activité en cours. Lorsque la commande de pas à pas sortant est exécutée à partir d'un gestionnaire de code, le débogueur marque un arrêt sur l'activité à laquelle le gestionnaire est associé.

- **Pas à pas principal**: Étape sur une activité en appuyant sur **F10**. Lorsque vous effectuez un pas à pas sur une activité composite, le débogueur marque un arrêt sur le premier enfant exécutable de l'activité composite. Lorsque vous effectuez un pas à pas sur une activité non composite (sur une activité <xref:System.Activities.Statements.Assign>, par exemple), le débogueur exécute l'activité et ses gestionnaires associés, et marque un arrêt sur l'activité suivante. Si l'activité exécutée est la dernière activité enfant d'une activité composite, après l'exécution, le débogueur marque un arrêt sur l'activité parente.

## <a name="debug-with-f5"></a>Déboguer avec F5

Si vous créez une application de console de flux de travail, appuyez simplement sur **F5** pour commencer le débogage de votre application et le flux de travail. Si vous générez une bibliothèque d’activités sur son propre, vous devez spécifier une application hôte exécutable comme projet de démarrage. Pour définir un projet de démarrage dans **l’Explorateur de solutions**, cliquez sur le nom du projet de l’hôte et sélectionnez **définir comme projet de démarrage**.