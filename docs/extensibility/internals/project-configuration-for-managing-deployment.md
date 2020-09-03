---
title: Configuration de projet pour la gestion du déploiement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706708"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuration de projet pour la gestion du déploiement
Le déploiement est l’action de déplacer physiquement les éléments de sortie d’un processus de génération vers l’emplacement prévu pour le débogage et l’installation. Par exemple, une application Web peut être générée sur un ordinateur local, puis placée sur le serveur.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge deux méthodes d’interprésence des projets dans le déploiement :

- Dans le cadre du processus de déploiement.

- En tant que responsable du processus de déploiement.

  Avant de pouvoir déployer des solutions, vous devez d’abord ajouter un projet de déploiement pour configurer les options de déploiement. Si le projet de déploiement n’existe pas encore, il vous est demandé si vous souhaitez en créer un lorsque vous sélectionnez **déployer la solution** dans le menu **générer** ou lorsque vous cliquez avec le bouton droit sur la solution. Cliquer sur **Oui** ouvre la boîte de dialogue **Ajouter un nouveau projet** avec l’option projet de l' **Assistant déploiement distant** sélectionnée.

  L’Assistant déploiement à distance vous demande le type d’application (Windows ou Web), les groupes de sorties de projet à inclure, les fichiers supplémentaires que vous souhaitez inclure et l’ordinateur distant sur lequel vous souhaitez effectuer le déploiement. La dernière page de l’Assistant affiche un résumé des options sélectionnées.

  Les projets faisant l’objet d’un processus de déploiement produisent des éléments de sortie qui doivent être déplacés vers un autre environnement. Ces éléments de sortie sont décrits comme paramètres pour l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interface, dont l’objectif principal est de permettre aux projets de regrouper les sorties. Pour plus d’informations sur l’implémentation de `IVsProjectCfg2` , consultez [configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).

  Les projets de déploiement, qui gèrent le processus de déploiement, activent la commande déployer et répondent lorsque cette commande est sélectionnée. Les projets de déploiement implémentent l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interface pour effectuer le déploiement et effectuer des appels à l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interface pour signaler des événements d’état de déploiement.

  Les configurations peuvent spécifier des dépendances qui affectent leurs opérations de génération ou de déploiement. Les dépendances de génération ou de déploiement sont des projets qui doivent être générés ou déployés avant ou après que les configurations elles-mêmes sont générées ou déployées. Les dépendances de build entre les projets sont décrites avec l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interface et déploient des dépendances avec l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interface. Pour plus d’informations, consultez [configuration de projet pour la génération](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)
