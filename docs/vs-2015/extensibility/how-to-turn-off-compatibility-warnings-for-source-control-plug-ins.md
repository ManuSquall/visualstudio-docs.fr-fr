---
title: 'Comment : désactiver les avertissements de compatibilité pour les Plug-ins de contrôle de code Source | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e77bfb81df5b9c30ae6b99076480f8ff72cd27a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273505"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Comment : désactiver les avertissements de compatibilité pour les Plug-ins de contrôle de code Source
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un utilisateur peut voir plusieurs avertissements de compatibilité lors de l’utilisation du contrôle de code source dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Les avertissements de dépendant des fonctionnalités de plug-in du contrôle de code source et peuvent être désactivés comme décrit ici.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Pour désactiver l’avertissement : « s’assurer l’intégration du contrôle de code source optimale avec Visual Studio... »  
  
-   Définissez l’entrée de Registre suivante (en ajoutant la valeur si nécessaire) :  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD : 00000001  
  
     Cet avertissement s’affiche pour tous les non -[!INCLUDE[vsvss](../includes/vsvss-md.md)] plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Pour désactiver l’avertissement : « le fournisseur de contrôle de code source installé ne prend pas en charge toutes les fonctionnalités »  
  
-   Définir les deux valeurs suivantes (en ajoutant les valeurs si nécessaire) :  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD : 00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD : 00000001  
  
     Cet avertissement s’affiche si le plug-in de contrôle de code source ne pas explicitement en charge la réentrance pour plusieurs projets (autrement dit, s’il peut vérifier dans un seul fichier et de projet à la fois).  
  
     Il est préférable de prendre en charge de la réentrance (`SCC_CAP_REENTRANT` capacité) ; Cela supprimera par conséquent, cet avertissement. Toutefois, si cette prise en charge n’est pas possible, vous peuvent définir ces entrées de Registre.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de capacité](../extensibility/capability-flags.md)

