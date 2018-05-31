---
title: Installer et configurer des outils de génération en utilisant iOS | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: d6acdd6433c090472e88d9973f6b28d80b8c2f8d
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454568"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Installer et configurer des outils de génération en utilisant iOS

Vous pouvez utiliser Visual C++ pour le développement mobile multiplateforme pour modifier et déboguer du code iOS et ensuite le déployer dans le simulateur iOS ou sur un appareil iOS, mais en raison de restrictions de licences, le code doit être généré et exécuté à distance sur un Mac. Pour générer et exécuter des applications iOS à l’aide de Visual Studio, vous devez installer et configurer l’agent distant, [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988), sur votre Mac. L’agent distant gère les demandes de génération de Visual Studio et exécute l’application sur un appareil iOS connecté au Mac ou dans le simulateur iOS sur le Mac.

> [!NOTE]
> Pour plus d’informations sur l’utilisation des services Mac hébergés dans le cloud plutôt que sur un Mac, consultez [Configurer Visual Studio pour vous connecter à votre Mac hébergé dans le cloud](https://docs.microsoft.com/en-us/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017#configure-visual-studio-to-connect-to-your-cloud-hosted-mac). Les instructions portent sur la génération à l’aide de Visual Studio Tools pour Apache Cordova. Pour utiliser les instructions de génération à l’aide de C++, remplacez vcremote par remotebuild.

Une fois que vous avez installé les outils permettant de générer avec iOS, reportez-vous à cette rubrique pour savoir comment configurer et mettre rapidement à jour l’agent distant en vue de développer du code pour iOS dans Visual Studio et sur votre Mac.

## <a name="prerequisites"></a>Prérequis

Pour installer et utiliser l’agent distant en vue de développer du code pour iOS, vous devez tout d’abord disposer des éléments suivants :

- Un ordinateur Mac exécutant OS X Mavericks version 10.9 ou ultérieure

- Un [ID Apple](https://appleid.apple.com/)

- Un compte de [programme développeur iOS](https://developer.apple.com/programs/ios/) actif auprès d’Apple

- [Xcode](https://developer.apple.com/xcode/downloads/) version 6 ou ultérieure.

   Xcode peut être téléchargé depuis l’App Store.

- Outils en ligne de commande Xcode

   Pour installer les outils en ligne de commande Xcode, ouvrez l’application Terminal sur votre Mac et entrez la commande suivante :

   `xcode-select --install`

- Une identité de signature iOS configurée dans Xcode

   Pour plus d’informations sur l’obtention d’une identité de signature iOS, consultez le document relatif à la [gestion des identités et des certificats de signature](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) dans la bibliothèque du développeur iOS. Pour afficher ou définir votre identité de signature dans Xcode, ouvrez le menu **Xcode** et choisissez **Preferences**. Sélectionnez **Accounts** , choisissez votre ID Apple, puis cliquez sur le bouton **View Details** .

- Si vous utilisez un appareil iOS pour le développement, un profil de mise en service (« Provisioning Profile ») configuré dans Xcode pour votre appareil

   Pour plus d’informations sur la création de profils de mise en service, consultez le document relatif à la [création de profils de mise en service via le centre des membres](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) dans la bibliothèque du développeur iOS.

- [Node.js](https://nodejs.org/)

   Installez la dernière version Long Term Support (LTS) 8.x du fichier Node.js sur votre Mac. Notez que les autres versions les plus récentes peuvent ne pas prendre en charge certains modules utilisés dans vcremote et entraîner l’échec de l’installation vcremote.

- Une version mise à jour de npm

   La version de npm fournie avec Node.js n’est peut-être pas suffisamment récente pour installer vcremote. Pour mettre à jour npm, ouvrez l’application Terminal sur votre Mac et entrez la commande suivante :

   `sudo npm install -g npm@latest`

##  <a name="Install"></a> Installer l’agent distant pour iOS

Quand vous installez Visual C++ pour le développement mobile multiplateforme, Visual Studio peut communiquer avec [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988). Cet agent distant s’exécutant sur votre Mac permet de transférer des fichiers, de générer et exécuter votre application iOS et d’envoyer des commandes de débogage.

Avant d’installer l’agent distant, assurez-vous que vous disposez bien des [Composants requis](#Prerequisites) et que vous avez installé [Visual C++ pour le développement mobile multiplateforme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools).

###  <a name="DownloadInstall"></a> Pour télécharger et installer l’agent distant

- Dans l’application Terminal de votre Mac, entrez :

   `sudo npm install -g --unsafe-perm vcremote`

   Le commutateur d’installation globale (**-g**) est recommandé, mais pas obligatoire.

   Pendant l’installation, vcremote est installé et le mode développeur est activé sur votre Mac. [Homebrew](https://brew.sh/) et deux packages npm, vcremote-lib et vcremote-utils, sont aussi installés. Une fois l’installation terminée, ne tenez pas compte des avertissements relatifs aux dépendances facultatives ignorées.

   > [!NOTE]
   > Pour installer Homebrew, vous devez disposer d’un accès sudo (administrateur). Si vous avez besoin d’installer vcremote sans sudo, vous pouvez installer Homebrew manuellement à un emplacement usr/local et ajouter son dossier bin à votre chemin. Pour plus d’informations, consultez la [documentation Homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Pour activer manuellement le mode développeur, entrez cette commande dans l’application Terminal : `DevToolsSecurity -enable`

Si vous avez mis à jour Visual Studio vers une nouvelle version, vous devez aussi mettre à jour l’agent distant vers la version actuelle. Pour mettre à jour l’agent distant, répétez la procédure de téléchargement et d’installation de l’agent à distance.

##  <a name="Start"></a> Démarrer l’agent distant

L’agent distant doit s’exécuter pour permettre à Visual Studio de générer et exécuter votre code iOS. Pour pouvoir communiquer, Visual Studio doit être couplé à l’agent distant. Par défaut, l’agent distant s’exécute en mode de connexion sécurisée, ce qui nécessite qu’un code confidentiel soit couplé à Visual Studio.

###  <a name="RemoteAgentStartServer"></a> Pour démarrer l’agent distant

- Dans l’application Terminal de votre Mac, entrez :

   `vcremote`

   L’agent distant démarre avec un répertoire de build par défaut ~/vcremote. Des options de configuration supplémentaires sont décrites dans la section [Configure the remote agent on the Mac](#ConfigureMac).

La première fois que vous démarrez l’agent et à chaque fois que vous créez un certificat client, les informations nécessaires à la configuration de l’agent dans Visual Studio vous sont fournies, notamment le nom d’hôte, le port et le code confidentiel.

![Utiliser vcremote pour générer un code PIN sécurisé](../cross-platform/media/cppmdd_vcremote_generateclientcert.png "CPPMDD_vcremote_generateClientCert")

Si vous envisagez de configurer l’agent distant dans Visual Studio en utilisant le nom d’hôte, envoyez une requête ping au Mac à partir de Windows en utilisant le nom d’hôte pour vérifier qu’il est accessible. Dans le cas contraire, vous serez peut-être amené à utiliser l’adresse IP à la place.

Le code confidentiel généré est à usage unique et n’est valable que pour une durée limitée. Si vous ne couplez pas Visual Studio à l’agent distant avant l’expiration du délai, vous devrez générer un nouveau code confidentiel. Pour plus d'informations, consultez [Generate a new security PIN](#GeneratePIN).

Vous pouvez utiliser l’agent distant en mode non sécurisé. En mode non sécurisé, l’agent distant peut être couplé à Visual Studio sans code confidentiel.

#### <a name="to-disable-secured-connection-mode"></a>Pour désactiver le mode de connexion sécurisée

- Pour désactiver le mode de connexion sécurisée dans vcremote, entrez cette commande dans l’application Terminal de votre Mac :

   `vcremote --secure false`

#### <a name="to-enable-secured-connection-mode"></a>Pour activer le mode de connexion sécurisée

- Pour activer le mode de connexion sécurisée, entrez cette commande :

   `vcremote --secure true`

Une fois l’agent distant démarré, vous pouvez l’utiliser dans Visual Studio jusqu’à ce que vous l’arrêtiez.

#### <a name="to-stop-the-remote-agent"></a>Pour arrêter l’agent distant

- Dans la fenêtre Terminal où s’exécute vcremote, entrez `Control+C`

##  <a name="ConfigureVS"></a> Configurer l’agent distant dans Visual Studio

Pour vous connecter à l’agent distant dans Visual Studio, vous devez spécifier la configuration à distance dans les options Visual Studio.

#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Pour configurer l’agent distant dans Visual Studio

1. Si l’agent n’est pas déjà en cours d’exécution sur votre Mac, suivez les étapes décrites dans [Démarrer l’agent distant](#Start). Votre Mac doit exécuter vcremote pour permettre à Visual Studio de se coupler, de se connecter et de générer votre projet.

1. Sur votre Mac, obtenez le nom d’hôte ou l’adresse IP de votre Mac.

   Vous pouvez obtenir l’adresse IP en utilisant la commande **ifconfig** dans une fenêtre Terminal. Utilisez l’adresse inet répertoriée sous l’interface réseau active.

1. Dans la barre de menus Visual Studio, choisissez **Outils**, **Options**.

1. Dans la boîte de dialogue **Options** , développez **Multiplateforme**, **C++**, **iOS**.

1. Dans les champs **Nom d’hôte** et **Port** , entrez les valeurs spécifiées par l’agent distant au moment où vous l’avez démarré. Le nom d’hôte peut être le nom DNS ou l’adresse IP de votre Mac. Le numéro de port par défaut est 3030.

   > [!NOTE]
   > Si vous ne pouvez pas envoyer une requête ping au Mac en utilisant le nom d’hôte, vous devrez peut-être utiliser l’adresse IP.

1. Si vous utilisez l’agent distant en mode de connexion sécurisée par défaut, cochez la case **Sécuriser** , puis entrez la valeur de code confidentiel spécifiée par l’agent distant dans le champ **Code confidentiel** . Si vous utilisez l’agent distant en mode de connexion non sécurisée, décochez la case **Sécuriser** et laisser le champ **Code confidentiel** vide.

1. Choisissez **Coupler** pour activer le jumelage.

   ![Configurer la connexion vcremote pour les builds iOS](../cross-platform/media/cppmdd_options_ios.PNG "CPPMDD_Options_iOS")

   Le couplage persiste tant que vous ne changez pas de nom d’hôte ou de port. Si vous changez de nom d’hôte ou de port dans la boîte de dialogue **Options** , pour annuler la modification, choisissez le bouton **Rétablir** pour revenir au couplage précédent.

   Si le couplage n’aboutit pas, vérifiez que l’agent distant s’exécute en suivant les étapes décrites dans [Start the remote agent](#Start). Si trop de temps s’est écoulé après la génération du code confidentiel de l’agent, suivez les étapes décrites dans [Generate a new security PIN](#GeneratePIN) sur le Mac, puis réessayez. Si vous utilisez le nom d’hôte de votre Mac, essayez plutôt d’utiliser l’adresse IP qui figure dans le champ **Nom d’hôte** .

1. Mettez à jour le nom de dossier dans le champ **Racine distante** pour spécifier le dossier utilisé par l’agent distant dans le répertoire de base (~) du Mac. Par défaut, l’agent distant utilise /Users/`username`/vcremote comme racine distante.

1. Choisissez **OK** pour enregistrer les paramètres de connexion de couplage à distance.

Visual Studio utilise les mêmes informations pour se connecter à l’agent distant sur votre Mac chaque fois que vous l’utilisez. Vous n’avez pas besoin de coupler à nouveau Visual Studio à l’agent distant, sauf si vous générez un nouveau certificat de sécurité sur votre Mac ou que son nom d’hôte ou son adresse IP est modifié.

##  <a name="GeneratePIN"></a> Generate a new security PIN

Quand vous démarrez l’agent distant pour la première fois, le code confidentiel généré est valide pendant une période limitée (par défaut, 10 minutes). Si vous ne couplez pas Visual Studio à l’agent distant avant l’expiration de ce délai, vous devez générer un nouveau code confidentiel.

#### <a name="to-generate-a-new-pin"></a>Pour générer un nouveau code confidentiel

1. Arrêtez l’agent ou ouvrez une deuxième fenêtre d’application Terminal sur votre Mac et utilisez-la pour entrer la commande.

1. Entrez cette commande dans l’application Terminal :

   `vcremote generateClientCert`

   L’agent distant génère un nouveau code confidentiel temporaire. Pour coupler Visual Studio à l’aide du nouveau code confidentiel, répétez les étapes décrites dans [Configurer l’agent distant dans Visual Studio](#ConfigureVS).

##  <a name="GenerateCert"></a> Générer un nouveau certificat de serveur

Pour des raisons de sécurité, les certificats de serveur qui couplent Visual Studio à l’agent distant sont liés à l’adresse IP ou au nom d’hôte de votre Mac. Si ces valeurs changent, vous devez générer un nouveau certificat de serveur et reconfigurer Visual Studio avec les nouvelles valeurs.

#### <a name="to-generate-a-new-server-certificate"></a>Pour générer un nouveau certificat de serveur

1. Arrêtez l’agent vcremote.

1. Entrez cette commande dans l’application Terminal :

   `vcremote resetServerCert`

1. Quand vous êtes invité à confirmer l’opération, entrez `Y`

1. Entrez cette commande dans l’application Terminal :

   `vcremote generateClientCert`

   Un nouveau code confidentiel temporaire est alors généré.

1. Pour coupler Visual Studio à l’aide du nouveau code confidentiel, répétez les étapes décrites dans [Configurer l’agent distant dans Visual Studio](#ConfigureVS).

##  <a name="ConfigureMac"></a> Configure the remote agent on the Mac

Vous pouvez configurer l’agent distant en utilisant diverses options de ligne de commande. Par exemple, vous pouvez spécifier le port à écouter pour les demandes de génération et spécifier le nombre maximal de builds à conserver sur le système de fichiers. Par défaut, cette limite est de 10 builds. Au moment de l’arrêt, l’agent supprime les builds qui dépassent ce nombre maximal.

#### <a name="to-configure-the-remote-agent"></a>Pour configurer l’agent distant

- Pour afficher la liste complète des commandes de l’agent distant, dans l’application Terminal, entrez :

   `vcremote --help`

- Pour désactiver le mode sécurisé et activer les connexions HTTP simples, entrez :

   `vcremote --secure false`

   Quand vous utilisez cette option, décochez la case **Sécuriser** et laissez le champ **Code PIN** vide pendant la configuration de l’agent dans Visual Studio.

- Pour spécifier l’emplacement des fichiers de l’agent distant, entrez :

   `vcremote --serverDir directory_path`

   où *chemin_répertoire* est l’emplacement sur votre Mac où seront placés les fichiers journaux, les builds et les certificats de serveur. Par défaut, cet emplacement est /Users/*nom_utilisateur*/vcremote. Les builds sont organisées par numéro de build à cet emplacement.

- Pour utiliser un processus en arrière-plan pour capturer `stdout` et `stderr` dans un fichier nommé serveur.log, entrez :

   `vcremote > server.log 2>&1 &`

   Le fichier serveur.log peut aider à la résolution des problèmes de génération.

- Pour exécuter l’agent en utilisant un fichier de configuration au lieu de paramètres de ligne de commande, entrez :

   `vcremote --config config_file_path`

   où *chemin_fichier_config* est le chemin d’accès à un fichier de configuration au format JSON. Les options de démarrage et leurs valeurs ne doivent pas inclure de tirets.

## <a name="see-also"></a>Voir aussi

- [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
