---
title: Changements dans Help Content Manager | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2fae83a05b3f6f8774e7ed119483274f22c4ddc3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502765"
---
# <a name="help-content-manager-overrides"></a>Changements dans Help Content Manager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [substitutions Help Content Manager](https://docs.microsoft.com/visualstudio/ide/help-content-manager-overrides).  
  
Vous pouvez modifier le Registre pour changer le comportement par défaut de la visionneuse et des fonctionnalités de l’aide dans l’IDE Visual Studio.  
  
|Tâche|Clé de Registre|Valeur et définition|  
|----------|------------------|--------------------------|  
|Définir le point de terminaison de service unique|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*.|  
|Définir le paramètre en ligne/hors ligne par défaut|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp--Entrez `0` pour spécifier l’aide locale, et `1` pour spécifier l’aide en ligne.|  
|Définir le point de terminaison unique F1|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|Substituer la priorité des travaux BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (sur un ordinateur 64 bits)\Microsoft\Help\v2.2|BITSPriority--Utilisez l’une des valeurs suivantes : **foreground**, **high**, **normal** ou **low**.|  
|Désactiver en ligne (et option IDE en ligne)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (sur un ordinateur 64 bits)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled--Indiquez la valeur 1 pour désactiver l’accès au contenu d’aide en ligne.|  
|Désactiver Gérer le contenu|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (sur un ordinateur 64 bits)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled--Indiquez la valeur 1 pour désactiver l’onglet **Gérer le contenu** dans la visionneuse d’aide.|  
|Pointer vers le magasin de contenu local sur un partage réseau|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath=« *ContentStoreNetworkShare* »|  
|Désactiver l’installation du contenu au premier démarrage de la fonctionnalité Visual Studio.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (sur un ordinateur 64 bits)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection--Définir sur 1 pour désactiver les fonctionnalités d’aide configurées au premier démarrage de Visual Studio.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de l’administrateur Help Viewer](../ide/help-viewer-administrator-guide.md)



