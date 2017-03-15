---
title: "Désactiver les avertissements de compatibilité pour les Plug-ins de contrôle de code Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: e1dda3bd8c41efcf74a1b27f764fdfbf817f8d63
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Comment : désactiver les avertissements de compatibilité pour les Plug-ins de contrôle de code Source
Un utilisateur peut afficher plusieurs avertissements de compatibilité lors de l’utilisation du contrôle de code source dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les avertissements de dépendant des fonctionnalités de contrôle de source de plug-in et peuvent être désactivés comme décrit ici.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Pour désactiver l’avertissement : « s’assurer l’intégration du contrôle source optimale avec Visual Studio... »  
  
-   Définissez l’entrée de Registre suivante (en ajoutant la valeur si nécessaire) :  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD :&00000;001  
  
     Cet avertissement s’affiche pour tous les autres[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Pour désactiver l’avertissement : « le fournisseur de contrôle de code source installé ne prend pas en charge toutes les fonctions »  
  
-   Définissez les deux valeurs suivantes (en ajoutant les valeurs si nécessaire) :  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD :&00000;000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD :&00000;001  
  
     Cet avertissement s’affiche si le plug-in de contrôle de code source ne pas explicitement en charge réentrance pour plusieurs projets (autrement dit, s’il peut vérifier qu’un seul fichier et de projet à la fois).  
  
     Il est préférable de prendre en charge la réentrance (`SCC_CAP_REENTRANT` capacité) ; cette opération entraîne la suppression cet avertissement. Toutefois, si ce n’est pas possible, vous peuvent définir ces entrées de Registre.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de capacité](../extensibility/capability-flags.md)
