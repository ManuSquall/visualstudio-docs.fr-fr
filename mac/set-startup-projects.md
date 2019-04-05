---
title: Définir plusieurs projets de démarrage dans Visual Studio pour Mac
description: Cet article explique comment définir plusieurs projets à démarrer au moment de l’exécution ou du débogage d’une solution.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 65b44dddfdadcb7ef38332fa35443dbaeededb5d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152913"
---
# <a name="how-to-set-multiple-startup-projects"></a>Procédure : Définir plusieurs projets de démarrage

Visual Studio pour Mac vous permet de spécifier le mode de démarrage de plusieurs projets quand vous déboguez ou exécutez votre solution.

## <a name="to-set-multiple-startup-projects"></a>Pour définir plusieurs projets de démarrage

1.  Dans le **Panneau Solutions**, sélectionnez la solution (nœud supérieur).

2. Choisissez le menu contextuel (clic droit) du nœud de la solution, puis choisissez **Définir les projets de démarrage**.

   ![Définir le menu contextuel des projets de démarrage](media/startup-proj-ctx-menu.png)

3. La boîte de dialogue **Créer une configuration d’exécution de solution** s’affiche. Cette boîte de dialogue crée une configuration d’exécution de solution nommée pour votre solution. Vous pouvez donner le nom de votre choix. Le nom par défaut est `Multiple Projects`.

   ![Boîte de dialogue Créer une configuration d’exécution de solution](media/create-sln-run-config.png)

4. Cliquez sur **Créer une configuration d’exécution**. La boîte de dialogue **Options de la solution** s’ouvre avec la nouvelle configuration d’exécution de solution sélectionnée.

   ![Boîte de dialogue Options de la solution](media/sln-options-run-config-multi-projects.png)

5. Sélectionnez les projets à démarrer quand vous déboguez ou exécutez votre application à partir de Visual Studio pour Mac.

   ![Boîte de dialogue Options de la solution avec la configuration d’exécution configurée](media/sln-options-run-config-multi-projects-configured.png)

6. Cliquez sur **OK**. La boîte de dialogue se ferme, et la nouvelle configuration d’exécution de solution est définie comme configuration d’exécution active.

   ![Solution avec plusieurs projets configurés pour démarrer au moment du débogage ou de l’exécution](media/startup-project-configured.png) Vous pouvez voir que deux projets sont configurés pour démarrer, car ils sont tous les deux en **gras** dans le **Panneau Solutions**. Dans la barre d’outils, la nouvelle configuration d’exécution est configurée en tant que configuration d’exécution de solution actuelle.

## <a name="next-steps"></a>Étapes suivantes

- [Compilation et génération dans Visual Studio pour Mac](compiling-and-building.md)
- [Présentation des configurations de build](configurations.md)