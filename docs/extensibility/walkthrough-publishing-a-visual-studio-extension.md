---
title: 'Procédure pas à pas : Publication d’une Extension de Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae0b9d48e2a2292229b40e3aaf2a1c755e4c844e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815739"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Procédure pas à pas : Publier une extension Visual Studio

Cette procédure pas à pas vous montre comment publier une extension Visual Studio sur la place de marché Visual Studio. Lorsque vous ajoutez votre extension à la place de marché, les développeurs peuvent utiliser **Extensions et mises à jour** pour rechercher des extensions nouvelles et mises à jour.

## <a name="prerequisites"></a>Prérequis

 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Créer une extension Visual Studio

Cet article utilise une extension de package Visual Studio par défaut, mais les étapes sont valides pour chaque type d’extension.

1. Créer un VSPackage en c# nommé `TestPublish` qui a une commande de menu. Pour plus d’informations, consultez [créer votre première extension : Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Votre extension de package

1. Mettre à jour de l’extension *.vsixmanifest* avec les informations correctes sur le nom de produit, auteur et la version.

   ![mettre à jour d’extension vsixmanifest](media/update-extension-vsixmanifest.png)

2. Générer votre extension **version** mode. Votre extension est maintenant fournie comme une extension VSIX dans le dossier \bin\Release.

3. Vous pouvez double-cliquer sur l’extension VSIX pour vérifier l’installation.

## <a name="test-the-extension"></a>Tester l’extension

 Avant de distribuer l’extension, générer et tester pour vous assurer qu’il est installé correctement dans l’instance expérimentale de Visual Studio.

1. Dans Visual Studio, démarrez le débogage pour ouvrir une instance expérimentale de Visual Studio.

2. Dans l’instance expérimentale, accédez à la **outils** menu et cliquez sur **Extensions et mises à jour**. L’extension TestPublish doit apparaître dans le volet central et être activée.

3. Sur le **outils** menu, vérifiez que vous voyez la commande de test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publier l’extension à la place de marché Visual Studio

1. Assurez-vous que vous avez créé la version Release de votre extension et qu’il est à jour.

2. Dans un navigateur web, ouvrez le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) site Web.

3. Dans le coin supérieur droit, cliquez sur **connectez-vous**.

4. Utilisez votre compte Microsoft pour vous connecter. Si vous n’avez pas d’un compte Microsoft, vous pouvez en créer une à ce stade.

5. Cliquez sur **publier des extensions**.  Cette option vous permet d’accéder à la page de gestion pour toutes vos extensions. Si vous n’avez pas un compte d’éditeur, vous êtes invité à en créer un pour l’instant.

   ![Charger à la place de marché](media/upload-to-marketplace.png)

6. Choisissez le serveur de publication que vous souhaitez utiliser pour télécharger votre extension. Vous pouvez modifier les serveurs de publication en cliquant sur les noms d’éditeurs apparaissent à gauche. Cliquez sur **nouvelle extension** et sélectionnez **Visual Studio**.

7. Dans **1 : charger l’extension**, vous pouvez choisir de télécharger un fichier VSIX directement à la place de marché Visual Studio ou simplement ajouter un lien vers votre propre site Web. Dans cet exemple, l’extension, *TestPublish.vsix* est chargé. Faites glisser et déposez votre extension ou utilisez le **cliquez sur** lien pour rechercher le fichier. Recherchez votre extension dans le dossier \bin\Release du projet.  Cliquez sur **Continuer**.

