---
title: "Configuration de la solution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurations de solution"
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Configuration de la solution
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Configurations de solution stockent les propriétés au niveau de la solution. Ils dirigent le comportement de la **Start** touche \(F5\) et **Build** commandes. Par défaut, ces commandes générer et démarrer la configuration debug. Les deux commandes s'exécutent dans le contexte d'une configuration de solution. Cela signifie que l'utilisateur peut attendre F5 pour démarrer et quelle que soit la solution active est configurée via les paramètres de build. L'environnement est conçu pour optimiser pour les solutions plutôt que des projets lorsqu'il s'agit de la création et l'exécution.  
  
 La barre d'outils standard de Visual Studio contient un bouton de démarrage et une liste déroulante à droite du bouton Démarrer de configuration de solution. Cette liste permet aux utilisateurs de choisir la configuration doit être démarré lorsque vous appuyez sur F5, leurs configurations de solution de créer ou modifier une configuration existante.  
  
> [!NOTE]
>  Il n'existe pas d'interfaces d'extensibilité pour créer ou modifier les configurations de solution. Vous devez utiliser `DTE.SolutionBuilder`. Toutefois, il existe API d'extensibilité pour la gestion de la génération. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Voici comment vous pouvez implémenter les configurations de solution prise en charge par votre type de projet :  
  
-   Projet  
  
     Affiche les noms des projets de la solution actuelle.  
  
-   Configuration  
  
     Pour fournir la liste des configurations prises en charge par votre type de projet et affichés dans les pages de propriétés, implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
     La colonne Configuration affiche le nom de la configuration de projet à créer dans cette configuration de solution et répertorie toutes les configurations de projet lorsque vous cliquez sur le bouton fléché. L'environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> méthode pour remplir cette liste. Si le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> méthode indique que le projet prend en charge la modification de configuration, nouveau ou modifier les sélections sont affichent également sous le titre de la Configuration. Chacun de ces sélections lancer des boîtes de dialogue appeler les méthodes de la `IVsCfgProvider2` interface pour modifier les configurations du projet.  
  
     Si un projet ne prend pas en charge les configurations, la colonne Configuration affiche aucun et est désactivée.  
  
-   Plateforme  
  
     Affiche la plate\-forme génère pour la configuration du projet sélectionné et répertorie toutes les plateformes disponibles pour le projet lorsque vous cliquez sur la flèche. L'environnement appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> méthode pour remplir cette liste. Si le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> méthode indique que le projet prend en charge la modification de la plateforme, nouveau ou modifier les sélections sont affichent également sous le titre de la plateforme. Chacun de ces sélections lancer des boîtes de dialogue qui appellent `IVsCfgProvider2` méthodes permettant de modifier les plateformes disponibles du projet.  
  
     Si un projet ne prend pas en charge les plates\-formes, la colonne de la plateforme pour ce projet affiche aucun et est désactivée.  
  
-   Build  
  
     Spécifie si le projet est généré par la configuration de solution en cours. Projets non sélectionnés ne sont pas générés lorsque les commandes de génération au niveau de la solution sont appelées en dépit de toutes les dépendances de projet qu'ils contiennent. Projets non sélectionnés pour être générées sont toujours inclus dans le débogage en cours d'exécution, empaquetage et déploiement de la solution.  
  
-   Déployer  
  
     Spécifie si le projet doit être déployé lorsque la commande Démarrer ou déployer est utilisée avec la configuration de build de solution sélectionnée. La case à cocher pour ce champ sera disponible si le projet prend en charge le déploiement en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface sur son <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objet.  
  
 Une fois qu'une nouvelle configuration de solution est ajoutée, l'utilisateur peut le sélectionner dans la zone de liste déroulante Configuration de Solution sur la barre d'outils standard pour construire et\/ou démarrer cette configuration.  
  
## Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)   
 [Objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md)