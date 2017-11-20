---
title: "Désactiver les avertissements de compatibilité pour les Plug-ins de contrôle de code Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93db7526e7d6ba3eccf86e8c9769a1d9e9af3519
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Comment : désactiver les avertissements de compatibilité pour les Plug-ins de contrôle de code Source
Un utilisateur peut voir plusieurs avertissements de compatibilité lors de l’utilisation du contrôle de code source [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les avertissements de varient selon les fonctionnalités du contrôle de source de plug-in et peuvent être désactivés comme décrit ici.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Pour désactiver l’avertissement : « s’assurer l’intégration du contrôle source optimale avec Visual Studio... »  
  
-   Définir l’entrée de Registre suivante (en ajoutant la valeur si nécessaire) :  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD : 00000001  
  
     Cet avertissement s’affiche pour tous les non -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Pour désactiver l’avertissement : « le fournisseur de contrôle de code source installé ne prend pas en charge toutes les fonctions »  
  
-   Définir les deux valeurs suivantes (en ajoutant les valeurs si nécessaire) :  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD : 00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD : 00000001  
  
     Cet avertissement s’affiche si le plug-in de contrôle de code source ne pas explicitement prend en charge la réentrance pour plusieurs projets (autrement dit, s’il peut vérifier dans un seul fichier et un projet à la fois).  
  
     Il est préférable de prendre en charge la réentrance (`SCC_CAP_REENTRANT` capacité) ; cela entraîne la suppression cet avertissement. Toutefois, si cette prise en charge n’est pas possible, vous peuvent définir ces entrées de Registre.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de capacité](../extensibility/capability-flags.md)