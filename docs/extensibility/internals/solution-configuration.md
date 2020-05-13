---
title: Configuration de solution Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705379"
---
# <a name="solution-configuration"></a>Configuration de la solution
Les configurations de solutions stockent les propriétés au niveau des solutions. Ils dirigent le comportement de la clé **Démarrer** (F5) et **construire des** commandes. Par défaut, ces commandes construisent et démarrent la configuration de déboçon. Les deux commandes s’exécutent dans le cadre d’une configuration de solution. Cela signifie que l’utilisateur peut s’attendre à ce que F5 démarre et construise quelle que soit la solution active configurée à travers les paramètres. L’environnement est conçu pour optimiser les solutions plutôt que pour les projets lorsqu’il s’agit de construire et de fonctionner.

 La barre d’outils Visual Studio standard contient un bouton Démarrer et une configuration de solution descendante vers la droite du bouton Démarrer. Cette liste permet aux utilisateurs de choisir la configuration à démarrer lorsque F5 est pressé, de créer leurs propres configurations de solutions ou de modifier une configuration existante.

> [!NOTE]
> Il n’existe pas d’interfaces d’extabilité pour créer ou modifier les configurations de solutions. Vous devez utiliser `DTE.SolutionBuild`. Cependant, il existe des API d’extensibility pour la gestion de la construction de la solution. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Voici comment vous pouvez implémenter les configurations de solutions prises en charge par votre type de projet :

- Projet

   Affiche les noms des projets trouvés dans la solution actuelle.

- Configuration

   Pour fournir la liste des configurations prises en charge par <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>votre type de projet et affichées dans les pages de propriété, implémentez .

   La colonne Configuration affiche le nom de la configuration du projet pour construire dans cette configuration de solution, et répertorie toutes les configurations du projet lorsque vous cliquez sur le bouton flèche. L’environnement <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> appelle la méthode pour remplir cette liste. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> la méthode indique que le projet prend en charge l’édition de configuration, les sélections Nouvelles ou Modifier sont également affichées sous le titre Configuration. Chacune de ces sélections lance des `IVsCfgProvider2` boîtes de dialogue qui appellent les méthodes de l’interface pour modifier les configurations du projet.

   Si un projet ne prend pas en charge les configurations, la colonne Configuration n’affiche aucun et est désactivée.

- Plateforme

   Affiche la plate-forme pour laquelle la configuration de projet sélectionnée s’appuie et répertorie toutes les plates-formes disponibles pour le projet lorsque vous cliquez sur le bouton flèche. L’environnement <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> appelle la méthode pour remplir cette liste. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> la méthode indique que le projet prend en charge l’édition de la plate-forme, les sélections Nouvelles ou Edit sont également affichées sous le titre Platform. Chacune de ces sélections lance `IVsCfgProvider2` des boîtes de dialogue qui appellent des méthodes pour modifier les plates-formes disponibles du projet.

   Si un projet ne prend pas en charge les plates-formes, la colonne de plate-forme de ce projet affiche Aucun et est désactivée.

- Générer

   Précise si le projet est construit ou non par la configuration actuelle de la solution. Les projets non sélectionnés ne sont pas construits lorsque les commandes de construction au niveau de la solution sont invoquées malgré les dépendances du projet qu’ils contiennent. Les projets qui ne sont pas sélectionnés pour être construits sont toujours inclus dans le débogage, la course, l’emballage et le déploiement de la solution.

- Déployer

   Précise si le projet sera déployé ou non lorsque les commandes Démarrer ou déployer sont utilisées avec la configuration de construction de solution sélectionnée. La case à cocher de ce champ sera disponible <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> si le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> projet prend en charge le déploiement en implémentant l’interface sur son objet.

  Une fois qu’une nouvelle configuration de solution est ajoutée, l’utilisateur peut la sélectionner à partir de la boîte de liste d’abandon de configuration de solution sur la barre d’outils standard pour construire et/ou démarrer cette configuration.

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Objet de configuration de projet](../../extensibility/internals/project-configuration-object.md)
