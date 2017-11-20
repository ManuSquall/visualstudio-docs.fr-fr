---
title: "Vue d’ensemble du Cache ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1aa73140760f161971f30e4232658b18453f233f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-cache-overview"></a>Vue d'ensemble du cache ClickOnce
Tous les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications, qu’ils soient installés localement ou hébergés en ligne, sont stockées sur l’ordinateur client dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]application *cache*. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache est une famille de répertoires cachés sous le répertoire Local Settings du dossier Documents and Settings de l’utilisateur actuel. Ce cache contient tous les fichiers de l’application, y compris les assemblys, les fichiers de configuration, application et paramètres utilisateur et répertoire de données. Le cache est également responsable de la migration de l’annuaire de données de l’application vers la dernière version. Pour plus d’informations sur la migration des données, consultez [l’accès aux données locales et distantes dans les Applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 En fournissant un emplacement unique pour le stockage de l’application, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] prend en charge la tâche de gestion de l’installation physique d’une application à partir de l’utilisateur. Le cache permet également d’isoler les applications en conservant les assemblys et les fichiers de données pour toutes les applications et leurs versions distinctes séparés à partir d’un autre. Par exemple, lorsque vous mettez à niveau un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, que la version et ses ressources de données sont fournis avec leurs propres répertoires dans le cache.  
  
## <a name="cache-storage-quota"></a>Quota de stockage du cache  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]les applications qui sont hébergées en ligne sont espace peuvent occuper limitées par un quota qui limite la taille de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache. La taille du cache s’applique aux applications en ligne de toutes les l’utilisateur ; une seule application de niveau de confiance partiel en ligne est limitée à occuper la moitié de l’espace de quota. Applications installées ne sont pas limitées par la taille du cache et ne comptent pas par rapport à la limite de cache. Pour toutes les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications, le cache conserve uniquement la version actuelle et la version installée précédemment.  
  
 Par défaut, les ordinateurs clients ont 250 Mo de stockage en ligne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications. Fichiers de données ne comptent pas pour cette limite. Un administrateur système peut agrandir ou réduire ce quota sur un ordinateur client en modifiant la clé de Registre HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, qui est une valeur DWORD qui indique la taille du cache en kilo-octets. Par exemple, pour réduire la taille du cache à 50 Mo, passe cette valeur à 51200.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)