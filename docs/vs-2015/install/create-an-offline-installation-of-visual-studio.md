---
title: Créer une installation hors connexion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 197ae2a168f7f14f7d0ea3d9b82b5943c1af82f4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077938"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Créer une installation hors connexion de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour consulter la documentation à jour sur Visual Studio, voir [Créer une installation hors connexion de Visual Studio](/visualstudio/install/create-an-offline-installation-of-visual-studio) ou [Créer une installation réseau de Visual Studio](/visualstudio/install/create-a-network-installation-of-visual-studio).

Cette page explique comment installer Visual Studio 2015 sans connexion à Internet. Toutefois, pour pouvoir effectuer une installation « déconnectée », il faut d’abord créer une structure d’installation hors connexion avec un ordinateur connecté à Internet. Voici comment faire.

> [!IMPORTANT]
> Si votre ordinateur en mode hors connexion fonctionne sur Windows 7 SP1 ou Windows Server 2008 R2, consultez les instructions spéciales dans la section [Résoudre les problèmes des installations hors connexion](#BKMK_tshoot) de cette rubrique.  Suivez-les *avant* d’installer Visual Studio 2015.

## <a name="BKMK_Offline"></a> Créer une installation hors connexion

#### <a name="to-create-an-offline-installation-layout"></a>Créer une structure d’installation hors connexion

1. Choisissez l’édition de Visual Studio que vous souhaitez installer sur la page de téléchargement [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015).

2. Après avoir téléchargé le programme d’installation sur votre système de fichiers, exécutez « \<nom_exécutable> /layout ».

     Par exemple, exécutez : `vs_enterprise.exe /layout D:\VisualStudio2015`

     Le commutateur `/layout` permet de télécharger presque tous les packages d’installation, et pas seulement ceux qui s’appliquent à l’ordinateur de téléchargement. Vous obtenez ainsi les fichiers dont vous avez besoin pour exécuter ce programme d’installation n’importe où et pouvez installer des composants qui ne faisaient pas partie de l’installation initiale.

3. Une fois cette commande exécutée, une boîte de dialogue permet de changer le dossier dans lequel se trouvera la structure de l’installation hors connexion.   Ensuite, cliquez sur le bouton **Télécharger**.

     Une fois package téléchargé, un message indique **Installation réussie ! Tous les composants spécifiés sont bien installés**.

4. Recherchez le dossier que vous avez spécifié tout à l’heure (par exemple, D:\VisualStudio2015). Il contient tout ce dont vous devez copier sur un emplacement partagé ou un support d’installation.

    > [!CAUTION]
    > Actuellement, le kit SDK Android ne prend pas en charge les installations hors connexion. Si vous installez des éléments de l’installation du kit SDK Android sur un ordinateur qui n’est pas connecté à internet, l’installation peut échouer. Pour plus d’informations, voir la section « Résoudre les problèmes des installations hors connexion » de cette rubrique.

5. Exécutez l’installation à partir de l’emplacement du fichier ou du support d’installation.

## <a name="updating-an-offline-installation"></a>Mettre à jour une installation hors connexion
 Microsoft a publié plusieurs mises à jour de Visual Studio 2015. Pour mettre à jour une installation de Visual Studio, il suffit de télécharger l’édition souhaitée sur la page de téléchargement [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015). Ensuite, suivez les étapes décrites dans cette rubrique pour créer une nouvelle structure d’installation hors connexion et l’utiliser pour mettre à jour votre version de Visual Studio 2015.

## <a name="BKMK_tshoot"></a> Résoudre les problèmes des installations hors connexion
 Quand vous effectuez une installation hors connexion à partir de votre cache d’installation hors connexion, des messages d’avertissement peuvent s’afficher pour vous indiquer l’impossibilité d’installer certains composants et packages. Le tableau suivant présente les solutions possibles à ces scénarios.

| Composant ou package | Solution |
|-|-|
| Dotfuscator and Analytics Community Edition 5.19.1 (pour les éditions Community, Professional et Enterprise de Visual Studio, installée sur **Windows 7 SP1** et **Windows Server 2008 R2**) | Si votre ordinateur hors connexion fonctionne sur **Windows 7 SP1** ou **Windows Server 2008 R2**, vous devez suivre les étapes ci-dessous avant d’installer Visual Studio 2015 :<br /><br /> 1.  Configurez un serveur de fichiers ou un serveur web de façon à télécharger les fichiers CTL.<br /><br /> 2.    Redirigez l’URL de mise à jour automatique de Microsoft pour un environnement déconnecté.<br /><br /> Pour plus d’informations, voir la page [Configurer les racines de confiance et les certificats non autorisés](https://technet.microsoft.com/library/dn265983.aspx) du site Microsoft TechNet. |
| Installation du SDK Android (Niveau API) | Vous devez avoir une connexion Internet pour installer les packages du SDK Android (niveau API). Si vous êtes sur un réseau limité, vous devez autoriser l’accès aux URL suivantes quand vous installez Visual Studio :<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Pour plus d’informations sur la résolution des éventuels problèmes avec les paramètres de proxy, consultez le billet de blog [Visual Studio 2015 install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/). |
| Modèles d’élément d’extensibilité de Visual Studio<br /><br /> Extension GitHub pour Visual Studio<br /><br /> Outils PowerShell pour Visual Studio | Si vous n’avez pas de connexion Internet au moment d’installer Visual Studio 2015, vous pouvez utiliser un flux hors connexion spécial pour générer la structure de l’installation hors connexion. **Remarque :** ce flux spécial comporte les dernières mises à jour de Visual Studio 2015. <br /><br /> Pour créer le flux hors connexion spécial, exécutez la commande suivante : /layout *Drive:* \VisualStudio2015 /overridefeeduri *URL-to-feed-xml*.<br /><br /> Par exemple, pour un flux hors connexion spécial en langue anglaise de Visual Studio 2015 Enterprise, exécutez :<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Pour connaître la liste complète des URL permettant de créer un flux hors connexion spécial dans chaque langue, voir le tableau ci-dessous. |

 Utilisez les URL suivantes pour créer un flux hors connexion spécial propre à une langue, comme dans le tableau ci-dessus.

|       Langue        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| Chinois (simplifié)  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Chinois (traditionnel) | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Tchèque         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Allemand         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Anglais        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Espagnol        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Français         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italien        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japonais        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Coréen         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polonais         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugais       | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Russe        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turc        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Voir aussi

- [Installer Visual Studio](install-visual-studio-2015.md)