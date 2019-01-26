---
title: Configuration de projet pour la gestion du déploiement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b4165a367a029bc0d226f7fce55f3b2929d0f965
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936280"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuration de projet pour la gestion du déploiement
Déploiement consiste à déplacer physiquement les éléments de sortie à partir d’un processus de génération à l’emplacement attendu pour l’installation et de débogage. Par exemple, une application Web peut être créée sur un ordinateur local et puis placée sur le serveur.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge que les projets peuvent être impliqués dans le déploiement de deux manières :  
  
- En tant que le sujet du processus de déploiement.  
  
- En tant que responsable du processus de déploiement.  
  
  Avant de pouvoir déployer des solutions, vous devez d’abord ajouter un projet de déploiement pour configurer les options de déploiement. Si le projet de déploiement n’existe pas déjà, vous êtes invité si vous souhaitez le faire lorsque vous sélectionnez **déployer la Solution** à partir de la **Build** menu ou sélectionnez la solution. En cliquant sur **Oui** ouvre le **ajouter un nouveau projet** boîte de dialogue avec le **Assistant de déploiement à distance** projet sélectionné.  
  
  L’Assistant de déploiement à distance vous demande pour le type d’application (Windows ou Web), les groupes de sortie de projet à inclure, tous les fichiers que vous souhaitez inclure et l’ordinateur distant que vous souhaitez déployer sur. La dernière page de l’Assistant affiche un résumé des options sélectionnées.  
  
  Les projets qui font l’objet d’un processus de déploiement produisent des éléments de sortie doivent être déplacés vers un autre environnement. De sortie de ces éléments sont décrits en tant que paramètres pour le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interface, dont le principal objectif if pour permettre aux projets à regrouper les sorties. Pour plus d’informations sur l’implémentation de `IVsProjectCfg2`, consultez [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).  
  
  Projets de déploiement, qui gèrent le processus de déploiement, activent la commande de déploiement et répondent lorsque cette commande est sélectionnée. Implémentent des projets de déploiement le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface pour effectuer le déploiement et d’effectuer des appels vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interface au rapport déployer des événements d’état.  
  
  Configurations peuvent spécifier les dépendances qui affectent leurs opérations de génération ou de déploiement. Générez ou déployez les dépendances sont des projets qui doivent être créés ou déployés avant ou après les configurations proprement dits sont créées ou déployées. Créer des dépendances entre projets sont décrites avec les <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interface et le déploiement des dépendances avec le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interface. Pour plus d’informations, consultez [Configuration de projet pour la création de](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)