---
title: Vue d’ensemble du cache ClickOnce | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151663"
---
# <a name="clickonce-cache-overview"></a>Vue d'ensemble du cache ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toutes les [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications, qu’elles soient installées localement ou hébergées en ligne, sont stockées sur l’ordinateur client dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] *cache*d’application. Un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] cache est une famille de répertoires masqués sous le répertoire des paramètres locaux du dossier Documents and Settings de l’utilisateur actuel. Ce cache contient tous les fichiers de l’application, y compris les assemblys, les fichiers de configuration, les paramètres de l’application et de l’utilisateur, ainsi que le répertoire des données. Le cache est également chargé de migrer le répertoire de données de l’application vers la version la plus récente. Pour plus d’informations sur la migration de données, consultez [accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 En fournissant un emplacement unique pour le stockage des applications, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] prend la tâche de gérer l’installation physique d’une application à partir de l’utilisateur. Le cache permet également d’isoler les applications en conservant les assemblys et les fichiers de données pour toutes les applications et leurs versions distinctes séparément les unes des autres. Par exemple, lorsque vous mettez à niveau une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application, cette version et ses ressources de données sont fournies avec leurs propres répertoires dans le cache.  
  
## <a name="cache-storage-quota"></a>Quota de stockage de cache  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] les applications hébergées en ligne sont limitées dans la quantité d’espace qu’ils peuvent occuper par un quota qui limite la taille du [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] cache. La taille du cache s’applique à toutes les applications en ligne de l’utilisateur. une seule application en ligne de confiance partielle est limitée à la moitié de l’espace de quota. Les applications installées ne sont pas limitées par la taille du cache et ne sont pas comptabilisées par rapport à la limite du cache. Pour toutes les [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications, le cache conserve uniquement la version actuelle et la version installée précédemment.  
  
 Par défaut, les ordinateurs clients disposent de 250 Mo de stockage pour les applications en ligne [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Les fichiers de données ne sont pas comptabilisés dans cette limite. Un administrateur système peut agrandir ou réduire ce quota sur un ordinateur client particulier en modifiant la clé de Registre HKEY_CURRENT_USER \Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, qui est une valeur DWORD qui exprime la taille du cache en kilo-octets. Par exemple, pour réduire la taille du cache à 50 Mo, vous devez remplacer cette valeur par 51200.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
