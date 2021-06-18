---
title: Activation des mises à jour de l’administrateur pour Visual Studio avec le point de terminaison Microsoft Configuration Manager
titleSuffix: ''
description: En savoir plus sur le déploiement des mises à jour de l’administrateur vers Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: affb5a0c78c1ad1e230c571485385d9f55fc2bec
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307451"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Activation des mises à jour de l’administrateur pour Visual Studio avec le point de terminaison Microsoft Configuration Manager

Le Configuration Manager de point de terminaison Microsoft (SCCM) peut gérer les mises à jour de l’Administrateur Visual Studio 2017 et Visual Studio 2019 à l’aide du flux de travail de gestion des mises à jour logicielles.

> [!NOTE]
> Pour la simplicité de la documentation, le contenu ci-dessous fait référence aux produits Visual Studio 2017, Visual Studio 2019 et Visual Studio 2022, collectivement sous le titre « Visual Studio ».

Lorsque Microsoft publie une nouvelle mise à jour de Visual Studio sur le réseau de distribution de contenu (CDN), Microsoft publie simultanément un package de mise à jour administrateur correspondant sur les serveurs Microsoft Update. Cela permet ensuite à un administrateur de distribuer la mise à jour de Visual Studio via le [catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) ou [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS). Configuration Manager peut être configuré pour synchroniser les mises à jour de l’Administrateur Visual Studio à partir du catalogue WSUS sur le serveur de site, puis il peut télécharger la mise à jour et la distribuer aux ordinateurs clients Visual Studio au sein de l’organisation. Pour plus d’informations sur les correctifs présents dans chaque version de Visual Studio, consultez les [notes de publication](/visualstudio/releases/2019/release-notes).

Pour distribuer les mises à jour de l’Administrateur Visual Studio par le biais de Configuration Manager, vous devez suivre ces deux étapes de préparation initiales :
1. Activez Configuration Manager pour recevoir les notifications de mise à jour de l’Administrateur Visual Studio. 
2. Activez (ou désactivez) les ordinateurs clients pour recevoir les mises à jour de l’Administrateur Visual Studio à partir de Configuration Manager.

Après avoir effectué ces étapes, vous pouvez utiliser les fonctionnalités de gestion des mises à jour logicielles de Configuration Manager pour déployer les mises à jour de l’Administrateur Visual Studio. Les différents types et caractéristiques des mises à jour de l’Administrateur Visual Studio sont décrits dans [application des mises à jour](../install/applying-administrator-updates.md)de l’administrateur, qui fournit des conseils sur la façon et le moment de la distribution dans l’ensemble de votre organisation. Pour plus d’informations sur les fonctionnalités et options de Configuration Manager, consultez [déployer des mises à jour logicielles dans des Configuration Manager de point de terminaison Microsoft](/mem/configmgr/sum/deploy-use/deploy-software-updates).

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Autoriser Configuration Manager à recevoir des notifications de mise à jour de l’Administrateur Visual Studio

Pour permettre à Configuration Manager de gérer les mises à jour de l’Administrateur Visual Studio, vous avez besoin des éléments suivants :

* Une version sous licence actuelle de Windows Server exécutant Microsoft Endpoint Configuration Manager (Current Branch) et Windows Server Update Services (WSUS). Vous ne pouvez pas utiliser WSUS pour déployer ces mises à jour ; elle doit être utilisée conjointement avec Configuration Manager.

* Le serveur WSUS de niveau supérieur de la hiérarchie et le serveur de site Configuration Manager de niveau supérieur doivent avoir accès aux URL et aux ports Visual Studio répertoriés ici : [installer et utiliser Visual Studio et les services Azure derrière un pare-feu ou un serveur proxy](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md).  

* Le point de terminaison Microsoft Configuration Manager doit être configuré pour recevoir des notifications lorsque les packages de mise à jour de l’Administrateur Visual Studio sont disponibles.  Pour ce faire, suivez les étapes ci-dessous et pour plus d’informations, consultez [Présentation des mises à jour logicielles dans le Configuration Manager de point de terminaison Microsoft](/mem/configmgr/sum/understand/software-updates-introduction).

  1. Dans la console Configuration Manager, sélectionnez **administration** (en bas à gauche), puis sélectionnez **configuration du site** (à gauche), puis **sites**, puis sélectionnez votre serveur de site.

  2. Dans le ruban de l’onglet d' **hébergement** en haut, dans le bouton groupe de **paramètres** , sélectionnez **configurer les composants de site**, puis sélectionnez point de **mise à jour logicielle**.

  3. Dans la boîte de dialogue **Propriétés du composant du point de mise à jour logicielle** :

        * Sous l’onglet **produits** , sous la hiérarchie **outils de développement, runtimes et redistribuables** , choisissez les versions de Visual Studio que vous souhaitez synchroniser.

        * Sous l’onglet **classifications** , assurez-vous que « mises à jour de sécurité », « packs de fonctionnalités » et « mises à jour » sont sélectionnés.

  4. Ensuite, synchronisez les mises à jour logicielles avec le serveur WSUS en choisissant **bibliothèque de logiciels** (en bas à gauche), puis, dans le ruban de l’onglet d' **hébergement** en haut, sélectionnez le bouton **synchroniser les mises à jour logicielles** . La synchronisation des mises à jour logicielles rend les mises à jour de l’Administrateur Visual Studio disponibles visibles dans et pouvant être déployées à partir de la console Configuration Manager.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Activer (ou désactiver) les ordinateurs clients qui peuvent recevoir des mises à jour de l’Administrateur Visual Studio à partir de Configuration Manager

