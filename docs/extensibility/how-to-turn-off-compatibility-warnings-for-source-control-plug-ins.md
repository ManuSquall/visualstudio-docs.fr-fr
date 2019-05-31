---
title: Désactiver les avertissements de compatibilité pour les Plug-ins de contrôle de code Source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6dc8edcb6ee10be8b020424d8f8c247770a98f27
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324807"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Procédure : Désactiver les avertissements de compatibilité pour les plug-ins de contrôle de code source
Un utilisateur peut voir plusieurs avertissements de compatibilité lors de l’utilisation du contrôle de code source dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les avertissements de dépendant des fonctionnalités de plug-in du contrôle de code source et peuvent être désactivés comme décrit ici.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Pour désactiver l’avertissement : « S’assurer l’intégration du contrôle de code source optimale avec Visual Studio »

- Définissez l’entrée de Registre suivante (en ajoutant la valeur si nécessaire) :

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   Cet avertissement s’affiche pour tous les non -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Pour désactiver l’avertissement : « Le fournisseur de contrôle de code source installé ne prend pas en charge toutes les fonctionnalités »

- Définir les deux valeurs suivantes (en ajoutant les valeurs si nécessaire) :

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     Cet avertissement s’affiche si le plug-in de contrôle de code source ne pas explicitement en charge la réentrance pour plusieurs projets (autrement dit, s’il peut vérifier dans un seul fichier et de projet à la fois).

     Il est préférable de prendre en charge de la réentrance (`SCC_CAP_REENTRANT` capacité) ; Cela supprimera par conséquent, cet avertissement. Toutefois, si cette prise en charge n’est pas possible, vous peuvent définir ces entrées de Registre.

## <a name="see-also"></a>Voir aussi
- [Indicateurs de capacité](../extensibility/capability-flags.md)