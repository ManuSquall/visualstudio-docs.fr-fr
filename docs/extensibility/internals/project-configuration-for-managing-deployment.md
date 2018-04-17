---
title: Configuration de projet pour la gestion du déploiement | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 723edd078636eb324fc2d5dfca2ae81ef3249a43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="project-configuration-for-managing-deployment"></a>Configuration de projet pour la gestion du déploiement
Déploiement consiste à déplacer physiquement les éléments de sortie à partir d’un processus de génération à l’emplacement prévu pour l’installation et de débogage. Par exemple, une application Web peut être créée sur un ordinateur local et puis placée sur le serveur.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge que les projets peuvent être impliqués dans le déploiement de deux manières :  
  
-   En tant que le sujet du processus de déploiement.  
  
-   En tant que le Gestionnaire du processus de déploiement.  
  
 Avant de pouvoir déployer des solutions, vous devez d’abord ajouter un projet de déploiement pour configurer des options de déploiement. Si le projet de déploiement n’existe pas déjà, vous êtes invité si vous souhaitez créer une lorsque vous sélectionnez **déployer la Solution** à partir de la **générer** menu ou sélectionnez la solution. En cliquant sur **Oui** ouvre le **ajouter un nouveau projet** boîte de dialogue avec le **Assistant de déploiement à distance** projet sélectionné.  
  
 L’Assistant de déploiement à distance vous demande pour le type d’application (Windows ou Web), les groupes de sortie de projet à inclure, tous les fichiers supplémentaires à inclure et l’ordinateur distant que vous souhaitez déployer sur. La dernière page de l’Assistant affiche un résumé des options sélectionnées.  
  
 Les projets qui font l’objet d’un processus de déploiement de produisent des éléments de sortie qui doivent être déplacés vers un autre environnement. Ces éléments sont décrits en tant que paramètres pour de sortie du <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interface, dont le principal objectif s’il faut autoriser les sorties de groupe des projets. Pour plus d’informations sur l’implémentation de `IVsProjectCfg2`, consultez [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).  
  
 Projets de déploiement, qui gèrent le processus de déploiement, activent la commande déployer et répondent quand cette commande est sélectionnée. Implémentent des projets de déploiement de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface pour effectuer le déploiement et d’effectuer des appels à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interface au rapport déployer des événements d’état.  
  
 Les configurations peuvent spécifier les dépendances qui affectent leurs opérations de génération ou de déploiement. Générez ou déployez dépendances sont des projets qui doivent être générées ou déployés avant ou après les configurations eux-mêmes sont créées ou déployées. Créer des dépendances entre les projets sont décrites avec le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> de l’interface et le déploiement des dépendances avec le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interface. Pour plus d’informations, consultez [Configuration de projet pour la génération de](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la génération](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)