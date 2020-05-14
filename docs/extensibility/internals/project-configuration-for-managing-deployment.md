---
title: Configuration du projet pour la gestion du déploiement (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706708"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuration de projet pour la gestion du déploiement
Le déploiement est l’acte de déplacer physiquement les éléments de sortie d’un processus de construction à l’emplacement prévu pour le débogage et l’installation. Par exemple, une application Web peut être construite sur une machine locale, puis placée sur le serveur.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]soutient deux façons dont les projets peuvent participer au déploiement :

- Comme sujet du processus de déploiement.

- En tant que gestionnaire du processus de déploiement.

  Avant de pouvoir déployer des solutions, vous devez d’abord ajouter un projet de déploiement pour configurer les options de déploiement. Si le projet de déploiement n’existe pas déjà, on vous demande si vous souhaitez en créer un lorsque vous **sélectionnez Deploy Solution** dans le menu **Build** ou en cliquez à droite sur la solution. Clicking **Yes** ouvre la boîte de dialogue **Add New Project** avec le projet Remote Deploy **Wizard** sélectionné.

  Le Remote Deploy Wizard vous demande le type d’application (Windows ou Web), les groupes de sortie du projet à inclure, tous les fichiers supplémentaires que vous souhaitez inclure, et l’ordinateur distant que vous souhaitez déployer. La dernière page de l’assistant affiche un résumé des options sélectionnées.

  Les projets qui font l’objet d’un processus de déploiement produisent des éléments de sortie qui doivent être déplacés vers un environnement alternatif. Ces éléments de sortie sont <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> décrits comme des paramètres pour l’interface, dont le but principal si de permettre aux projets de regrouper les sorties. Pour plus d’informations `IVsProjectCfg2`sur la mise en œuvre de , voir [Configuration du projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).

  Les projets de déploiement, qui gèrent le processus de déploiement, permettent au commandement De déploiement et répondent lorsque cette commande est sélectionnée. Les projets <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> de déploiement implémentent <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> l’interface pour effectuer le déploiement et effectuent des appels vers l’interface pour signaler les événements d’état de déploiement.

  Les configurations peuvent spécifier les dépendances qui affectent leurs opérations de construction ou de déploiement. Construire ou déployer des dépendances sont des projets qui doivent être construits ou déployés avant ou après la construction ou le déploiement des configurations elles-mêmes. Les dépendances de construction entre <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> les projets sont <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> décrites avec l’interface et déploient des dépendances avec l’interface. Pour plus d’informations, voir [Configuration du projet pour la construction](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)
