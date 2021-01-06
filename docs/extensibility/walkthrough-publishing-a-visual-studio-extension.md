---
title: 'Procédure pas à pas : publication d’une extension Visual Studio | Microsoft Docs'
description: Découvrez comment publier une extension Visual Studio dans le Visual Studio Marketplace, ce qui permet aux développeurs de rechercher les extensions nouvelles et mises à jour.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbdd283c5d147c53e7d82843207b48d0dbf6e6e9
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877882"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Procédure pas à pas : publication d’une extension Visual Studio

Cette procédure pas à pas vous montre comment publier une extension Visual Studio sur le Visual Studio Marketplace. Lorsque vous ajoutez votre extension au Marketplace, les développeurs peuvent utiliser des **extensions et des mises à jour** pour rechercher les extensions nouvelles et mises à jour.

## <a name="prerequisites"></a>Prérequis

 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Créer une extension Visual Studio

Cet article utilise une extension VSPackage par défaut, mais les étapes sont valides pour chaque type d’extension.

1. Créez un VSPackage en C# nommé `TestPublish` qui comporte une commande de menu. Pour plus d’informations, consultez [créer votre première extension : Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Empaqueter votre extension

1. Mettez à jour l’extension *. vsixmanifest* avec les informations correctes sur le nom du produit, l’auteur et la version.

   ![mettre à jour l’extension vsixmanifest](media/update-extension-vsixmanifest.png)

2. Générez votre extension en mode **Release** . Votre extension est maintenant empaquetée en tant que VSIX dans le dossier \bin\Release

3. Vous pouvez double-cliquer sur le VSIX pour vérifier l’installation.

## <a name="test-the-extension"></a>Tester l’extension

 Avant de distribuer l’extension, générez et testez-la pour vous assurer qu’elle est installée correctement dans l’instance expérimentale de Visual Studio.

1. Dans Visual Studio, démarrez le débogage pour ouvrir une instance expérimentale de Visual Studio.

2. Dans l’instance expérimentale, accédez au menu **Outils** , puis cliquez sur **extensions et mises à jour**. L’extension TestPublish doit apparaître dans le volet central et être activée.

3. Dans le menu **Outils** , vérifiez que vous voyez la commande test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publier l’extension sur le Visual Studio Marketplace

1. Assurez-vous que vous avez créé la version Release de votre extension et qu’elle est à jour.

2. Dans un navigateur Web, ouvrez le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) .

3. Dans l’angle supérieur droit, cliquez sur **se connecter**.

4. Utilisez votre compte Microsoft pour vous connecter. Si vous n’avez pas de compte Microsoft, vous pouvez en créer un à ce stade.

5. Cliquez sur **publier des extensions**.  Cette option vous permet d’accéder à la page gérer pour toutes vos extensions. Si vous n’avez pas de compte d’éditeur, vous êtes invité à en créer un pour l’instant.

   ![Télécharger sur la place de marché](media/upload-to-marketplace.png)

6. Choisissez le serveur de publication que vous souhaitez utiliser pour télécharger votre extension. Vous pouvez modifier les serveurs de publication en cliquant sur les noms des serveurs de publication figurant sur la gauche. Cliquez sur **nouvelle extension** , puis sélectionnez **Visual Studio**.

7. Dans **1 : charger l’extension**, vous pouvez choisir de télécharger un fichier VSIX directement vers Visual Studio Marketplace ou simplement ajouter un lien vers votre propre site Web. Dans cet exemple, l’extension *TestPublish. vsix* est téléchargée. Glissez-déplacez votre extension ou utilisez le lien de **clic** pour rechercher le fichier. Recherchez votre extension dans le dossier \bin\Release du projet.  Cliquez sur **Continuer**.

