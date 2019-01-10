---
title: 'Procédure : Créer et exécuter une Installation sans assistance | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 0045ff701947f834bd38dfff7c90b7388e9353b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951928"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Procédure : Créer et exécuter une Installation sans assistance de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez exécuter l’application d’installation pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comme installation sans assistance via un intranet plutôt qu’à partir de supports tels que les DVD. Cette rubrique décrit comment préparer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour ce type d’installation à partir d’un partage réseau.

## <a name="creating-a-network-image"></a>Création d’une image réseau
 Tout d’abord, créez une image réseau du support [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-create-a-network-image"></a>Pour créer une image réseau

1.  Créez un dossier sur le serveur (par exemple, *Lecteur*:\IDEinstall\\).

2.  Télécharger le programme d’installation à partir de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015), puis exécutez *produit*.exe /Layout *lecteur*: \IDEinstall\

3.  Partagez le dossier IDEinstall sur le réseau et définir ensuite les paramètres de sécurité appropriés.

     Le chemin d’accès réseau de l’application d’installation pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ressemble à \\ \\ *nom_serveur*\IDEinstall\\*produit*.exe.

    > [!NOTE]
    >  L’installation peut échouer si la combinaison du nom du chemin d’accès et du fichier dépasse 260 caractères. La longueur maximale d’un chemin dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est de 221 caractères.  Le nom de chemin d’accès local ne doit pas dépasser 70 caractères et le nom du chemin d’accès réseau ne doit pas dépasser 39 caractères.

     L’installation peut également échouer si les noms de dossiers du chemin incluent des espaces incorporés (par exemple, "\\\\*nom_serveur*\installation IDE" ou \\\\*nom_serveur*\Visual Studio\\).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Déploiement de Visual Studio en mode sans assistance
 Pour déployer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en mode sans assistance, vous devez modifier le fichier AdminDeployment.xml. Pour ce faire, vous devez d’abord créer le fichier AdminDeployment.xml à l’aide de la `/CreateAdminFile`  *\<emplacement_fichier >* paramètre de ligne de commande. Ensuite, vous pouvez utiliser ce fichier pour pousser un déploiement de Visual Studio sur votre réseau ou l’extraire dans une installation si vous placez ce fichier dans le répertoire *Lecteur*:\IDEinstall\packages. Le fichier AdminDeployment.xml n’est pas propre à un système d’exploitation, une architecture, une version de Visual Studio ou un langage de système d’exploitation.

