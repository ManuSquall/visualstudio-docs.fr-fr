---
title: Substitutions Help Content Manager | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e8657d2ff12e911286fd120d3d19e16aed838db6
ms.lasthandoff: 02/22/2017

---
# <a name="help-content-manager-overrides"></a>Substitutions Help Content Manager
Vous pouvez modifier le Registre pour modifier le comportement par défaut de la visionneuse d’aide et les fonctionnalités relatives à l’aide de l’IDE Visual Studio.  
  
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
 [Guide de l’administrateur de la visionneuse d’aide](../ide/help-viewer-administrator-guide.md)
