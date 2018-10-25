---
title: Installer Visual Studio 2015 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
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
manager: ghogen
ms.openlocfilehash: df09e647908b264ade467b8fafd4487641d3be6c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841102"
---
# <a name="install-visual-studio-2015"></a>Installer Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour la dernière documentation d’installation pour Visual Studio 2017, consultez [installer Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio). Pour afficher les informations d’installation des versions précédentes de Visual Studio, cliquez sur le lien « Autres versions » en haut de cette page.

Cette page inclut des informations détaillées pour vous aider à installer **Visual Studio 2015**, notre suite intégrée d’outils de productivité pour les développeurs. Nous avons aussi inclus des liens vous permettant d’accéder rapidement à des informations sur les [fonctionnalités](https://www.visualstudio.com/news/vs2015-vs.aspx), les [éditions](http://go.microsoft.com/fwlink/?LinkID=242142), la [configuration requise](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), les [téléchargements](http://go.microsoft.com/fwlink/?LinkId=517106)et bien plus encore.  
  

## <a name="quick-links"></a>Liens rapides  
 Avant d’entrer dans les détails, voici une liste de nos liens les plus demandés.  
  
|||  
|------------------|----------------| 
|![Téléchargez Visual Studio](../install/media/downloads.png "téléchargements") |**Téléchargements**: pour installer Visual Studio 2015, vous pouvez télécharger un fichier exécutable de produit à partir de la [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) page (abonnement requis), ou utiliser le support d’installation à partir du produit boxed. [En savoir plus sur le téléchargement en cours ou les versions antérieures de Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![En savoir plus sur les fonctionnalités](../install/media/features.png "fonctionnalités") |**Fonctionnalités**: pour en savoir plus sur les fonctionnalités de Visual Studio 2015, consultez les notes de publication pour [RTM](https://www.visualstudio.com/news/vs2015-vs), [mise à jour 1](https://www.visualstudio.com/news/vs2015-update1-vs), [mise à jour 2](https://www.visualstudio.com/news/vs2015-update2-vs), et [ Mise à jour 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|  
|![Découvrir les nouveautés dans chaque référence (SKU)](../install/media/sku.png "références (SKU)") |**Références (SKU)**: pour savoir ce qui est disponible dans chaque édition de Visual Studio 2015, consultez notre [comparer les offres Visual Studio](http://go.microsoft.com/fwlink/?LinkID=242142) page.|  
|![Configuration système requise](../install/media/system-requirements.png "configuration système requise") |**Configuration système requise**: pour afficher la configuration système requise pour chaque édition de Visual Studio 2015, consultez le [compatibilité de Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) page.|  
|![Recherchez votre clé de produit](../install/media/product-keys.png "clés de produit") |**Clés de produit**: pour trouver votre clé de produit, consultez le [Comment : trouver la clé de produit Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) rubrique.|  
|![Découvrez les licences](../install/media/licensing.png "Gestionnaire de licences") |**Gestion des licences**: pour connaître les options de licence pour les individus ou les clients d’entreprise, consultez le [licences Visual Studio et MSDN](https://www.microsoft.com/download/details.aspx?id=13350) livre blanc.|  
  
##  <a name="custom"></a> Visual Studio par défaut. installation personnalisée  
 Au moment d’installer Visual Studio 2015, vous pouvez inclure les composants que vous prévoyez d’utiliser au quotidien et exclure les autres. Cela signifie qu’une installation par défaut sera souvent plus petite et plus rapide à installer qu’une installation personnalisée. Cela signifie aussi que bon nombre de composants qui étaient installés par défaut dans les versions précédentes sont maintenant considérés comme des composants personnalisés que vous devez sélectionner explicitement dans cette version.  
  
 ![Boîte de dialogue d’installation Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")  
  
 Les composants personnalisés incluent Visual C++, Visual F#, SQL Server Data Tools, les outils mobiles multiplateformes et les Kits de développement logiciel (SDK), ainsi que les extensions et les SDK tiers. Vous pouvez installer les composants personnalisés ultérieurement si vous ne les sélectionnez pas pendant l’installation initiale.  
  
> [!NOTE]
>  Une installation personnalisée inclut automatiquement les composants qui figurent dans une installation par défaut.  
  
 Voici la liste complète des composants personnalisés :  
  
|Ensembles de fonctionnalités|Composants|  
|------------------|----------------|  
|**Mises à jour**|Visual Studio 2015 Update 3|  
|**Langages de programmation**|Visual C++<br />Visual F#<br />Outils Python pour Visual Studio|  
|**Développement Web et Windows**|Outils de publication de ClickOnce<br />LightSwitch<br />Outils de développement Microsoft Office<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />Outils PowerShell pour Visual Studio (3e partie)<br />Kit de développement Silverlight<br />Outils de développement d’applications Windows universelles<br />Kits de développement logiciel (SDK) et outils Windows 10<br />Outils Windows 8.1 et Windows Phone 8.0/8.1<br />Kits de développement logiciel (SDK) et outils Windows 8.1|  
|**Développement Mobile interplateforme**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Développement mobile Visual C++ pour iOS / Android<br />Clang avec Microsoft CodeGen|  
|**Kits de développement logiciel et outils courants**|Kit de développement natif Android (3e partie)<br /> Kit de développement logiciel Android [3e partie]<br />API du programme d’installation du Kit Android SDK (3e partie)<br />Apache Ant (3e partie)<br /> Java SE Development Kit (3e partie)<br /> Joyent Node.js (3e partie)|  
|**Outils courants**|GIT pour Windows (3e partie)<br />Extension GitHub pour Visual Studio (3e partie)<br /> Outils d'extensibilité de Visual Studio|  
  
##  <a name="installing"></a> Installation de Visual Studio  
 Vous pouvez installer Visual Studio à l’aide du support d’installation (DVD), à l’aide de votre service d’abonnement Visual Studio à partir de la [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) site Web, en téléchargeant un programme d’installation web à partir de la [Visual Studio Téléchargements](http://go.microsoft.com/fwlink/?LinkId=517106) site Web, ou en créant une disposition d’installation hors connexion (voir la [créer une Installation hors connexion de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) page pour plus d’informations).  
  
> [!IMPORTANT]
>  Vous avez besoin d’informations d’identification d’administrateur pour installer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Toutefois, elles ne sont pas requises pour utiliser [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] après son installation.  
  
 Les privilèges suivants de votre compte d'administrateur local doivent autoriser l'installation de tous les composants de Visual Studio.  
  
|Nom d'affichage de l'objet de stratégie locale|Droit d'utilisateur|  
|--------------------------------------|----------------|  
|Sauvegarder les fichiers et les répertoires|SeBackupPrivilege|  
|Déboguer les programmes|SeDebugPrivilege|  
|Gérer le journal d'audit et de sécurité|SeSecurityPrivilege|  
  
 Pour plus d’informations sur cette exigence de compte d’administrateur local, consultez l’article suivant de la Base de connaissances : [Échec de l’installation de SQL Server si le compte d’installation ne possède pas certains droits d’utilisateur](https://support.microsoft.com/en-us/kb/2000257).  
  
###  <a name="BKMK_Media"></a> À l’aide du support d’installation  
 Pour installer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], dans le répertoire racine du support d'installation de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , exécutez le fichier d'installation de l'édition souhaitée :  
  
|Édition|Fichier d'installation|  
|-------------|-----------------------|  
|Visual Studio Enterprise|vs_enterprise.exe|  
|Visual Studio Professional|vs_professional.exe|  
|Communauté Visual Studio|vs_community.exe|  
  
###  <a name="BKMK_Website"></a> Téléchargement à partir du site Web du produit  
 Visitez le [téléchargements Visual Studio](http://go.microsoft.com/fwlink/?LinkId=517106) page, puis sélectionnez l’édition de Visual Studio que vous souhaitez.  
  
### <a name="downloading-from-your-subscription-service"></a>Téléchargement à partir de votre service d’abonnement  
 Visitez le [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) page, puis sélectionnez l’édition de Visual Studio que vous souhaitez.  
  
###  <a name="BKMK_Offline"></a> Création d’une disposition d’installation hors connexion  
 Si vous n’avez pas le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] support d’installation, ou vous ne possédez pas d’un abonnement Visual Studio, ou vous ne souhaitez pas installer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en utilisant le programme d’installation web, vous pouvez effectuer une installation « déconnectée » en créant ce que l'on appelle un hors connexion disposition d’installation. Pour plus d’informations, consultez le [créer une Installation hors connexion de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) page.  
  
##  <a name="enterprise"></a> Déploiement de Visual Studio dans une entreprise  
 Pour plus d’informations sur le déploiement [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sur un réseau, consultez le [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).  
  
###  <a name="BKMK_Virtualized"></a> Installation de Visual Studio dans un environnement virtualisé  
 **Problèmes vidéo avec Hyper-V**  
  
 Si vous exécutez Windows Server 2008 R2 avec Hyper-V activé et une carte graphique accélérée, il se peut que vous rencontriez des ralentissements du système.  
  
 Pour plus d’informations, consultez sur le site web Microsoft la page suivante, qui explique pourquoi les [performances vidéo peuvent diminuer quand un ordinateur Windows Server 2008 ou Windows Server 2008 R2 a le rôle Hyper-V activé et une carte graphique accélérée installée](http://go.microsoft.com/fwlink/?LinkID=231084).  
  
 **Émulation de périphériques avec Hyper-V**  
  
 Quand vous installez Visual Studio 2015 sur du vrai matériel, sans virtualisation, vous pouvez choisir les fonctionnalités qui permettent d'émuler les appareils Windows et Android avec Hyper-V. En revanche, quand vous effectuez l'installation dans Hyper-V, vous ne pouvez pas émuler les appareils Windows ou Android. Ceci est dû au fait que les émulateurs sont eux-mêmes des machines virtuelles et que vous ne pouvez pas héberger actuellement une machine virtuelle à l'intérieur d'une autre machine virtuelle. Une solution de contournement consiste à faire l'acquisition d'appareils Windows ou Android sur lesquels vous pouvez directement déployer et déboguer votre application.  
  
##  <a name="optionalComponents"></a> Installation des composants facultatifs  
 Si vous souhaitez installer les composants que vous avez ne peut-être pas activé lors de l’installation d’origine, procédez comme suit.  
  
#### <a name="to-install-optional-components"></a>Pour installer les composants facultatifs  
  
1.  Dans **Panneau de configuration**, dans la page **Programmes et fonctionnalités** , sélectionnez l'édition du produit à laquelle vous souhaitez ajouter un ou plusieurs composants, puis cliquez sur **Modifier**.  
  
2.  Dans l'Assistant Installation, sélectionnez **Modifier**, puis sélectionnez les composants que vous souhaitez installer.  
  
3.  Choisissez **Suivant**, puis suivez les instructions restantes.  
  
##  <a name="helpContent"></a> Installation du contenu d’aide hors connexion  
 Après avoir installé [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez télécharger le contenu d'aide supplémentaire afin qu'il soit disponible hors connexion.  
  
#### <a name="to-install-or-uninstall-help-content"></a>Pour installer ou désinstaller le contenu de l'aide  
  
1. Dans la barre de menus [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , choisissez **Aide**, **Ajouter et supprimer le contenu d'aide**.  
  
2. Sous l'onglet **Gérer le contenu** de la **Visionneuse d'aide Microsoft**, sélectionnez la source d'installation pour votre contenu d'aide.  
  
3. Si vous avez besoin d’une collection d’aide spécifique, entrez le nom ou un mot clé dans le **recherche** zone de texte et appuyez sur **entrée**.  
  
4. À côté du nom de la collection d'aide souhaitée, choisissez le lien **Ajouter** ou **Supprimer** .  
  
5. Cliquez sur le **mise à jour** bouton.  
  
   Pour plus d’informations sur la façon d’installer ou de déployer en mode hors connexion, consultez le [Guide administrateur de la visionneuse d’aide](../ide/help-viewer-administrator-guide.md).  
  
##  <a name="serviceReleases"></a> Vérification des Service Packs et mises à jour de produit  
 Étant donné que toutes les extensions ne sont compatibles, Visual Studio n’automatiquement à niveau les extensions lorsque vous mettez à niveau à partir de versions précédentes. Vous devez réinstaller les extensions à partir de la [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) ou à partir de l’éditeur de logiciel.  
  
#### <a name="to-automatically-check-for-service-releases"></a>Pour rechercher automatiquement les publications du service  
  
1.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
2.  Dans la boîte de dialogue **Options** , développez **Environnement**, puis sélectionnez **Extensions et mises à jour**. Assurez-vous de cocher la case **Rechercher automatiquement les mises à jour** , puis choisissez **OK**.  
  
## <a name="registering-visual-studio"></a>Inscription de Visual Studio  
  
1.  Dans la barre de menus, choisissez **Aide**, **À propos de**.  
  
     La boîte de dialogue **À propos de** affiche le numéro d'identification du produit (PID). Vous avez besoin du PID et des informations d'identification d'un compte Windows (telles qu'une adresse de messagerie Hotmail ou Outlook.com et un mot de passe) pour inscrire le produit.  
  
2.  Dans la barre de menus, cliquez sur **Aide**, puis sur **Inscrire le produit**.  
  
##  <a name="repair"></a> Réparation de Visual Studio  
  
#### <a name="to-repair-visual-studio"></a>Pour réparer Visual Studio  
  
1.  Dans le **Panneau de configuration**, dans la page **Programmes et fonctionnalités** , sélectionnez l'édition du produit que vous souhaitez réparer, puis sélectionnez **Modifier**.  
  
2.  Dans l'Assistant Installation, sélectionnez **Réparer**, **Suivant**, puis suivez les instructions restantes.  
  
#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Pour réparer Visual Studio en mode silencieux ou passif (autrement dit, réparer à partir de la source)  
  
1.  Sur l'ordinateur où Visual Studio est installé, ouvrez l'invite de commandes Windows.  
  
2.  Entrez les paramètres suivants :  
  
     *DVDRoot* \\< fichier d’Installation\> \</quiet/&#124;/passive > [/norestart] /Repair  
  
##  <a name="troubleshooting"></a> Dépannage d’une installation  
 Utilisez ces ressources pour obtenir de l'aide sur les problèmes de configuration et d'installation.  
  
-   Forum[Installation et configuration de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=151190) . Passez en revue les questions et les réponses des autres dans la communauté Visual Studio. Si vous ne trouvez pas ce dont vous avez besoin, posez vos propres questions.  
  
-   Site web de[support technique Microsoft pour Visual Studio](http://go.microsoft.com/fwlink/?LinkID=251019) . Lisez les articles de la Base de connaissances et apprenez comment contacter le support technique Microsoft pour obtenir plus d'informations sur les problèmes liés à l'installation de Visual Studio.  
  
-   Pour les versions de Visual Studio 2015, vous pouvez signaler votre problème à l’aide du site Connect à l’adresse [ https://connect.microsoft.com/visualstudio ](https://connect.microsoft.com/visualstudio).  
  
     Il est recommandé d'inclure les journaux d'installation avec votre problème. Vous pouvez préparer vos journaux pour le signalement de votre problème à l'aide de l'outil Microsoft Visual Studio and .NET Framework Log Collection Tool, comme indiqué dans les étapes suivantes.  
  
    1.  Téléchargez l’outil de diagnostic d’installation à partir de [ http://aka.ms/vscollect ](http://aka.ms/vscollect).  
  
    2.  À partir d'une invite de commandes avec élévation de privilèges, exécutez le programme collect.exe.  
  
    3.  Une fois le programme collect.exe terminé, récupérez le fichier vslogs.cab de votre répertoire Temp et chargez-le dans le rapport du problème.  
  
##  <a name="relatedTopics"></a> Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Créer une installation hors connexion de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Décrit comment installer Visual Studio lorsque vous n’êtes pas connecté à Internet.
|[Installer des versions de Visual Studio côte à côte](../install/install-visual-studio-versions-side-by-side.md)|Fournit des informations concernant l’installation de plusieurs versions de Visual Studio sur le même ordinateur.|  
|[Utiliser les paramètres de ligne de commande pour installer Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Répertorie les paramètres de ligne de commande que vous pouvez utiliser lorsque vous installez Visual Studio à partir d’une invite de commandes.|  
|[Désinstaller Visual Studio](../install/uninstall-visual-studio.md)|Décrit comment désinstaller Visual Studio.|  
|[Guide de l’administrateur Visual Studio](../install/visual-studio-administrator-guide.md)|Fournit des informations concernant des options de déploiement pour Visual Studio.|  
|[Bibliothèque d’images Visual Studio](../designers/the-visual-studio-image-library.md)|Fournit des informations concernant l’installation de graphiques qui peuvent être utilisés dans les applications Visual Studio.|  
|[Bien démarrer avec le développement dans Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Inclut des informations et des liens qui peuvent vous aider à utiliser Visual Studio plus efficacement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à Visual Studio](../ide/signing-in-to-visual-studio.md)