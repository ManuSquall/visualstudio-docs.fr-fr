---
title: ClickOnce et paramètres d’Application | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2aa565721bc934fb78a7b183b0e4b4b637bafaf8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503165"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce et paramètres d'application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [ClickOnce et paramètres d’Application](https://docs.microsoft.com/visualstudio/deployment/clickonce-and-application-settings).  
  
Paramètres d’application pour Windows Forms rend plus facile à créer, stocker et gérer des applications personnalisées et préférences de l’utilisateur sur le client. Le document suivant explique le fonctionnement des fichiers de paramètres d’application dans une application ClickOnce, et comment ClickOnce migre les paramètres lorsque l’utilisateur met à niveau vers la prochaine version.  
  
 Les informations ci-dessous s’appliquent uniquement à un fournisseur de paramètres d’application par défaut, le <xref:System.Configuration.LocalFileSettingsProvider> classe. Si vous fournissez un fournisseur personnalisé, ce fournisseur détermine comment il stocke ses données et comment il met à niveau ses paramètres entre les versions. Pour plus d’informations sur les fournisseurs de paramètres d’application, consultez [Application Settings Architecture](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>Fichiers de paramètres d’application  
 Paramètres d’application consomment deux fichiers : *application*. exe.config et user.config, où *application* est le nom de votre application Windows Forms. User.config est créé sur la client la première fois que votre application stocke des paramètres de portée utilisateur. *application*. exe.config, en revanche, existera avant le déploiement si vous définissez les valeurs par défaut pour les paramètres. Visual Studio inclut ce fichier automatiquement lorsque vous utilisez sa **publier** commande. Si vous créez votre application ClickOnce à l’aide de Mage.exe ou MageUI.exe, vous devez vous assurer que ce fichier est inclus avec votre application des autres fichiers de lorsque vous remplissez votre manifeste d’application.  
  
 Dans les applications Windows Forms ne pas déployé à l’aide de ClickOnce, une application *application*. fichier exe.config est stockée dans le répertoire de l’application, tandis que le fichier user.config est stocké dans l’utilisateur **Documents and Settings**  dossier. Dans une application ClickOnce, *application*. exe.config dans le répertoire de l’application à l’intérieur du cache d’application ClickOnce, et User.config dans le répertoire de données ClickOnce pour cette application.  
  
 Quelle que soit la manière dont vous déployez votre application, paramètres de l’application garantissent un accès en lecture sécurisé à *application*. exe.config et accès en lecture/écriture sécurisé à user.config.  
  
 Dans une application ClickOnce, la taille des fichiers de configuration utilisé par les paramètres de l’application est limitée par la taille du cache ClickOnce. Pour plus d’informations, consultez [vue d’ensemble du Cache ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Mises à niveau de version  
 Tout comme chaque version d’une application ClickOnce est isolée de toutes les autres versions, les paramètres d’application pour une application ClickOnce sont isolés à partir des paramètres pour les autres versions ainsi. Quand votre utilisateur mis à niveau vers une version ultérieure de votre application, paramètres de l’application compare les paramètres de (la plus élevée numérotées) version la plus récente sur les paramètres fournis avec la version mise à jour et fusionnent les paramètres dans un nouvel ensemble de fichiers de paramètres.  
  
 Le tableau suivant décrit comment les paramètres de l’application déterminent les paramètres à copier.  
  
|Type de modification|Action de mise à niveau|  
|--------------------|--------------------|  
|Paramètre ajouté à *application*. exe.config|Le nouveau paramètre est fusionné dans la version actuelle *application*. exe.config|  
|Paramètre retiré *application*. exe.config|L’ancien paramètre est supprimé de la version actuelle *application*. exe.config|  
|Par défaut du paramètre changé ; paramètre locale est toujours définie sur la valeur par défaut d’origine dans le fichier user.config|Le paramètre est fusionné dans le fichier user.config de la version actuelle avec la nouvelle valeur par défaut en tant que la valeur|  
|Par défaut du paramètre changé ; paramètre la valeur par défaut dans le fichier user.config|Le paramètre est fusionné dans le fichier user.config de la version actuelle avec la valeur par défaut non conservée|  
  
 Si vous avez créé vos propres paramètres de l’application classe wrapper et que vous souhaitez personnaliser la logique de mise à jour, vous pouvez remplacer le <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> (méthode).  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce et paramètres d’itinérance  
 ClickOnce ne fonctionne pas avec les paramètres d’itinérance, qui permet à votre fichier de paramètres pour vous suivent sur plusieurs ordinateurs sur un réseau. Si vous avez besoin de paramètres d’itinérance, vous devrez soit implémenter un fournisseur de paramètres d’application qui stocke les paramètres sur le réseau ou développer vos propres classes de paramètres personnalisés pour stocker les paramètres sur un ordinateur distant. Pour plus d’informations dans les fournisseurs de paramètres, consultez [Application Settings Architecture](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Vue d’ensemble des paramètres d’application](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [Vue d’ensemble du Cache ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



