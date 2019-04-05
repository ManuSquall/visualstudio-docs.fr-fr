---
title: Vue d’ensemble du Cache ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58ea758ea10e2c58ff123a2bc991f14191db0aa1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953137"
---
# <a name="clickonce-cache-overview"></a>Vue d'ensemble du cache ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tous les [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications, qu’ils soient installés localement ou hébergés en ligne, sont stockées sur l’ordinateur client dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]application *cache*. Un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] cache est une famille de répertoires cachés sous le répertoire de paramètres locaux du dossier Documents and Settings de l’utilisateur actuel. Ce cache conserve tous les fichiers de l’application, y compris les assemblys, fichiers de configuration, application paramètres utilisateur et répertoire de données. Le cache est également responsable de la migration de l’annuaire de données de l’application vers la dernière version. Pour plus d’informations sur la migration des données, consultez [l’accès aux données locales et distantes dans les Applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 En fournissant un emplacement unique pour le stockage de l’application, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] prend en charge la tâche de gestion de l’installation physique d’une application à partir de l’utilisateur. Le cache permet également d’isoler les applications en conservant les assemblys et les fichiers de données pour toutes les applications et leurs versions distinctes séparent les uns des autres. Par exemple, lorsque vous mettez à niveau un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application, que la version et ses ressources de données sont fournis avec leurs propres répertoires dans le cache.  
  
## <a name="cache-storage-quota"></a>Quota de stockage de cache  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications hébergées en ligne ne peuvent occuper d’espace limitées par un quota qui limite la taille de la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] cache. La taille du cache s’applique aux applications en ligne de tous les l’utilisateur ; une seule application partiellement fiable, en ligne est limitée à occuper la moitié de l’espace de quota. Applications installées ne sont pas limitées par la taille du cache et ne sont pas comptés dans la limite de cache. Pour toutes les [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications, le cache conserve uniquement la version actuelle et la version précédemment installée.  
  
 Par défaut, les ordinateurs clients ont 250 Mo de stockage en ligne [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications. Fichiers de données ne comptent pas dans cette limite. Un administrateur système peut agrandir ou réduire ce quota sur un ordinateur client en modifiant la clé de Registre HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, qui est une valeur DWORD qui exprime la taille du cache en kilo-octets. Par exemple, afin de réduire la taille du cache de 50 Mo, vous modifieriez cette valeur 51200.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
