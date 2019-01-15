---
title: ClickOnce et paramètres d’Application | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40077a30a49842187c24b4cf8b0cba18b3d0a46a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850964"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce et paramètres d’application
Paramètres d’application pour Windows Forms rend plus facile à créer, stocker et gérer des applications personnalisées et préférences de l’utilisateur sur le client. Le document suivant explique le fonctionnement des fichiers de paramètres d’application dans une application ClickOnce, et comment ClickOnce migre les paramètres lorsque l’utilisateur met à niveau vers la prochaine version.  
  
 Les informations ci-dessous s’appliquent uniquement à un fournisseur de paramètres d’application par défaut, le \<xref:System.Configuration.LocalFileSettingsProvider > classe. Si vous fournissez un fournisseur personnalisé, ce fournisseur détermine comment il stocke ses données et comment il met à niveau ses paramètres entre les versions. Pour plus d’informations sur les fournisseurs de paramètres d’application, consultez [architecture des paramètres d’Application](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="application-settings-files"></a>Fichiers de paramètres d’application  
 Paramètres d’application consomment deux fichiers :  *\<application >. exe.config* et *user.config*, où *application* est le nom de votre application Windows Forms. *User.config* est créé sur la client la première fois que votre application stocke des paramètres de portée utilisateur. *\<application >. exe.config*, en revanche, existera avant le déploiement si vous définissez les valeurs par défaut pour les paramètres. Visual Studio inclut ce fichier automatiquement lorsque vous utilisez sa **publier** commande. Si vous créez votre application ClickOnce à l’aide *Mage.exe* ou *MageUI.exe*, vous devez vous assurer que ce fichier est inclus avec votre application des autres fichiers de lorsque vous remplissez votre manifeste d’application.  
  
 Dans les applications Windows Forms ne pas déployé à l’aide de ClickOnce, une application  *\<application >. exe.config* fichier est stocké dans le répertoire de l’application, tandis que le *user.config* fichier est stocké. de l’utilisateur **Documents and Settings** dossier. Dans une application ClickOnce,  *\<application >. exe.config* se trouve dans le répertoire de l’application dans le cache d’application ClickOnce, et *user.config* se trouve dans le répertoire de données ClickOnce pour cette application.  
  
 Quelle que soit la manière dont vous déployez votre application, paramètres de l’application garantissent un accès en lecture sécurisé à  *\<application >. exe.config*et l’accès en lecture/écriture sécurisé à *user.config*.  
  
 Dans une application ClickOnce, la taille des fichiers de configuration utilisé par les paramètres de l’application est limitée par la taille du cache ClickOnce. Pour plus d’informations, consultez [vue d’ensemble du cache ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Mises à niveau de version  
 Tout comme chaque version d’une application ClickOnce est isolée de toutes les autres versions, les paramètres d’application pour une application ClickOnce sont isolés à partir des paramètres pour les autres versions ainsi. Quand votre utilisateur mis à niveau vers une version ultérieure de votre application, paramètres de l’application compare les paramètres de (la plus élevée numérotées) version la plus récente sur les paramètres fournis avec la version mise à jour et fusionnent les paramètres dans un nouvel ensemble de fichiers de paramètres.  
  
 Le tableau suivant décrit comment les paramètres de l’application déterminent les paramètres à copier.  
  
|Type de modification|Action de mise à niveau|  
|--------------------|--------------------|  
|Paramètre ajouté à  *\<application >. exe.config*|Le nouveau paramètre est fusionné dans la version actuelle  *\<application >. exe.config*|  
|Paramètre retiré  *\<application >. exe.config*|L’ancien paramètre est supprimé de la version actuelle  *\<application >. exe.config*|  
|Par défaut du paramètre changé ; paramètre locale est toujours définie sur la valeur par défaut d’origine dans *user.config*|Le paramètre est fusionné dans la version actuelle *user.config* avec la nouvelle valeur par défaut en tant que la valeur|  
|Par défaut du paramètre changé ; défini sur non définis par défaut dans *user.config*|Le paramètre est fusionné dans la version actuelle *user.config* avec la valeur par défaut non conservée|  
  
Si vous avez créé vos propres paramètres de l’application classe wrapper et que vous souhaitez personnaliser la logique de mise à jour, vous pouvez remplacer le \<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A > méthode.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce et paramètres d’itinérance  
 ClickOnce ne fonctionne pas avec les paramètres d’itinérance, qui permet à votre fichier de paramètres pour vous suivent sur plusieurs ordinateurs sur un réseau. Si vous avez besoin de paramètres d’itinérance, vous devrez soit implémenter un fournisseur de paramètres d’application qui stocke les paramètres sur le réseau ou développer vos propres classes de paramètres personnalisés pour stocker les paramètres sur un ordinateur distant. Pour plus d’informations dans les fournisseurs de paramètres, consultez [architecture des paramètres d’Application](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Vue d’ensemble des paramètres d’application](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [Vue d’ensemble du cache ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Accéder aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)