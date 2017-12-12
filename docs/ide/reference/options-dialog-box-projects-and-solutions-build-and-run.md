---
title: "Options (boîte de dialogue), Projets et solutions, Générer et exécuter | Microsoft Docs"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e15880551e2a896bca473d463b253ec15dda7b36
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Options (boîte de dialogue), Projets et solutions, Générer et exécuter

Dans cette boîte de dialogue, vous pouvez spécifier le nombre maximal de projets Visual C++ ou Visual C# pouvant être générés simultanément, certains comportements de génération par défaut et certains paramètres du journal de génération. Pour accéder à ces options, sélectionnez **Outils > Options**, développez **Projets et solutions** et sélectionnez **Générer et exécuter**.
  
**Nombre maximal de générations de projets en parallèle**  
Spécifie le nombre maximal de projets Visual C++ et Visual C# qui peuvent être générés en même temps. Pour optimiser le processus de génération, le nombre maximal de générations de projets en parallèle est automatiquement défini par rapport au nombre de processeurs équipant votre ordinateur. Le nombre maximal est 32.  

**Générer uniquement des projets de démarrage et des dépendances à l'exécution**  
Génère uniquement le projet de démarrage et ses dépendances lorsque vous utilisez la touche F5, sélectionnez la commande de menu **Déboguer > Démarrer** ou les commandes applicables du menu **Générer**. Si cette option est décochée, tous les projets et toutes les dépendances sont générés. 

**À l'exécution, lorsque les projets sont obsolètes**  
*S’applique aux projets [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] uniquement.*

Lors de l’exécution d’un projet avec F5 ou la commande **Déboguer > Démarrer**, le paramètre par défaut **Inviter à générer** affiche un message si une configuration de projet est obsolète. Sélectionnez **Toujours générer** pour générer le projet chaque fois qu’il est exécuté. Sélectionnez **Jamais générer** pour supprimer toutes les builds automatiques quand un projet est exécuté.

**À l’exécution, lors d’erreurs de génération ou de déploiement**  
*S’applique aux projets [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] uniquement.*

Lors de l’exécution d’un projet avec F5 ou la commande **Déboguer > Démarrer**, le paramètre par défaut **Inviter à générer** affiche un message si un projet doit être exécuté même si la génération a échoué. Sélectionnez **Lancer l’ancienne version** pour lancer automatiquement la dernière build correcte, ce qui peut entraîner des incompatibilités entre le code en cours d’exécution et le code source. Sélectionnez **Ne pas lancer** pour supprimer le message.

**Pour les nouvelles solutions, utiliser le projet sélectionné actuellement comme projet de démarrage**  
Quand cette option est définie, les nouvelles solutions utilisent le projet sélectionné comme projet de démarrage.  

**Commentaires relatifs à la sortie de build du projet MSBuild**  
Détermine quelles informations s’affichent dans la fenêtre **Sortie** de la build.  

**Commentaires du fichier journal de génération du projet MSBuild**  
*S’applique aux projets [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] uniquement.*

Détermine quelles informations sont écrites dans le fichier journal de build, qui se trouve dans \\...\\*Nom_Projet*\Debug\\*Nom_Projet*.log.  

## <a name="see-also"></a>Voir aussi  
[Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)  
[Boîte de dialogue Options, Projets et solutions](projects-and-solutions-options-dialog-box.md)  
[Boîte de dialogue Options, Projets et solutions, Projets web](options-dialog-box-projects-and-solutions-web-projects.md)