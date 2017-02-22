---
title: "ClickOnce Cache Overview | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Windows applications, ClickOnce deployemtn"
  - "ClickOnce applications, cache"
  - "ClickOnce deployment, cache"
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# ClickOnce Cache Overview
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Toutes les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], qu'elles soient installées localement ou hébergées en ligne, sont stockées sur l'ordinateur client dans un *cache* de l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Un cache [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est une famille de répertoires masqués qui se trouvent dans le répertoire Local Settings du dossier Documents and Settings de l'utilisateur actuel.  Ce cache contient tous les fichiers de l'application, y compris les assemblys, les fichiers de configuration, les paramètres de l'application et d'utilisateur et le répertoire de données.  Le cache a également pour fonction de migrer le répertoire de données de l'application vers la version la plus récente.  Pour plus d'informations sur la migration des données, consultez [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 En fournissant un emplacement unique pour le stockage d'application, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] prend en charge la gestion de l'installation physique d'une application et libère ainsi l'utilisateur de cette tâche.  Le cache aide également à isoler des applications en maintenant les assemblys et les fichiers de données de toutes les applications et leurs versions distinctes séparés l'un de l'autre.  Par exemple, lorsque vous mettez à niveau une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], cette version et ses ressources de données sont fournies avec leur propre répertoire dans le cache.  
  
## Quota de stockage du cache  
 Les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] hébergées en ligne ne peuvent occuper qu'un espace limité par un quota défini pour la taille du cache [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La taille du cache s'applique à toutes les applications en ligne de l'utilisateur ; une application d'un niveau de confiance partiel en ligne unique est limitée à occuper la moitié de l'espace de quota.  Les applications installées ne sont pas limitées par la taille du cache et n'entrent pas en ligne de compte dans le calcul de la limite du cache.  Pour toutes les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], le cache conserve uniquement la version actuelle et la version installée précédemment.  
  
 Par défaut, les ordinateurs clients disposent d'un espace de stockage de 250 Mo pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en ligne.  Les fichiers de données ne comptent pas en direction cette limite.  Un administrateur système peut augmenter ou réduire ce quota sur un ordinateur client particulier en modifiant la clé de Registre, HKEY\_CURRENT\_USER\\Software\\Classes\\Software\\Microsoft\\Windows\\CurrentVersion\\Deployment\\OnlineAppQuotaInKB, qui est une valeur DWORD exprimant la taille du cache en kilo\-octets.  Par exemple, pour limiter la taille du cache à 50 Mo, vous pouvez définir cette valeur à 51200.  
  
## Voir aussi  
 [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)