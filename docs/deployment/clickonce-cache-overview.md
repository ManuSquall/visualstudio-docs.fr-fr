---
title: Vue d’ensemble du cache ClickOnce | Microsoft Docs
description: Découvrez le cache d’application ClickOnce, qui comprend des répertoires cachés sur un ordinateur client sur lequel sont stockées les applications ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 12c14850717688b17caed2fbe7feb546e0ebdb6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936169"
---
# <a name="clickonce-cache-overview"></a>Vue d’ensemble du cache ClickOnce
Toutes les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications, qu’elles soient installées localement ou hébergées en ligne, sont stockées sur l’ordinateur client dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *cache* d’application. Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache est une famille de répertoires masqués sous le répertoire des paramètres locaux du dossier Documents and Settings de l’utilisateur actuel. Ce cache contient tous les fichiers de l’application, y compris les assemblys, les fichiers de configuration, les paramètres de l’application et de l’utilisateur, ainsi que le répertoire des données. Le cache est également chargé de migrer le répertoire de données de l’application vers la version la plus récente. Pour plus d’informations sur la migration de données, consultez [accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

 En fournissant un emplacement unique pour le stockage des applications, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] prend la tâche de gérer l’installation physique d’une application à partir de l’utilisateur. Le cache permet également d’isoler les applications en conservant les assemblys et les fichiers de données pour toutes les applications et leurs versions distinctes séparément les unes des autres. Par exemple, lorsque vous mettez à niveau une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, cette version et ses ressources de données sont fournies avec leurs propres répertoires dans le cache.

## <a name="cache-storage-quota"></a>Quota de stockage de cache
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les applications hébergées en ligne sont limitées dans la quantité d’espace qu’ils peuvent occuper par un quota qui limite la taille du [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache. La taille du cache s’applique à toutes les applications en ligne de l’utilisateur. une seule application en ligne de confiance partielle est limitée à la moitié de l’espace de quota. Les applications installées ne sont pas limitées par la taille du cache et ne sont pas comptabilisées par rapport à la limite du cache. Pour toutes les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications, le cache conserve uniquement la version actuelle et la version installée précédemment.

 Par défaut, les ordinateurs clients disposent de 250 Mo de stockage pour les applications en ligne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Les fichiers de données ne sont pas comptabilisés dans cette limite. Un administrateur système peut agrandir ou réduire ce quota sur un ordinateur client particulier en modifiant la clé de Registre **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB**, qui est une valeur DWORD qui exprime la taille du cache en kilo-octets. Par exemple, pour réduire la taille du cache à 50 Mo, vous devez remplacer cette valeur par 51200.

## <a name="see-also"></a>Voir aussi
- [Accéder aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)