---
title: Boîte de dialogue Options, Projets et solutions, Générer et exécuter
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24ba5bbf34ecc12c2508c538e74909ee0a10aef4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461394"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Boîte de dialogue d’options : Projets et solutions \> Construisent et exécutent

Dans cette boîte de dialogue, vous pouvez spécifier le nombre maximal de projets C++ ou C# pouvant être générés simultanément, certains comportements de génération par défaut et certains paramètres du journal de génération. Pour accéder à ces options, sélectionnez **Outils** > **Options d’élargir** les **projets et les solutions,** puis sélectionnez **Build and Run**.

**Nombre maximal de générations de projets en parallèle**

Spécifie le nombre maximal de projets C++ et C# qui peuvent être générés en même temps. Pour optimiser le processus de génération, le nombre maximal de générations de projets en parallèle est automatiquement défini par rapport au nombre de processeurs équipant votre ordinateur. La valeur maximale est de 32.

**Générer uniquement des projets de démarrage et des dépendances à l'exécution**

Génère uniquement le projet de démarrage et ses dépendances lorsque vous utilisez la touche **F5**, sélectionnez la commande de menu **Déboguer** > **Démarrer le débogage** ou les commandes applicables du menu **Générer**. Si cette option est décochée, tous les projets et toutes les dépendances sont générés.

**À l'exécution, lorsque les projets sont obsolètes**

*S’applique aux projets C++ uniquement.*

Lors de l’exécution d’un projet avec **F5** ou la commande **Déboguer** > **Démarrer le débogage**, le paramètre par défaut **Inviter à générer** affiche un message si une configuration de projet est obsolète. Sélectionnez **Toujours générer** pour générer le projet chaque fois qu’il est exécuté. Sélectionnez **Jamais générer** pour supprimer toutes les builds automatiques quand un projet est exécuté.

**À l’exécution, lors d’erreurs de génération ou de déploiement**

*S’applique aux projets C++ uniquement.*

Lors de l’exécution d’un projet avec **F5** ou la commande **Déboguer** > ** Démarrer le débogage**, le paramètre par défaut **Inviter à générer** affiche un message si un projet doit être exécuté même si la génération a échoué. Sélectionnez **Lancer l’ancienne version** pour lancer automatiquement la dernière build correcte, ce qui peut entraîner des incompatibilités entre le code en cours d’exécution et le code source. Sélectionnez **Ne pas lancer** pour supprimer le message.

**Pour les nouvelles solutions, utiliser le projet sélectionné actuellement comme projet de démarrage**

Quand cette option est définie, les nouvelles solutions utilisent le projet sélectionné comme projet de démarrage.

**Commentaires relatifs à la sortie de build du projet MSBuild**

Détermine la quantité d’informations du processus de génération qui s’affiche dans la fenêtre **Sortie**.

**Commentaires du fichier journal de génération du projet MSBuild**

*S’applique aux projets C++ uniquement.*

Détermine la quantité d’informations écrites sur le fichier de journal de construction, qui est situé à * \\ \<ProjectName\\\<>-Debug ProjectName>.log*.

## <a name="see-also"></a>Voir aussi

- [Compilation et construction](../../ide/compiling-and-building-in-visual-studio.md)
- [Boîte de dialogue Options, Projets et solutions](projects-and-solutions-options-dialog-box.md)
- [Boîte de dialogue Options, Projets et solutions, Projets web](options-dialog-box-projects-and-solutions-web-projects.md)