---
title: Désactiver les avertissements de compatibilité pour les plug-ins de contrôle des sources (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710726"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Comment : Désactiver les avertissements de compatibilité pour les plug-ins de contrôle des sources
Un utilisateur peut voir plusieurs avertissements de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]compatibilité lors de l’utilisation du contrôle des sources dans . Les avertissements présentés dépendent des capacités du plug-in de contrôle source et peuvent être désactivés comme détaillé ici.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Pour désactiver l’avertissement : « Assurer une intégration optimale du contrôle des sources avec Visual Studio »

- Définissez l’entrée de registre suivante (ajout de la valeur si nécessaire) :

   **HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0-SourceControl-DontDisplayCheckDotNETCompatible - dword:00000001**

   Cet avertissement est affiché[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] pour tous les non-plug-ins.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Pour désactiver l’avertissement : « Le fournisseur de contrôle source installé ne prend pas en charge toutes les capacités »

- Définissez les deux valeurs de registre suivantes (ajout des valeurs si nécessaire) :

     **HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0-SourceControl-WarnedOldMSSCCIProvider - dword:00000000**

    **HKEY_CURRENT_USER-Software-Microsoft-VisualStudio 8.0-SourceControl-UseOldSCC - dword:00000001**

     Cet avertissement est affiché si le plug-in de contrôle source ne prend pas explicitement en charge la réentrabilité pour plusieurs projets (c’est-à-dire s’il peut enregistrer un seul fichier et projet à la fois).

     Il est préférable de soutenir`SCC_CAP_REENTRANT` la réentreprésentation (capacité); ce faisant, supprimera cet avertissement. Toutefois, si ce support n’est pas possible, ces entrées de registre peuvent être définies.

## <a name="see-also"></a>Voir aussi
- [Drapeaux de capacité](../extensibility/capability-flags.md)
