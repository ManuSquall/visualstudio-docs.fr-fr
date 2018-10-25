---
title: Désactiver les avertissements de compatibilité pour les Plug-ins de contrôle de code Source | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b1dca06ca82e467080f4bcd88a3b10c691345344
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888344"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Comment : désactiver les avertissements de compatibilité pour les plug-ins de contrôle de code source
Un utilisateur peut voir plusieurs avertissements de compatibilité lors de l’utilisation du contrôle de code source dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les avertissements de dépendant des fonctionnalités de plug-in du contrôle de code source et peuvent être désactivés comme décrit ici.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Pour désactiver l’avertissement : « s’assurer l’intégration du contrôle de code source optimale avec Visual Studio »  
  
- Définissez l’entrée de Registre suivante (en ajoutant la valeur si nécessaire) :  
  
   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD : 00000001**  
  
   Cet avertissement s’affiche pour tous les non -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Pour désactiver l’avertissement : « le fournisseur de contrôle de code source installé ne prend pas en charge toutes les fonctionnalités »  
  
-   Définir les deux valeurs suivantes (en ajoutant les valeurs si nécessaire) :  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD : 00000000**  
  
    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD : 00000001**  
  
     Cet avertissement s’affiche si le plug-in de contrôle de code source ne pas explicitement en charge la réentrance pour plusieurs projets (autrement dit, s’il peut vérifier dans un seul fichier et de projet à la fois).  
  
     Il est préférable de prendre en charge de la réentrance (`SCC_CAP_REENTRANT` capacité) ; Cela supprimera par conséquent, cet avertissement. Toutefois, si cette prise en charge n’est pas possible, vous peuvent définir ces entrées de Registre.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de capacité](../extensibility/capability-flags.md)