> [!CAUTION]
>  Parfois, les éléments répertoriés comme étant sélectionnés dans le fichier AdminDeployment.xml ne sont pas installés. Pour résoudre ce problème, placez à la **fin** du fichier AdminDeployment.xml les éléments marqués comme suit : « Selected="yes" ».
>
>  Si vous ne souhaitez pas installer les dépendances facultatives d’un élément, vous devez d’abord sélectionner le parent, puis désélectionner les dépendances facultatives après le parent, comme illustré dans la capture d’écran suivante :
>
>  ![Éléments de l’installation à la fin du fichier AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
>  Une autre façon de procéder consiste à simplement omettre les enfants facultatifs d’un parent (en d’autres termes, vous excluez les éléments « Selected="no" »), mais vous devez quand même placer tous les éléments « Selected="yes" » à la fin du fichier AdminDeployment.xml.

> [!IMPORTANT]
>  Pendant l’installation, l’ordinateur peut redémarrer automatiquement une ou plusieurs fois. Après qu’il a redémarré, vous devez vous reconnecter avec le même compte d’utilisateur que celui avec lequel vous étiez connecté pour effectuer l’installation avant le redémarrage de l’ordinateur. Vous pouvez éviter les redémarrages automatiques en installant les composants requis avant d’exécuter une installation sans assistance. Pour plus d’informations, consultez la section intitulée « Éviter le redémarrage lors de l’installation » dans le [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

 Le schéma de fichier AdminDeployment contient les éléments suivants :

|Élément|Attribut|Valeurs|Description|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Chemin d’accès*|Identique au remplacement du chemin d’accès dans l’interface utilisateur de l’application d’installation. Cet élément est ignoré si Visual Studio est déjà installé.|
|BundleCustomizations|NoWeb|Oui&#124;par défaut|Si la valeur de cet élément est Oui, l’application d’installation ne tente jamais d’accéder au web lors de l’action d’installation.|
|SelectableItemCustomization|Hidden|Oui&#124;non|Si la valeur de cet élément est Oui, masque un élément sélectionnable dans l’arborescence de la personnalisation.|
|SelectableItemCustomization|Selected|Oui&#124;non|Active ou désactive un élément sélectionnable dans l’arborescence de la personnalisation.|
|BundleCustomizations|Feed|Chemin|Emplacement du flux que l’utilisateur souhaite utiliser.  Ce flux est utilisé pour les opérations de modification ultérieures sur l’ordinateur (« Default » par défaut).|
|BundleCustomizations|SuppressRefreshPrompt|Oui&#124;par défaut|Empêche l’envoi d’invites demandant à l’utilisateur d’actualiser le programme d’installation si une version plus récente est disponible.|
|BundleCustomizations|NoRefresh|Oui&#124;par défaut|N’actualise pas le programme d’installation si une version plus récente est disponible.|
|BundleCustomizations|NoCacheOnlyMode|Oui&#124;par défaut|Empêche le préremplissage du cache du package.|

> [!WARNING]
>  L’application d’installation respecte l’état sélectionné d’un événement SelectableItem, même s’il est masqué. Par exemple, si vous souhaitez toujours installer un élément sélectionnable, vous pouvez le marquer comme masqué et sélectionné.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Pour créer une installation sans assistance de Visual Studio

1.  Dans le fichier *Lecteur*:\IDEinstall\AdminDeployment.xml, modifiez la valeur de l’attribut NoWeb de l’élément BundleCustomizations en remplaçant « par défaut » par « oui », comme le montre l’exemple suivant :

     Remplacer `<BundleCustomizations TargetDir="default" NoWeb="default"/>` par `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2.  Modifiez l’attribut SelectableItemCustomization si nécessaire pour les composants facultatifs, puis enregistrez le fichier.

## <a name="running-unattended-setup"></a>Exécution du programme d’installation sans assistance
 Vous pouvez exécuter le programme d’installation sans assistance en exécutant automatiquement l’application d’installation pour Visual Studio sur les ordinateurs clients ou en permettant aux utilisateurs d’exécuter l’application avec les paramètres que vous définissez.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Pour exécuter une installation sans assistance sur un ordinateur client

- Ouvrez le **Démarrer** menu, choisissez **exécuter**, puis entrez \\ \\ *nom_serveur*\IDEinstall\vs_*produit*.exe /adminfile *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>

   Par exemple, vous pouvez spécifier la ligne de commande suivante : `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Pour permettre aux clients d’installer manuellement Visual Studio avec des paramètres prédéfinis

1.  Copiez le fichier AdminDeployment.xml personnalisé sur un partage réseau qui est en lecture seule (par exemple, \\\\*nom_serveur*\IDEinstall\packages\AdminDeployment.xml).

2.  Autorisez les utilisateurs à installer à partir de ce partage.

## <a name="maintaining-an-installation"></a>Maintenance d’une installation
 Si vous ouvrez le **Panneau de configuration** et réexécutez l’application d’installation, vous pouvez modifier les fonctionnalités de Visual Studio, désinstaller les langages de programmation et réparer ou désinstaller Visual Studio.

> [!NOTE]
>  Vous devez avoir les informations d’identification de l’administrateur sur l’ordinateur local pour utiliser le mode maintenance.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Pour maintenir une installation sur un ordinateur client

-   Ouvrez le **Panneau de configuration**, puis choisissez **Programmes et fonctionnalités**.

-   Choisissez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puis choisissez **Modifier**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Pour modifier les paramètres d’AdminDeployment sur un ordinateur client après l’installation de Visual Studio

1. Mettez à jour admindeployment.xml si nécessaire.

2. Ouvrez le menu **Démarrer** , puis choisissez **Exécuter**.

3. Tapez le texte suivant : \\\\*Nom_serveur*\IDEinstall\vs_*produit*.exe /AdminFile PathToAdmindeployment.xml fichier

    AdditionalParametersAsNeeded

    Par exemple, vous pouvez spécifier la ligne de commande suivante : `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   La réparation est le paramètre par défaut après l’installation de Visual Studio. Si vous réparez Visual Studio avec un /AdminFile mis à jour, vous remplacent les paramètres de déploiement Admin actuelle avec ceux qui appelle le fichier AdminDeployment.xml mis à jour.

## <a name="updating-an-installation"></a>Une installation de la mise à jour
 Microsoft a publié plusieurs mises à jour de Visual Studio 2015. Cette section explique comment mettre à jour votre image d’installation sans assistance de Visual Studio 2015 afin qu’il inclue les mises à jour.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Pour mettre à jour une installation sans assistance de Visual Studio

1. Recherchez le fichier Product.exe dans l’image de réseau existant, faites un clic droit, puis cliquez sur **propriétés**.

2. Cliquez sur le **détails** onglet et notez le **version_produit** propriété.

    ![Exemple de la boîte de dialogue de propriétés dans une installation sans assistance de Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "installer sans assistance - boîte de dialogue Propriétés")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Si la version du produit est 14.0.24720.0 ou 14.0.24720.1, procédez comme suit :
4. 1.  Exécutez *Product.exe* /Layout *lecteur :* \IDEinstall sur un ordinateur qui a accès à Internet. (Par exemple, exécutez : `vs_enterprise.exe /Layout d:\IDEinstall`.)

   2.  Une fois terminée la/Layout, copiez la nouvelle image vers un nouvel emplacement.

   3.  Créer et modifier le fichier AdminDeployment.xml. Pour ce faire, utilisez le `/CreateAdminFile`  *\<emplacement_fichier >* paramètre de ligne de commande. (Pour plus d’informations, consultez la section « Déploiement Visual Studio en mode sans assistance » de cet article.)

   4.  Sur l’ordinateur client, exécutez la commande suivante pour mettre à jour la copie de Visual Studio que vous avez installé précédemment : «\\\\*server1*\IDEinstall_Updated_1\\*Product.exe*  /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart ».

        Par exemple, exécutez : `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>Pour les autres valeurs de version de produit, procédez comme suit :
6. 1.  Exécutez *Product.exe* /Layout *lecteur :* \IDEinstall sur un ordinateur qui a accès à Internet. (Par exemple, exécutez `vs-enterprise.exe /Layout d:\IDEinstall`.)

   2.  Une fois terminée la/Layout, copiez la nouvelle image vers un nouvel emplacement. (Ou, vous pouvez remplacer l’image de réseau existante à la place.)

   3.  Créez et modifiez le fichier AdminDeployment.xml. Pour ce faire, utilisez le `/CreateAdminFile`  *\<emplacement_fichier >* paramètre de ligne de commande. (Pour plus d’informations, consultez la section « Déploiement Visual Studio en mode sans assistance » de cet article.)

   4.  Si vous copiez l’image vers un nouvel emplacement, vous devez exécuter la commande suivante sur l’ordinateur client pour mettre à jour la copie de Visual Studio que vous avez installé précédemment : «\\\\*server1*\IDEinstall_Updated_1\\ *Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml/quiet/norestart ».

        Par exemple, exécutez : `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5.  Si vous remplacez l’image de réseau existante, vous pouvez exécuter la commande comme indiqué dans l’étape précédente, ou vous pouvez effectuer les opérations suivantes :

   6.  1.  Ouvrez le **Panneau de configuration**, puis choisissez **Programmes et fonctionnalités**.

       2.  Choisissez **Visual Studio**, puis choisissez **modification**.

       3.  Une fois que Visual Studio démarre en mode maintenance, cliquez sur **modifier**.

       4.  La dernière mise à jour doit apparaître sur la page de fonctionnalités. Sélectionnez les autres fonctionnalités que vous souhaitez installer, cliquez sur **suivant**, puis cliquez sur **mettre à jour** pour installer la mise à jour et les nouvelles fonctionnalités.

## <a name="registering-the-product"></a>Inscription du produit
 Une fois l’installation terminée, vous pouvez enregistrer votre copie de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] depuis [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-register"></a>Pour inscrire

1.  Ouvrez le menu **Aide** , puis choisissez **Inscrire le produit**.

2.  Entrez la clé du produit.

     Pour plus d’informations, consultez la page [Guide pratique pour Recherchez la clé de produit Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) et [Comment : Appliquer automatiquement les clés de produit lors du déploiement de Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) rubriques.)

## <a name="see-also"></a>Voir aussi
 [Installer Visual Studio](../install/install-visual-studio-2015.md)