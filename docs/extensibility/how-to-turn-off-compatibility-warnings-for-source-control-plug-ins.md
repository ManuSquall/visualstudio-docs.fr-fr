---
title: Désactiver les avertissements pour les plug-ins de contrôle de code source
description: Un utilisateur peut voir plusieurs avertissements de compatibilité lors de l’utilisation du contrôle de code source dans Visual Studio. Découvrez comment désactiver ces avertissements.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ced04b09f8d4442cf0769ef503ee52772eccc0f6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905746"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Comment : désactiver les avertissements de compatibilité pour les plug-ins de contrôle de code source

Un utilisateur peut voir plusieurs avertissements de compatibilité lors de l’utilisation du contrôle de code source dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Les avertissements présentés dépendent des fonctionnalités du plug-in de contrôle de code source et peuvent être désactivés comme indiqué ici.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Pour désactiver l’avertissement : « pour garantir une intégration optimale du contrôle de code source à Visual Studio »

- Définissez l’entrée de Registre suivante (en ajoutant la valeur si nécessaire) :

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD : 00000001**

   Cet avertissement s’affiche pour tous les non [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Pour désactiver l’avertissement : « le fournisseur de contrôle de code source installé ne prend pas en charge toutes les fonctionnalités »

- Définissez les deux valeurs de Registre suivantes (en ajoutant les valeurs si nécessaire) :

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD : 00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD : 00000001**

     Cet avertissement s’affiche si le plug-in de contrôle de code source ne prend pas explicitement en charge la réentrance pour plusieurs projets (autrement dit, s’il peut archiver un seul fichier et un seul projet à la fois).

     Il est préférable de prendre en charge la réentrance ( `SCC_CAP_REENTRANT` fonctionnalité). cette opération supprime cet avertissement. Toutefois, si cette prise en charge n’est pas possible, ces entrées de Registre peuvent être définies.

## <a name="see-also"></a>Voir aussi

- [Indicateurs de capacité](../extensibility/capability-flags.md)
