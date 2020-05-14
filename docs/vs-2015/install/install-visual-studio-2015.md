---
title: Installer Visual Studio 2015 │ Microsoft Docs
titleSuffix: ''
ms.date: 04/15/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bfc573c30281e5bc976ee25ea3a80a2f874ab25
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445075"
---
# <a name="install-visual-studio-2015"></a>Installer Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette page comprend des informations détaillées qui vous aideront à installer **Visual Studio 2015**, notre suite intégrée d’outils de productivité pour les développeurs. Nous avons également inclus des liens pour vous amener rapidement à des informations sur [les fonctionnalités,](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history) [les exigences du système,](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs)les [téléchargements,](https://visualstudio.microsoft.com/vs/older-downloads/)et plus encore.

## <a name="quick-links"></a>Liens rapides

Avant d’entrer dans les détails, voici une liste de nos liens les plus demandés.

|||
|------------------|----------------|
|![Télécharger Visual Studio](../install/media/downloads.png "Téléchargements") |**Téléchargements**: Pour installer Visual Studio 2015, vous pouvez télécharger un fichier exécutable à partir de la page [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (abonnement requis), ou utiliser le support d’installation à partir du produit en boîte. [En savoir plus sur la façon de télécharger les versions actuelles ou précédentes de Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![En savoir plus sur les fonctionnalités](../install/media/features.png "Fonctionnalités") |**Caractéristiques**: Pour en savoir plus sur les fonctionnalités de Visual Studio 2015, voir les notes de sortie pour [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Mise à jour 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Mise à jour 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs), et [Mise à jour 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Afficher les exigences du système](../install/media/system-requirements.png "Configuration requise") |**Exigences du système**: Pour consulter les exigences du système pour chaque édition de Visual Studio 2015, consultez la page [De ciblage et compatibilité de la plateforme Visual Studio 2015.](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)|
|![Localisez votre clé de produit](../install/media/product-keys.png "Clés de produit") |**Clés de produit**: Pour localiser votre clé de produit, consultez le thème Comment : Localiser le sujet [de clé de produit visual studio.](../install/how-to-locate-the-visual-studio-product-key.md)|
|![Renseignez-vous sur les licences](../install/media/licensing.png "Licence") |**Licences**: Pour en savoir plus sur les options de licence pour les particuliers ou les clients d’entreprise, consultez le [Visual Studio 2015 Licensing White Paper](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a>Défaut vs Configuration personnalisée
 Au moment d’installer Visual Studio 2015, vous pouvez inclure les composants que vous prévoyez d’utiliser au quotidien et exclure les autres. Cela signifie qu’une installation par défaut sera souvent plus petite et plus rapide à installer qu’une installation personnalisée. Cela signifie aussi que bon nombre de composants qui étaient installés par défaut dans les versions précédentes sont maintenant considérés comme des composants personnalisés que vous devez sélectionner explicitement dans cette version.

 ![Boîte de dialogue d'installation de Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Les composants personnalisés comprennent Visual CMD, Visual F, SQL Server Data Tools, cross-platform mobile tools and SDKs, et third-party SDKs and extensions. Vous pouvez installer les composants personnalisés ultérieurement si vous ne les sélectionnez pas pendant l’installation initiale.

> [!NOTE]
> Une installation personnalisée inclut automatiquement les composants qui figurent dans une installation par défaut.

 Voici la liste complète des composants personnalisés :

|Ensembles de fonctionnalités|Components|
|------------------|----------------|
|**Mises à jour**|Visual Studio 2015 Update 3|
|**Programmation Langues**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Développement Windows et web**|Outils de publication de ClickOnce<br />LightSwitch<br />Outils de développement Microsoft Office<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />Outils PowerShell pour Studio Visuel (3ème Partie)<br />Kit de développement Silverlight<br />Outils de développement d’applications Windows universelles<br />Kits de développement logiciel (SDK) et outils Windows 10<br />Outils Windows 8.1 et Windows Phone 8.0/8.1<br />Kits de développement logiciel (SDK) et outils Windows 8.1|
|**Développement multiplateforme pour appareils mobiles**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Développement mobile Visual C++ pour iOS / Android<br />Clang avec Microsoft CodeGen|
|**Outils communs et kits de développement logiciel**|Kit de développement autochtone Android (3e partie)<br /> Android SDK [3ème Partie]<br />Android SDK Setup API (3ème partie)<br />Apache Ant (3ème Partie)<br /> Kit de développement Java SE (3e partie)<br /> Joyent Node.js (3e partie)|
|**Outils courants**|Git pour Windows (3ème Partie)<br />Extension GitHub pour Visual Studio (3e partie)<br /> Outils d'extensibilité de Visual Studio|

## <a name="install-visual-studio"></a><a name="installing"></a>Installer Visual Studio
 Vous pouvez installer Visual Studio en utilisant des supports d’installation (DVD), en utilisant votre service d’abonnement Visual Studio à partir du site [Web My.VisualStudio.com,](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) en téléchargeant un installateur web à partir du site [Visual Studio Downloads,](https://visualstudio.microsoft.com/vs/older-downloads/) ou en créant une mise en page d’installation hors ligne (voir la [page Créer une installation hors ligne de studio visuel](../install/create-an-offline-installation-of-visual-studio.md) pour plus de détails).

> [!IMPORTANT]
> Vous avez besoin d’informations d’identification d’administrateur pour installer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Toutefois, elles ne sont pas requises pour utiliser [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] après son installation.

 Les privilèges suivants de votre compte d'administrateur local doivent autoriser l'installation de tous les composants de Visual Studio.

|Nom d'affichage de l'objet de stratégie locale|Droit d'utilisateur|
|--------------------------------------|----------------|
|Sauvegarder les fichiers et les répertoires|SeBackupPrivilege|
|Déboguer les programmes|SeDebugPrivilege|
|Gérer le journal d'audit et de sécurité|SeSecurityPrivilege|

 Pour plus d’informations sur cette exigence de compte d’administrateur local, consultez l’article suivant de la Base de connaissances : [Échec de l’installation de SQL Server si le compte d’installation ne possède pas certains droits d’utilisateur](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a>Utiliser les supports d’installation
 Pour installer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], dans le répertoire racine du support d'installation de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , exécutez le fichier d'installation de l'édition souhaitée :

|Édition|Fichier d'installation|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Communauté Visual Studio|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a>Télécharger à partir du site Web du produit
 Visitez la page [Visual Studio Downloads](https://visualstudio.microsoft.com/vs/older-downloads/) et sélectionnez l’édition de Visual Studio que vous voulez.

### <a name="download-from-your-subscription-service"></a>Télécharger à partir de votre service d’abonnement
 Visitez la page [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) et sélectionnez l’édition de Visual Studio que vous voulez.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a>Créer une disposition d’installation hors ligne
 Si vous n’avez pas le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] support d’installation, ou si vous n’avez pas d’abonnement Visual Studio, ou si vous ne voulez pas installer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en utilisant l’installateur Web, vous pouvez effectuer une installation « déconnectée » en créant ce qu’on appelle une mise en page d’installation hors ligne. Pour plus d’informations, consultez la page [Créer une installation hors ligne de Studio visuel.](../install/create-an-offline-installation-of-visual-studio.md)

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a>Déployer Visual Studio dans une entreprise
 Pour plus d’informations sur la façon de se déployer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sur un réseau, consultez le Visual Studio Administrator [Guide](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a>Installer Visual Studio dans un environnement virtualisé
 **Problèmes vidéo avec Hyper-V**

 Si vous exécutez Windows Server 2008 R2 avec Hyper-V activé et une carte graphique accélérée, il se peut que vous rencontriez des ralentissements du système.

 Pour plus d’informations, voir [les performances vidéo peuvent diminuer quand un serveur Windows 2008 ou Windows Server 2008 R2 ordinateur a le rôle Hyper-V activé et un adaptateur d’affichage accéléré installé](https://support.microsoft.com/kb/961661).

 **Émulation d’appareils avec Hyper-V**

 Quand vous installez Visual Studio 2015 sur du vrai matériel, sans virtualisation, vous pouvez choisir les fonctionnalités qui permettent d'émuler les appareils Windows et Android avec Hyper-V. En revanche, quand vous effectuez l'installation dans Hyper-V, vous ne pouvez pas émuler les appareils Windows ou Android. Ceci est dû au fait que les émulateurs sont eux-mêmes des machines virtuelles et que vous ne pouvez pas héberger actuellement une machine virtuelle à l'intérieur d'une autre machine virtuelle. Une solution de contournement consiste à faire l'acquisition d'appareils Windows ou Android sur lesquels vous pouvez directement déployer et déboguer votre application.

## <a name="install-optional-components"></a><a name="optionalComponents"></a>Installer des composants optionnels
 Si vous souhaitez installer des composants que vous n’avez peut-être pas sélectionnés lors de votre installation d’origine, utilisez la procédure suivante.

#### <a name="to-install-optional-components"></a>Installer des composants optionnels

1. Dans **Panneau de configuration**, dans la page **Programmes et fonctionnalités** , sélectionnez l'édition du produit à laquelle vous souhaitez ajouter un ou plusieurs composants, puis cliquez sur **Modifier**.

2. Dans l'Assistant Installation, sélectionnez **Modifier**, puis sélectionnez les composants que vous souhaitez installer.

3. Choisissez **Suivant**, puis suivez les instructions restantes.

## <a name="install-offline-help-content"></a><a name="helpContent"></a>Installer du contenu d’aide hors ligne
 Après avoir installé [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez télécharger le contenu d'aide supplémentaire afin qu'il soit disponible hors connexion.

#### <a name="to-install-or-uninstall-help-content"></a>Pour installer ou désinstaller le contenu de l'aide

1. Dans la barre de menus [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , choisissez **Aide**, **Ajouter et supprimer le contenu d'aide**.

2. Sous l'onglet **Gérer le contenu** de la **Visionneuse d'aide Microsoft**, sélectionnez la source d'installation pour votre contenu d'aide.

3. Si vous recherchez une collection d’aide spécifique, entrez le nom ou le mot clé dans la zone de texte **Rechercher**, puis appuyez sur **Entrée**.

4. À côté du nom de la collection d'aide souhaitée, choisissez le lien **Ajouter** ou **Supprimer** .

5. Cliquez sur le bouton **Mettre à jour**.

   Pour plus d’informations sur la façon d’installer ou de déployer l’aide hors ligne, consultez le [Guide d’administrateur du téléspectateur d’aide](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a>Vérifiez les communiqués de service et les mises à jour des produits
 Comme les extensions ne sont pas toutes compatibles, Visual Studio ne met pas automatiquement à niveau les extensions quand vous effectuez une mise à niveau de versions antérieures. Vous devez réinstaller les extensions du [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou de l’éditeur de logiciels.

#### <a name="to-automatically-check-for-service-releases"></a>Pour rechercher automatiquement les publications du service

1. Sur la barre de menu, choisissez **Des outils,** **options**.

2. Dans la boîte de dialogue **Options** , développez **Environnement**, puis sélectionnez **Extensions et mises à jour**. Assurez-vous de cocher la case **Rechercher automatiquement les mises à jour** , puis choisissez **OK**.

## <a name="register-visual-studio"></a>Enregistrer Visual Studio

1. Dans la barre de menus, choisissez **Aide**, **À propos de**.

     La boîte de dialogue **À propos de** affiche le numéro d'identification du produit (PID). Vous avez besoin du PID et des informations d'identification d'un compte Windows (telles qu'une adresse de messagerie Hotmail ou Outlook.com et un mot de passe) pour inscrire le produit.

2. Dans la barre de menus, cliquez sur **Aide**, puis sur **Inscrire le produit**.

## <a name="repair-visual-studio"></a><a name="repair"></a>Réparer Visual Studio

#### <a name="to-repair-visual-studio"></a>Pour réparer Visual Studio

1. Dans le **Panneau de configuration**, dans la page **Programmes et fonctionnalités** , sélectionnez l'édition du produit que vous souhaitez réparer, puis sélectionnez **Modifier**.

2. Dans l'Assistant Installation, sélectionnez **Réparer**, **Suivant**, puis suivez les instructions restantes.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Pour réparer Visual Studio en mode silencieux ou passif (c’est-à-dire pour réparer à partir de la source)

1. Sur l'ordinateur où Visual Studio est installé, ouvrez l'invite de commandes Windows.

2. Entrez les paramètres suivants :

     FICHIER *d’installation* \> \< `/quiet|/passive` *DVDRoot* \\ <>`norestart`[/ ]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a>Dépanner une installation
 Utilisez ces ressources pour obtenir de l'aide sur les problèmes de configuration et d'installation.

- Forum[Installation et configuration de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) . Passez en revue les questions et les réponses des autres dans la communauté Visual Studio. Si vous ne trouvez pas ce dont vous avez besoin, posez vos propres questions.

- [Obtenez de l’aide avec Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Trouvez des articles de base de connaissances (KB) et apprenez à contacter Microsoft Support pour obtenir des informations sur les problèmes liés à l’installation visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a>Sujets connexes

|Intitulé|Description|
|-----------|-----------------|
|[Créer une installation hors ligne de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Décrit comment installer Visual Studio lorsque vous n’êtes pas connecté à Internet.
|[Installer visual Studio Versions Side-by-Side](../install/install-visual-studio-versions-side-by-side.md)|Fournit des informations concernant l’installation de plusieurs versions de Visual Studio sur le même ordinateur.|
|[Utiliser les paramètres de la ligne de commande pour installer Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Répertorie les paramètres de ligne de commande que vous pouvez utiliser lorsque vous installez Visual Studio à partir d’une invite de commande.|
|[Désinstaller Visual Studio](../install/uninstall-visual-studio.md)|Décrit comment désinstaller Visual Studio.|
|[Guide d’administrateur de studio visuel](../install/visual-studio-administrator-guide.md)|Fournit des informations concernant des options de déploiement pour Visual Studio.|
|[La Bibliothèque d’images Visual Studio](../designers/the-visual-studio-image-library.md)|Fournit des informations concernant l’installation de graphiques qui peuvent être utilisés dans les applications Visual Studio.|
|[Démarrer le développement avec Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Inclut des informations et des liens qui peuvent vous aider à utiliser Visual Studio plus efficacement.|

## <a name="see-also"></a>Voir aussi

- [Connexion à Visual Studio](../ide/signing-in-to-visual-studio.md)