8. Dans **2 : fournir les détails** de l’extension, certains champs sont remplis automatiquement à partir du fichier *source. extension. vsixmanifest* de votre extension. Pour plus d’informations, consultez les informations ci-dessous :

    * Le **nom interne** est utilisé dans l’URL de la page de détails de l’extension. Par exemple, la publication d’une extension sous le nom de l’éditeur « myname » et la spécification du nom interne comme « mon extension » génère une URL « Marketplace. VisualStudio \. com/items ? ItemName = myname. MyExtension » pour la page de détails de votre extension.

    * **Nom d’affichage** de votre extension. Ce nom est renseigné automatiquement à partir du fichier *source. extension. vsixmanifest* .

    * Numéro de **version** de l’extension que vous chargez. Cette version est remplie automatiquement à partir du fichier *source. extension. vsixmanifest* .

    * L' **ID VSIX** est l’identificateur unique que Visual Studio utilise pour votre extension. Cet identificateur est requis si vous souhaitez que votre extension soit mise à jour automatiquement. Cet identificateur est rempli automatiquement à partir du fichier *source. extension. vsixmanifest* .

    * **Logo** utilisé pour votre extension. Ce logo est rempli automatiquement à partir du fichier *source. extension. vsixmanifest* , s’il est fourni.

    * **Brève description** de ce que fait votre extension. Cette description est remplie automatiquement à partir du fichier *source. extension. vsixmanifest* .

    * La **vue d’ensemble** est un bon endroit pour inclure des captures d’écran et des informations détaillées sur ce que fait votre extension.

    * **Versions de Visual Studio prises en charge** vous permet de choisir les versions de Visual Studio sur lesquelles votre extension fonctionnera. Votre extension est installée uniquement sur ces versions.

    * * * L’édition de Visual Studio prise en charge vous permet de choisir les éditions de Visual Studio sur lesquelles utiliser votre extension. Votre extension est installée uniquement dans ces éditions.

    * **Type**. Les extensions les plus courantes sont les **Outils**.

    * **Catégories**. Sélectionnez jusqu’à trois qui conviennent le mieux à votre extension.

    * Les **balises** sont des mots clés qui aident les utilisateurs à trouver votre extension. Les balises peuvent vous aider à augmenter la pertinence de la recherche de vos extensions sur la place de marché.

    * La **catégorie de tarification** est le coût de votre extension.

    * Le **référentiel de code source** vous permet de partager un lien vers votre code source avec la communauté.

    * **Allow Q&A pour votre extension** permet aux utilisateurs de laisser des questions sur la page d’entrée de votre extension.

9. Cliquez sur **enregistrer & Télécharger**. Cette option vous permet de revenir à la page de gestion de votre éditeur. Votre extension n’a pas encore été publiée. Pour publier votre extension, cliquez avec le bouton droit sur votre extension et sélectionnez **rendre public**. Vous pouvez afficher l’aspect de votre extension sur la place de marché en sélectionnant **afficher l’extension**. Pour les numéros d’acquisition, cliquez sur **rapports**. Pour apporter des modifications à votre extension, cliquez sur **modifier**.

   ![Menu de l’entrée d’extension](media/extension-entry-menu.png)

10. Une fois que vous avez cliqué sur **rendre public**, votre extension est désormais publique. Recherchez votre extension dans le Visual Studio Marketplace.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Ajouter des utilisateurs supplémentaires pour gérer votre compte d’éditeur

Marketplace prend en charge l’octroi d’autorisations d’utilisateurs supplémentaires pour accéder à un compte d’éditeur et le gérer.

1. Accédez au compte d’éditeur auquel vous souhaitez ajouter des utilisateurs supplémentaires.

2. Sélectionnez **membres** , puis cliquez sur **Ajouter**.

   ![Ajouter un utilisateur supplémentaire](media/add-users.png)

3. Vous pouvez ensuite spécifier l’adresse de messagerie de l’utilisateur que vous souhaitez ajouter et accorder le niveau d’accès approprié sous **Sélectionner un rôle**.  Vous pouvez choisir parmi les options suivantes :

   * **Créateur**: l’utilisateur peut publier des extensions, mais il ne peut pas afficher ou gérer les extensions publiées par d’autres utilisateurs.

   * **Lecteur**: l’utilisateur peut afficher les extensions, mais ne peut pas publier ou gérer les extensions.

   * **Contributeur**: l’utilisateur peut publier et gérer les extensions, mais il ne peut pas modifier les paramètres du serveur de publication ni gérer l’accès.

   * **Propriétaire**: l’utilisateur peut publier et gérer des extensions, modifier les paramètres du serveur de publication et gérer l’accès.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installer l’extension à partir de la Visual Studio Marketplace

Maintenant que l’extension est publiée, installez-la dans Visual Studio et testez-la ici.

1. Dans Visual Studio, dans le menu **Outils** , cliquez sur **extensions et mises à jour**.

2. Cliquez sur **en ligne** , puis recherchez **TestPublish**.

3. Cliquez sur **Télécharger**. L’extension est alors planifiée pour l’installation.

4. Pour terminer l’installation, fermez toutes les instances de Visual Studio.

## <a name="remove-the-extension"></a>Supprimer l’extension

Vous pouvez supprimer l’extension de la Visual Studio Marketplace et de votre ordinateur.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Pour supprimer l’extension de la Visual Studio Marketplace

1. Ouvrez le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) .

2. Dans l’angle supérieur droit, cliquez sur **publier** les extensions. Sélectionnez le serveur de publication que vous avez utilisé pour publier **TestPublish**. La liste de **TestPublish** s’affiche.

3. Cliquez avec le bouton droit sur l’entrée de l’extension et cliquez sur **supprimer**. Vous êtes invité à confirmer si vous souhaitez supprimer l’extension. Cliquez sur **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension de votre ordinateur

1. Dans Visual Studio, dans le menu **Outils** , cliquez sur **extensions et mises à jour**.

2. Sélectionnez **TestPublish** , puis cliquez sur **désinstaller**. La désinstallation de l’extension est alors planifiée.

3. Pour terminer la désinstallation, fermez toutes les instances de Visual Studio.
