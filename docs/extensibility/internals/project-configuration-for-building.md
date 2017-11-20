---
title: "Configuration pour la génération de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f89736c448570157711c15d2d86091d91e1f30d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-for-building"></a>Configuration de projet pour la génération
La liste des configurations de solution pour une solution donnée est gérée par la boîte de dialogue des Configurations de Solution.  
  
 Un utilisateur peut créer d’autres configurations de solutions, chacune avec son propre nom unique. Lorsque l’utilisateur crée une nouvelle configuration de solution, l’IDE par défaut est le nom de configuration correspondant dans les projets, ou débogage si aucun nom correspondant existe. L’utilisateur peut modifier la sélection en fonction des besoins si nécessaire. La seule exception à ce comportement est lorsque le projet prend en charge une configuration qui correspond au nom de la nouvelle configuration de solution. Par exemple, supposons qu'une solution contient Project1 et Project2. Project1 a des configurations de projet Debug, commerciale et MyConfig1. Projet2 a des configurations de projet Debug, commerciale et MyConfig2.  
  
 Si l’utilisateur crée une nouvelle configuration de solution nommée MyConfig2, Projet1 lie sa configuration de débogage à la configuration de solution par défaut. Projet2 lie également sa configuration MyConfig2 à la configuration de solution par défaut.  
  
> [!NOTE]
>  Liaison respecte la casse.  
  
 Lorsque l’utilisateur sélectionne le **sélection Multiple** élément dans la liste déroulante de configuration, l’environnement affiche une boîte de dialogue qui fournit la liste des configurations disponibles.  
  
 ![Plusieurs Configurations](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Plusieurs configurations  
  
 Dans cette boîte de dialogue, l’utilisateur peut sélectionner une ou plusieurs configurations. Une fois sélectionné, les valeurs de propriété affichées sur la boîte de dialogue des pages de propriétés reflètent l’intersection des valeurs pour les configurations sélectionnées.  
  
 Consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md) pour plus d’informations relatives à l’ajout et la modification du nom des configurations pour les solutions et projets.  
  
 Dépendances du projet et l’ordre de génération sont configuration indépendante de la solution : autrement dit, vous ne pouvez configurer arborescence une dépendance pour tous les projets dans la solution. Clic droit sur la solution ou le projet et en sélectionnant le **dépendances du projet** ou **ordre de génération de projet** option ouvre le **dépendances du projet** boîte de dialogue. Il peut également être ouvert à partir de la **projet** menu.  
  
 ![Dépendances du projet](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Dépendances du projet  
  
 Dépendances du projet déterminent l’ordre dans lequel les projets sont générés. Utilisez l’onglet de l’ordre de la génération dans la boîte de dialogue pour afficher l’ordre exact dans lequel les projets dans une solution générer et utilisez l’onglet dépendances pour modifier l’ordre de génération.  
  
> [!NOTE]
>  Dans la liste des projets qui ont leurs cases à cocher activées mais grisées ont été ajoutés par l’environnement en raison des dépendances explicites, spécifié par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> des interfaces et ne peut pas être modifié. Par exemple, ajoutez une référence de projet dans un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projet vers un autre projet ajoute automatiquement une dépendance de génération qui ne peut être supprimée en supprimant la référence. Les projets dont les cases à cocher sont désactivées et apparaissent grisés ne peut pas être sélectionnés, car cela créerait une boucle de dépendance (par exemple, Projet1 serait dépend Projet2 et Projet2 serait dépend Projet1), ce qui serait bloquer la génération.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]processus de génération incluent la compilation classique et les opérations de liaison qui sont appelées avec une seule commande Build. Deux autres processus de génération peuvent également être pris en charge : une opération de nettoyage pour supprimer tous les éléments de sortie à une version antérieure et une vérification à jour pour déterminer si un élément de sortie dans une configuration a changé.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>objets de retournent un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (retourné par <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) pour gérer leurs processus de génération. Pour signaler l’état d’une opération de génération lorsqu’elle se produit, les configurations effectuent des appels vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, une interface implémentée par l’environnement et tout autre objet intéressés par les événements de statut de build.  
  
 Une fois généré, les paramètres de configuration permet de déterminer si ils peuvent être exécutés sous le contrôle du débogueur. Implémentent des configurations <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> pour prendre en charge le débogage.  
  
 Après avoir implémenté les dépendances du projet, vous pouvez manipuler par programme les dépendances via le modèle automation. Vous appelez <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> dans le modèle automation. Il n’existe aucune interface au niveau de l’API VSIP disponibles qui permettre du manipuler directement les configurations de gestionnaire de build de solution et leurs propriétés.  
  
 En outre, vous pouvez fournir une grille dans la fenêtre de dépendances du projet. Pour plus d’informations, consultez [afficher la grille Propriétés](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la gestion du déploiement](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)