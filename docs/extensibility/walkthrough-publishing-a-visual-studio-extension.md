---
title: 'Procédure pas à pas : Publication d’une extension de studio visuel (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697139"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Procédure pas à pas : Publier une extension de Visual Studio

Cette procédure pas à pas vous montre comment publier une extension Visual Studio au Visual Studio Marketplace. Lorsque vous ajoutez votre extension au Marketplace, les développeurs peuvent utiliser **des extensions et des mises** à jour pour parcourir des extensions nouvelles et mises à jour.

## <a name="prerequisites"></a>Prérequis

 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Créer une extension Visual Studio

Cet article utilise une extension VSPackage par défaut, mais les étapes sont valables pour chaque type d’extension.

1. Créez un VSPackage en `TestPublish` C nommé qui a une commande de menu. Pour plus d’informations, voir [Créer votre première extension: Bonjour Monde](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Empaqueter votre extension

1. Mettre à jour l’extension *.vsixmanifest* avec les informations correctes sur le nom du produit, l’auteur et la version.

   ![mise à jour de l’extension vsixmanifest](media/update-extension-vsixmanifest.png)

2. Construisez votre extension en mode **Version.** Maintenant, votre extension est emballée comme un VSIX dans le dossier 'bin’Release.

3. Vous pouvez cliquer deux fois sur le VSIX pour vérifier l’installation.

## <a name="test-the-extension"></a>Testez l’extension

 Avant de distribuer l’extension, construisez et testez-la pour vous assurer qu’elle est installée correctement dans l’instance expérimentale de Visual Studio.

1. Dans Visual Studio, commencez à débogage pour ouvrir une instance expérimentale de Visual Studio.

2. Dans le cas expérimental, allez au menu **Tools** et cliquez sur **Extensions et Mises à jour**. L’extension TestPublish doit apparaître dans le volet central et être activée.

3. Sur le menu **Tools,** assurez-vous de voir la commande de test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publier l’extension du Visual Studio Marketplace

1. Assurez-vous d’avoir construit la version Version Version de votre extension et qu’elle est à jour.

2. Dans un navigateur Web, ouvrez le site [Web Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

3. Dans le coin supérieur droit, cliquez sur **Connectez-vous**.

4. Utilisez votre compte Microsoft pour vous connecter. Si vous n’avez pas de compte Microsoft, vous pouvez en créer un à ce stade.

5. Cliquez **sur Publier les extensions**.  Cette option vous guide vers la page de gestion de toutes vos extensions. Si vous n’avez pas de compte d’éditeur, vous êtes invité à en créer un pour le moment.

   ![Télécharger sur Marketplace](media/upload-to-marketplace.png)

6. Choisissez l’éditeur que vous souhaitez utiliser pour télécharger votre extension. Vous pouvez changer d’éditeur en cliquant sur les noms d’éditeurs répertoriés à gauche. Cliquez sur **nouvelle extension** et sélectionnez **Visual Studio**.

7. Dans **1: Extension de téléchargement**, vous pouvez choisir de télécharger un fichier VSIX directement sur Visual Studio Marketplace ou tout simplement ajouter un lien vers votre propre site Web. Dans cet exemple, l’extension, *TestPublish.vsix* est téléchargée. Faites glisser et laissez tomber votre extension ou utilisez le lien **de clic** pour parcourir le fichier. Trouvez votre extension dans le dossier 'bin’Release du projet.  Cliquez sur **Continuer**.

8. Dans **2: Fournir des détails d’extension**, certains champs sont auto-peuplés à partir du fichier *source.extension.vsixmanifest* de votre extension. Pour plus de détails sur chacun ci-dessous :

    * **Le nom interne** est utilisé dans l’URL de la page de détail de l’extension. Par exemple, la publication d’une extension sous le nom d’éditeur "myname" et la spécit\.du nom interne pour être "mon extension" aboutit à une URL de "marketplace.visualstudio com/items?itemName-myextension" pour la page de détail de votre extension.

    * **Afficher le nom** de votre extension. Ce nom est auto-peuplé à partir du fichier *source.extension.vsixmanifest.*

    * **Numéro** de version de l’extension que vous téléchargez. Cette version est auto-peuplée à partir du fichier *source.extension.vsixmanifest.*

    * **VSIX ID** est l’identifiant unique que Visual Studio utilise pour votre extension. Cet identifiant est requis si vous souhaitez que votre extension soit mise à jour automatiquement. Cet identifiant est auto-peuplé à partir du fichier *source.extension.vsixmanifest.*

    * **Logo** qui est utilisé pour votre extension. Ce logo est auto-peuplé à partir du fichier *source.extension.vsixmanifest* si fourni.

    * **Courte description** de ce que fait votre extension. Cette description est auto-peuplée à partir du fichier *source.extension.vsixmanifest.*

    * **Aperçu** est un bon endroit pour inclure des captures d’écran et des informations détaillées sur ce que votre extension fait.

    * **Les versions Visual Studio prises en** charge vous permettent de choisir les versions de Visual Studio sur lesquelles votre extension fonctionnera. Votre extension n’est installée que sur ces versions.

    * L’édition Visual Studio vous permet de choisir les éditions de Visual Studio sur lesquelles votre extension fonctionnera. Votre extension n’est installée que sur ces éditions.

    * **Type**. Le type le plus commun d’extensions sont **Outils**.

    * **Catégories**. Ramassez jusqu’à trois qui conviennent le mieux à votre extension.

    * **Les balises** sont des mots clés qui aident les utilisateurs à trouver votre extension. Les balises peuvent aider à augmenter la pertinence de recherche de vos extensions sur le marché.

    * **La catégorie de prix** est le coût de votre extension.

    * **Le référentiel de code source** vous permet de partager un lien vers votre code source avec la communauté.

    * **Autoriser Q&A pour votre extension** permet aux utilisateurs de laisser des questions sur votre page d’entrée d’extension.

9. Cliquez **sur Enregistrer & Télécharger**. Cette option vous ramène à votre éditeur gérer la page. Votre extension n’a pas encore été publiée. Pour publier votre extension, cliquez à droite sur votre extension et **sélectionnez Rendez-vous public**. Vous pouvez voir à quoi ressemblera votre extension sur Marketplace en sélectionnant **View Extension**. Pour les numéros d’acquisition, cliquez sur **Les rapports**. Pour apporter des modifications à votre extension, cliquez sur **Edit**.

   ![Menu d’entrée d’extension](media/extension-entry-menu.png)

10. Après avoir cliqué **Sur Make Public**, votre extension est maintenant publique. Recherchez votre extension sur le marché visual studio.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Ajouter d’autres utilisateurs pour gérer votre compte d’éditeur

Marketplace prend en charge l’octroi d’autorisations supplémentaires aux utilisateurs pour accéder et gérer un compte d’éditeur.

1. Naviguez vers le compte éditeur à laquelle vous souhaitez ajouter d’autres utilisateurs.

2. Sélectionnez **les membres** et cliquez sur **Ajouter**.

   ![Ajouter un utilisateur supplémentaire](media/add-users.png)

3. Vous pouvez ensuite spécifier l’adresse e-mail de l’utilisateur que vous souhaitez ajouter et accorder le bon niveau d’accès sous **Sélectionnez un rôle**.  Vous pouvez choisir parmi les options suivantes :

   * **Créateur**: L’utilisateur peut publier des extensions, mais ne peut pas afficher ou gérer les extensions publiées par d’autres utilisateurs.

   * **Lecteur**: L’utilisateur peut afficher des extensions, mais ne peut pas publier ou gérer les extensions.

   * **Contributeur**: L’utilisateur peut publier et gérer des extensions, mais ne peut pas modifier les paramètres de l’éditeur ou gérer l’accès.

   * **Propriétaire**: L’utilisateur peut publier et gérer des extensions, modifier les paramètres de l’éditeur et gérer l’accès.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installer l’extension à partir du marché visual Studio

Maintenant que l’extension est publiée, installez-la dans Visual Studio et testez-la là.

1. Dans Visual Studio, sur le menu **Tools,** cliquez sur **Extensions et Mises à jour**.

2. Cliquez **en ligne,** puis recherchez **TestPublish**.

3. Cliquez sur **Télécharger**. L’extension est alors prévue pour l’installation.

4. Pour compléter l’installation, fermez toutes les instances de Visual Studio.

## <a name="remove-the-extension"></a>Supprimer l’extension

Vous pouvez supprimer l’extension du Visual Studio Marketplace et de votre ordinateur.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Supprimer l’extension du Visual Studio Marketplace

1. Ouvrez le site [Web visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

2. Dans le coin supérieur droit, cliquez sur Les extensions **Publier.** Choisissez l’éditeur que vous avez utilisé pour publier **TestPublish**. La liste pour **TestPublish** apparaît.

3. Cliquez à droite sur l’entrée d’extension et cliquez sur **Supprimer**. On vous demande de confirmer si vous voulez supprimer l’extension. Cliquez sur **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension de votre ordinateur

1. Dans Visual Studio, sur le menu **Tools,** cliquez sur **Extensions et Mises à jour**.

2. Sélectionnez **TestPublish,** puis cliquez sur **Uninstall**. L’extension est alors prévue pour un désinstallation.

3. Pour compléter la désinstallation, fermez toutes les instances de Visual Studio.
