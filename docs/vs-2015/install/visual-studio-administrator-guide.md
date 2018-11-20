---
title: Guide de l’administrateur Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 25d6655969245adf1b2a28df2b3327561d149983
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722821"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio Administrator Guide
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour la documentation la plus récente pour Visual Studio 2017, consultez le [guide de l’administrateur Visual Studio 2017](/visualstudio/install/visual-studio-administrator-guide).

Vous pouvez déployer Visual Studio 2015 sur un réseau tant que chaque ordinateur cible remplit la [configuration minimale requise](http://www.microsoft.com/visualstudio/eng/products/2013-editions). Vous pouvez créer un partage réseau en exécutant le fichier d’installation avec le commutateur/Layout (comme décrit dans la [créer une Installation hors connexion de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) page) et en le copiant à partir de l’ordinateur local au partage réseau. Si vous utilisez un fichier ISO, vous pouvez monter l’image ISO et partagez-le ou copiez l’image ISO sur un partage réseau.  
  
 Notez que les installations effectuées à partir d’un partage réseau « se souviennent » de l’emplacement source dont elles sont issues. Cela signifie que la réparation d’un ordinateur client peut devoir retourner sur le partage réseau à partir duquel le client a été initialement installé. Choisissez soigneusement votre emplacement réseau : sa durée de vie doit être au moins aussi longue que celle des clients Visual Studio 2015 qui s’exécuteront dans votre organisation.  
  
## <a name="detection-and-servicing-keys"></a>Clés de détection et de maintenance  
 Vous pouvez utiliser les sous-clés de détection du Registre pour déterminer si un produit Visual Studio est déjà installé sur un ordinateur. Vous pouvez utiliser ces clés de détection dans un déploiement automatisé pour déterminer s’il est nécessaire de procéder à une installation.  Consultez [Detecting System Requirements](../extensibility/internals/detecting-system-requirements.md)[Detecting System Requirements].  
  
## <a name="avoiding-reboots"></a>Éviter les redémarrages  
 Vous pouvez réduire le nombre de redémarrages en vous assurant que vous disposez de la configuration requise avant de déployer Visual Studio. Pour le .NET Framework, vous devrez peut-être redémarrer les ordinateurs qui exécutent Windows 8 si vous déployez Visual Studio 2015 sur ces derniers sans d’abord installer le .NET Framework 4.6.  
  
 Pour l’émulation des appareils Windows et Android, vous devrez peut-être redémarrer les ordinateurs si vous n’avez pas déjà activé la fonctionnalité Hyper-V de Windows. Pour le développement web, vous devrez peut-être redémarrer les ordinateurs si vous n’avez pas déjà activé la fonctionnalité Serveur web de Windows. Pour le développement Office, vous devrez peut-être redémarrer les ordinateurs si vous n'avez pas déjà activé la fonctionnalité Windows Identity Foundation de Windows. redémarrer les ordinateurs si vous n'avez pas déjà activé la fonctionnalité Serveur web de Windows. Pour le développement Office, vous devrez peut-être redémarrer les ordinateurs si vous n’avez pas déjà activé la fonctionnalité Windows Identity Foundation de Windows. Pour plus d’informations sur l’automatisation de la détection et de l’installation des fonctionnalités Windows, consultez l’article [Installation d’un rôle serveur sur un serveur exécutant une installation minimale de Windows Server 2008 R2](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Codes de retour d’erreur  
 Le tableau suivant répertorie des codes d’erreur importants. Vous pouvez utiliser ces codes d’erreur dans votre automatisation pour décider si un redémarrage est nécessaire et si l’installation a abouti. Si vous recevez un code d’erreur, utilisez les étapes de dépannage sur le [installer Visual Studio](../install/install-visual-studio-2015.md) page.  
  
|État d’installation|Redémarrage non nécessaire|Redémarrage nécessaire|Description|  
|------------------|--------------------------|----------------------|-----------------|  
|Opération réussie|0x00000000 [0]|0x00000bc2 [3010]|Installation réussie.|  
|Bloc|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Si le seul bloc à signaler est « Redémarrage en attente, » la valeur retournée est la valeur requise pour Redémarrage incomplet (0x80048bc7).|  
|Annuler|0x00000642 [1602]|0x80048642 [-2147187134]|Quand la valeur Reboot est retournée, le code de retour est 1602.|  
|Incomplet-Redémarrage nécessaire|N/A|0x80048bc7 [-2147185721]|Un redémarrage est nécessaire pour que l’installation puisse continuer.|  
|Échec|0x00000643 [1603]|0x80048643 [-2147187133]|Quand la valeur Reboot est retournée, le code de retour est 1603.|  
  
## <a name="interactive-administrator-installer"></a>Programme d’installation interactif de l’administrateur  
 Si vous créez un programme d’installation interactif par-dessus l’installation de Visual Studio, vous pouvez afficher la progression à partir du programme d’installation de Visual Studio. Le programme d’installation de Visual Studio 2015 est basé sur la technologie de chaînage open source de Windows Installer XML (WiX), également appelée « burn ». La technologie burn prend en charge deux protocoles de communication : burn et netfx4. Pour obtenir des informations de référence rapides, consultez la description de l’attribut de protocole dans la documentation de l’élément ExePackage sur le site [wixtoolset.org](http://wixtoolset.org/). Un examen de l’implémentation open source de WiX de cet attribut de protocole peut être nécessaire pour l’intégration.  
  
## <a name="controlling-what-is-installed"></a>Contrôle des composants installés  
 Si vous voulez contrôler les composants que votre utilisateur final peut installer, il existe deux options : l’installation du fichier administrateur et les options de ligne de commande. Sélectionnez l’installation du fichier administrateur si votre objectif est de limiter les composants que votre utilisateur final peut choisir pendant l’exécution du programme d’installation de Visual Studio. Sélectionnez les paramètres de ligne de commande si vous voulez créer une configuration initiale, tout en autorisant l’utilisateur final à choisir une installation personnalisée de Visual Studio.  
  
 Pour plus d’informations sur l’expérience de fichier administrateur, consultez [How to: Create and Run an Unattended Installation of Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) et [How to: Automatically apply product keys when deploying Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Pour plus d’informations sur les contrôles de ligne de commande, consultez le [utiliser des paramètres de ligne de commande pour installer Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) page.  
  
## <a name="specifying-customer-feedback-settings"></a>Spécification de paramètres pour les commentaires client  
 Par défaut, l’installation de Visual Studio active les commentaires client. Vous pouvez configurer Visual Studio pour désactiver les commentaires client sur un ordinateur en affectant la valeur "0" à la clé de Registre suivante :  
  
 **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
 (Par exemple, modifiez-la en HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn="0")  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Guide pratique pour installer une version spécifique de Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)|Décrit comment installer des configurations spécifiques de la version actuelle de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Guide pratique pour créer et exécuter une installation sans assistance de Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Décrit comment installer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en mode sans assistance.|  
|[Guide pratique pour appliquer automatiquement des clés de produit lors du déploiement de Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Décrit comment appliquer des clés de produit lors du déploiement sur plusieurs ordinateurs.|  
|[Guide de l’administrateur Help Viewer](../ide/help-viewer-administrator-guide.md)|Fournit des informations sur la gestion des installations locales d’aide pour les environnements de réseau qui ont ou n’ont pas accès à internet.|  
|[Installer Visual Studio](../install/install-visual-studio-2015.md)|Fournit des instructions et des liens vers des rubriques qui décrivent comment installer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|