Pour permettre à un ordinateur client d’accepter les mises à jour de l’Administrateur Visual Studio, vous devez vous assurer que l’utilitaire de détection du client Visual Studio est correctement installé et que vous devez définir une clé de Registre pour permettre au client de recevoir les mises à jour de l’administrateur.  

### <a name="visual-studio-client-detector-utility"></a>Utilitaire de détection du client Visual Studio

L' [utilitaire de détection du client Visual Studio](https://support.microsoft.com/help/5001148) doit être installé sur les ordinateurs clients afin que les mises à jour de l’administrateur soient correctement reconnues et reçues. Cet utilitaire a été inclus avec toutes les mises à jour de produit Visual Studio 2017 et Visual Studio 2019 publiées le 12 mai, ou après le 2020 12 mai, il est inclus comme condition préalable à l’ensemble des mises à jour de l’Administrateur Visual Studio. il est également disponible sur le [catalogue Microsoft Update](https://catalog.update.microsoft.com) pour une installation indépendante.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>Encodage de l’intention de l’administrateur sur les ordinateurs clients

Les ordinateurs clients doivent être activés pour recevoir les mises à jour de l’administrateur. Cette étape est nécessaire pour s’assurer que les mises à jour ne sont pas involontairement ou accidentellement transmises à des ordinateurs clients qui ne sont pas suspectés.

La clé **AdministratorUpdatesEnabled**   est conçue pour permettre à l’administrateur d’encoder l’intention de l’administrateur. Cette clé peut se trouver dans n’importe quel emplacement Visual Studio standard, comme décrit dans la documentation [définir les valeurs par défaut pour les déploiements d’entreprise de Visual Studio](/visualstudio/install/set-defaults-for-enterprise-deployments) . L’accès administrateur sur l’ordinateur client est requis pour créer et définir la valeur de cette clé.

* Pour configurer l’ordinateur client pour qu’il accepte les mises à jour de l’administrateur, affectez la valeur 1 à la clé **AdministratorUpdatesEnabled**   REG_DWORD. ****
* Si la  ****   clé de REG_DWORD AdministratorUpdatesEnabled est **manquante ou est définie sur 0**, l’application des mises à jour de l’administrateur sera bloquée sur l’ordinateur client.

## <a name="feedback-and-support"></a>Commentaires et support

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Vous pouvez utiliser les méthodes suivantes pour fournir des commentaires sur les mises à jour de l’Administrateur Visual Studio ou pour signaler des problèmes qui affectent les mises à jour :

* Reportez-vous à la [résolution des problèmes d’installation et de mise à niveau de Visual Studio](../install/troubleshooting-installation-issues.md) .
* Posez des questions à la Communauté lors du [programme d’installation de Visual Studio Q&Forum](/answers/topics/vs-setup.html).
* Accédez à la [page de support de Visual Studio](https://visualstudio.microsoft.com/vs/support/)et vérifiez si votre problème est mentionné dans le Forum aux questions.  Vous pouvez également sélectionner le bouton de [lien support](https://visualstudio.microsoft.com/vs/support/#talktous) pour l’aide de conversation.
* [Fournissez des commentaires sur les fonctionnalités ou signalez un problème](https://aka.ms/vs/wsus/feedback) à l’équipe Visual Studio en ce qui concerne l’activation des mises à jour de l’administrateur.
* Contactez le responsable technique de votre organisation pour Microsoft.

## <a name="see-also"></a>Voir aussi

* [Application des mises à jour de l’administrateur](../install/applying-administrator-updates.md)
* [Guide de l’administrateur Visual Studio](../install/visual-studio-administrator-guide.md)
* [Cycle de vie et maintenance des produits Visual Studio](/visualstudio/productinfo/vs-servicing-vs)
* [Notes de publication de Visual Studio 2019](/visualstudio/releases/2019/release-notes)
* [Notes de publication de Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Installer Visual Studio](../install/install-visual-studio.md)
* [FAQ sur le catalogue Microsoft Update](https://www.catalog.update.microsoft.com/faq.aspx)
* [Documentation de Microsoft Endpoint Configuration Manager (SCCM)](/mem/configmgr)
* [Importer des mises à jour à partir de Microsoft Catalog dans Configuration Manager](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Documentation Windows Server Update Services (WSUS)](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