8. Dans **2 : fournir les détails de l’extension**, certains champs sont remplis automatiquement à partir de la *source.extension.vsixmanifest* fichier à partir de votre extension. Rechercher plus en détail chacun ci-dessous :

    * **Nom interne** est utilisé dans l’URL de page de détails de l’extension. Pour obtenir un exemple, la publication d’une extension sous le nom du serveur de publication « myname » et en spécifiant le nom interne pour être « mon extension » entraîne une URL de « marketplace.visualstudio\.com/items?itemName=myname.myextension » pour les détails de votre extension page.
    
    * **Nom d’affichage** de votre extension. Ce nom est rempli automatiquement à partir de la *source.extension.vsixmanifest* fichier.
   
    * **Version** numéro de l’extension que vous chargez. Cette version est rempli automatiquement à partir de la *source.extension.vsixmanifest* fichier.
    
    * **ID VSIX** est l’identificateur unique utilisé par Visual Studio pour votre extension. Cet identificateur est requis si vous souhaitez que pour que votre extension à jour automatiquement. Cet identificateur est rempli automatiquement à partir de la *source.extension.vsixmanifest* fichier.
    
   * **Logo** qui est utilisé pour votre extension. Ce logo est rempli automatiquement à partir de la *source.extension.vsixmanifest* fichier s’il est fourni.
    
     * **Description courte** de ce que fait votre extension. Cette description est rempli automatiquement à partir de la *source.extension.vsixmanifest* fichier.
    
     * **Vue d’ensemble** est un bon emplacement pour inclure des captures d’écran et des informations détaillées sur ce que fait votre extension.
    
     * **Prise en charge des versions de Visual Studio** vous permet de choisir les versions de Visual Studio fonctionne sur votre extension. Votre extension est installée uniquement pour ces versions.
    
     * ** Pris en charge de Visual Studio Édition vous permet de choisir quelles éditions de Visual Studio fonctionne sur votre extension. Votre extension est installée uniquement pour ces éditions.
    
     * **Type**. Le type le plus courant des extensions sont **outils**.
    
     * **Catégories**. Sélectionnez jusqu'à trois qui sont le mieux pour votre extension.
    
     * **Balises** sont les mots clés qui permettent aux utilisateurs de trouver votre extension. Balises peuvent aider à augmenter la pertinence de la recherche de vos extensions dans la place de marché.
    
     * **Catégorie de tarification** est le coût de votre extension.
    
     * **Référentiel de code source** vous permet de partager un lien vers votre code source avec la Communauté.
    
     * **Autoriser des questions et réponses pour votre extension** permet aux utilisateurs de laisser des questions sur votre page d’entrée extension.

9. Cliquez sur **enregistrer et charger**. Page de gestion de cette option vous revenez à votre serveur de publication. Votre extension n’a pas encore été publiée. Pour publier votre extension, cliquez sur votre extension, puis sélectionnez **rendre Public**. Vous pouvez afficher la façon dont votre extension ressemblera sur place de marché en sélectionnant **afficher l’Extension**. Pour les nombres d’acquisition, cliquez sur **rapports**. Pour apporter des modifications à votre extension, cliquez sur **modifier**.

   ![Menu de l’entrée extension](media/extension-entry-menu.png)

10. Après avoir cliqué sur **rendre Public**, votre extension est désormais publique. Rechercher la place de marché Visual Studio pour votre extension.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Ajouter des utilisateurs supplémentaires pour gérer votre compte de serveur de publication

Place de marché prend en charge l’octroi d’autorisations des utilisateurs supplémentaires pour accéder et gérer un compte d’éditeur.

1. Accédez au compte de publication que vous souhaitez ajouter des utilisateurs.

2. Sélectionnez **membres** , puis cliquez sur **ajouter**.

   ![Ajouter des utilisateurs supplémentaires](media/add-users.png)

3. Vous pouvez ensuite spécifier l’adresse de messagerie de l’utilisateur que vous souhaitez ajouter et accorder le niveau d’accès sous **sélectionner un rôle**.  Vous pouvez choisir parmi les options suivantes :

   * **Créateur**: l’utilisateur peut publier des extensions, mais ne peut pas afficher ou gérer les extensions publiées par d’autres utilisateurs.
  
   * **Lecteur**: l’utilisateur peut afficher les extensions, mais ne peut pas publier ou gérer les extensions.
  
   * **Contributeur**: l’utilisateur peut publier et gérer des extensions, mais ne peut pas modifier les paramètres de l’éditeur ou gérer l’accès.
  
   * **Propriétaire**: l’utilisateur peut publier et gérer les extensions, modifier les paramètres de l’éditeur et gérer l’accès.
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installer l’extension à partir de Visual Studio Marketplace

Maintenant que l’extension est publiée, installez-le dans Visual Studio et testez-le.

1. Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.

2. Cliquez sur **Online** , puis recherchez **TestPublish**.

3. Cliquez sur **Télécharger**. L’extension est ensuite planifiée pour l’installation.

4. Pour terminer l’installation, fermez toutes les instances de Visual Studio.

## <a name="remove-the-extension"></a>Supprimer l’extension

Vous pouvez supprimer l’extension à partir de Visual Studio Marketplace et à partir de votre ordinateur.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Pour supprimer l’extension à partir de Visual Studio Marketplace

1. Ouvrez le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) site Web.

2. Dans le coin supérieur droit, cliquez sur **publier** extensions. Choisissez le serveur de publication que vous avez utilisé pour publier **TestPublish**. La liste de **TestPublish** s’affiche.

3. Avec le bouton droit sur l’entrée de l’extension et cliquez sur **supprimer**. Vous êtes invité à confirmer si vous souhaitez supprimer l’extension. Cliquez sur **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension à partir de votre ordinateur

1. Dans Visual Studio, sur le **outils** menu, cliquez sur **Extension et mises à jour**.

2. Sélectionnez **TestPublish** puis cliquez sur **désinstallation**. L’extension est ensuite planifiée pour la désinstallation.

3. Pour terminer la désinstallation, fermez toutes les instances de Visual Studio.
