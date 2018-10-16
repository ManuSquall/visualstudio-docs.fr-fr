---
title: Configuration pour la génération de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bcac8acced823f294c4e6dd33302e3eea30b0439
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221115"
---
# <a name="project-configuration-for-building"></a>Configuration de projet pour la création
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La liste des configurations de solution pour une solution donnée est gérée par la boîte de dialogue Configurations de Solution.  
  
 Un utilisateur peut créer des configurations de solution supplémentaires, chacune avec son propre nom unique. Lorsque l’utilisateur crée une nouvelle configuration de solution, l’IDE par défaut est le nom de configuration correspondant dans les projets, ou débogage si aucun nom correspondant existe. L’utilisateur peut modifier la sélection pour répondre aux exigences spécifiques si nécessaire. La seule exception à ce comportement est lorsque le projet prend en charge une configuration qui correspond au nom de la nouvelle configuration de solution. Par exemple, supposons qu'une solution contient Project1 et Project2. Project1 a des configurations de projet Debug et MyConfig1 vente au détail. Project2 a des configurations de projet Debug et MyConfig2 vente au détail.  
  
 Si l’utilisateur crée une nouvelle configuration de solution nommée MyConfig2, Projet1 lie sa configuration de débogage à la configuration de solution par défaut. Project2 lie également sa configuration MyConfig2 à la configuration de solution par défaut.  
  
> [!NOTE]
>  Liaison respecte la casse.  
  
 Lorsque l’utilisateur sélectionne le **sélection Multiple** élément dans la liste déroulante de configuration, l’environnement affiche une boîte de dialogue qui fournit la liste des configurations disponibles.  
  
 ![Plusieurs Configurations](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Plusieurs configurations  
  
 Dans cette boîte de dialogue, l’utilisateur peut sélectionner une ou plusieurs configurations. Une fois sélectionnée, les valeurs de propriété affichées sur la boîte de dialogue des pages de propriétés reflètent l’intersection des valeurs pour les configurations sélectionnées.  
  
 Consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md) pour plus d’informations relatives à l’ajout et la modification du nom des configurations pour les projets et solutions.  
  
 Dépendances du projet et l’ordre de génération sont configuration indépendante de la solution : autrement dit, vous pouvez uniquement définir arborescence d’une dépendance pour tous les projets dans la solution. Clic droit sur la solution ou le projet et en sélectionnant le **dépendances du projet** ou **ordre de génération de projet** option ouvre le **dépendances du projet** boîte de dialogue. Il peut également être ouvert à partir de la **projet** menu.  
  
 ![Dépendances du projet](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Dépendances du projet  
  
 Dépendances du projet déterminent l’ordre dans lequel les projets sont générés. Utilisez l’onglet de l’ordre de génération sur la boîte de dialogue pour afficher l’ordre exact dans lequel les projets au sein d’une solution de générer et utilisez l’onglet dépendances pour modifier l’ordre de génération.  
  
> [!NOTE]
>  Dans la liste des projets qui ont leurs cases à cocher activées mais grisées ont été ajoutés par l’environnement en raison des dépendances explicites spécifié par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaces et ne peut pas être modifié. Par exemple, ajoutez une référence de projet à partir d’un [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projet vers un autre projet ajoute automatiquement une dépendance de build qui peut être supprimée seulement en supprimant la référence. Les projets dont les cases à cocher sont claires et apparaissent grisés ne peuvent pas être sélectionnés, car cela créerait une boucle de dépendance (par exemple, Projet1 serait dépend Project2 et Project2 serait dépend Projet1), ce qui serait bloquer la génération.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] processus de génération incluent la compilation classique et les opérations de liaison qui sont appelées avec une seule commande de Build. Deux autres processus de génération peuvent également être pris en charge : une opération de nettoyage pour supprimer tous les éléments de sortie à une build précédente et une vérification à jour pour déterminer si un élément de sortie dans une configuration a changé.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> les objets renvoient un correspondant <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (retourné par <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) pour gérer leurs processus de génération. Pour signaler l’état d’une opération de génération lorsqu’elle se produit, configurations effectuer des appels vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, une interface implémentée par l’environnement et tout autre objet intéressés par les événements de statut de build.  
  
 Une fois généré, les paramètres de configuration peuvent être utilisés pour déterminer s’ils peuvent être exécutés sous le contrôle du débogueur. Implémentent des configurations <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> pour prendre en charge le débogage.  
  
 Après avoir implémenté les dépendances du projet, vous pouvez manipuler par programmation les dépendances via le modèle automation. Vous appelez <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> dans le modèle automation. Il n’existe aucune interface de niveau d’API VSIP disponibles qui permettent la manipulation directe de leurs propriétés et les configurations de gestionnaire de build de solution.  
  
 En outre, vous pouvez fournir une grille dans la fenêtre de dépendances du projet. Pour plus d’informations, consultez [afficher la grille Propriétés](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la gestion du déploiement](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)

