---
title: ClickOnce et paramètres d’application | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: c8e1ffe6d6f32cfad137d5890715a5a0032a29d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696688"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce et paramètres d'application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les paramètres d’application pour Windows Forms facilitent la création, le stockage et la gestion des applications personnalisées et des préférences utilisateur sur le client. Le document suivant décrit comment les fichiers de paramètres d’application fonctionnent dans une application ClickOnce et comment ClickOnce migre les paramètres lorsque l’utilisateur effectue une mise à niveau vers la version suivante.  
  
 Les informations ci-dessous s’appliquent uniquement au fournisseur de paramètres d’application par défaut, la <xref:System.Configuration.LocalFileSettingsProvider> classe. Si vous fournissez un fournisseur personnalisé, ce fournisseur détermine son mode de stockage des données et la manière dont il met à niveau ses paramètres entre les versions. Pour plus d’informations sur les fournisseurs de paramètres d’application, consultez [architecture des paramètres d’application](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>Fichiers de paramètres d’application  
 Les paramètres d’application consomment deux fichiers : *application*.exe.config et user.config, où *app* est le nom de votre application Windows Forms. user.config est créé sur le client la première fois que votre application stocke les paramètres de portée utilisateur. le.exe.config de l' *application* , en revanche, existe avant le déploiement si vous définissez des valeurs par défaut pour les paramètres. Visual Studio inclut automatiquement ce fichier quand vous utilisez sa commande **publier** . Si vous créez votre application ClickOnce à l’aide de Mage.exe ou MageUI.exe, vous devez vous assurer que ce fichier est inclus dans les autres fichiers de votre application lorsque vous remplissez le manifeste de votre application.  
  
 Dans un Windows Forms applications non déployées à l’aide de ClickOnce, le fichier *de.exe.config d’application d'* une application est stocké dans le répertoire de l’application, tandis que le fichier user.config est stocké dans le dossier **Documents and Settings** de l’utilisateur. Dans une application ClickOnce, l' *application.exe.config réside* dans le répertoire de l’application au sein du cache d’application ClickOnce, et user.config vit dans le répertoire de données ClickOnce pour cette application.  
  
 Quelle que soit la façon dont vous déployez votre application, les paramètres de l’application garantissent un accès en lecture sécurisé *aux.exe.config d’application et* un accès en lecture/écriture sécurisé aux user.config.  
  
 Dans une application ClickOnce, la taille des fichiers de configuration utilisés par les paramètres d’application est restreinte par la taille du cache ClickOnce. Pour plus d’informations, consultez [vue d’ensemble du cache ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Mises à niveau de version  
 Tout comme chaque version d’une application ClickOnce est isolée de toutes les autres versions, les paramètres d’application pour une application ClickOnce sont également isolés des paramètres pour d’autres versions. Lorsque votre utilisateur se met à niveau vers une version ultérieure de votre application, les paramètres de l’application comparent les paramètres de la version la plus récente (avec les numéros les plus élevés) par rapport aux paramètres fournis avec la version mise à jour et fusionne les paramètres dans un nouvel ensemble de fichiers de paramètres.  
  
 Le tableau suivant décrit comment les paramètres de l’application déterminent les paramètres à copier.  
  
|Type de modification|Action de mise à niveau|  
|--------------------|--------------------|  
|Paramètre ajouté à l' *application*.exe.config|Le nouveau paramètre est fusionné dans l' *application* de la version actuelle.exe.config|  
|Paramètre supprimé de l' *application*.exe.config|L’ancien paramètre est supprimé de l' *application* de la version actuelle.exe.config|  
|Modification de la valeur par défaut du paramètre ; le paramètre local est toujours défini sur la valeur par défaut d’origine dans user.config|Le paramètre est fusionné dans le user.config de la version actuelle avec la nouvelle valeur par défaut.|  
|Modification de la valeur par défaut du paramètre ; paramètre défini sur non défini par défaut dans user.config|Le paramètre est fusionné dans le user.config de la version actuelle avec la valeur non définie par défaut.|  
  
 Si vous avez créé votre propre classe wrapper de paramètres d’application et que vous souhaitez personnaliser la logique de mise à jour, vous pouvez substituer la <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> méthode.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce et paramètres d’itinérance  
 ClickOnce ne fonctionne pas avec les paramètres d’itinérance, ce qui permet à votre fichier de paramètres de vous suivre sur les ordinateurs d’un réseau. Si vous avez besoin de paramètres d’itinérance, vous devez implémenter un fournisseur de paramètres d’application qui stocke les paramètres sur le réseau ou développer vos propres classes de paramètres personnalisées pour le stockage des paramètres sur un ordinateur distant. Pour plus d’informations sur les fournisseurs de paramètres, consultez [architecture des paramètres d’application](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Vue d’ensemble des paramètres d’application](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [Vue d’ensemble du cache ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Accès aux données locales et distantes dans les applications ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
