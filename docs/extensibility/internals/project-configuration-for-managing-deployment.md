---
title: "Configuration de projet pour la gestion du d&#233;ploiement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurations de projet, la gestion du déploiement"
  - "projets (Visual Studio SDK), configuration pour la gestion du déploiement"
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Configuration de projet pour la gestion du d&#233;ploiement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le déploiement consiste à déplacer physiquement les éléments de sortie d'un processus de génération à l'emplacement attendu pour le débogage et installation.  Par exemple, une application Web peut être générée sur un ordinateur local et être ensuite placé sur le serveur.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge deux façons dont les projets peuvent être impliqué dans le déploiement :  
  
-   Comme rubrique du processus de déploiement.  
  
-   en tant que gestionnaire du processus de déploiement.  
  
 Avant que les solutions puissent être déployées, vous devez d'abord ajouter un projet de déploiement pour configurer des options de déploiement.  Si le projet de déploiement n'existe pas déjà, vous êtes si vous souhaitez créer un lorsque vous sélectionnez **Déployer la solution** dans le menu de **Générer** ou cliquez avec le bouton droit sur la solution.  Cliquez sur **Oui** ouvre la boîte de dialogue d' **Ajouter un nouveau projet** avec le projet d' **Assistant Déploiement à distance** sélectionné.  
  
 Assistant Déploiement à distance vous demande le type d'application \(les fenêtres ou le Web\), les groupes de sorties de projet à inclure, tous les fichiers supplémentaires que vous voulez inclure, et l'ordinateur distant vous souhaitez déployer à.  la dernière page de l'Assistant affiche un résumé des options sélectionnées.  
  
 Projets qui font l'objet d'éléments d'un résultat de processus de déploiement qui doivent être déplacés dans un environnement secondaire.  Ces éléments de sortie sont décrits comme paramètres pour l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , dont l'objectif principal si de permettre à des projets de regrouper des sorties.  Pour plus d'informations sur l'implémentation d' `IVsProjectCfg2`, consultez [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).  
  
 Les projets de déploiement, qui gèrent le processus de déploiement, vérifiez la commande deploy et répondent quand cette commande est sélectionnée.  Les projets de déploiement implémentent l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> pour effectuer le déploiement et appeler à l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> pour stocker déployez les événements d'état.  
  
 Les configurations peuvent définir les dépendances qui affectent leurs opérations de génération ou de déploiement.  Générez ou déployez les dépendances sont des projets devant être générés ou déployés avant ou après que la configuration elles\-mêmes générées ou déployées.  Générez les dépendances entre les projets sont décrits par l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> et de déployer des dépendances avec l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> .  Pour plus d'informations, consultez [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md).  
  
## Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)