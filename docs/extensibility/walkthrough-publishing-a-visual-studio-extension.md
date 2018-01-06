---
title: "Procédure pas à pas : Publication d’une Extension Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9b2823c15309e63262052fd3cc95d914bf1614c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Procédure pas à pas : Publication d’une Extension Visual Studio

Cette procédure pas à pas montre comment publier une extension Visual Studio pour Visual Studio Marketplace. Lorsque vous ajoutez votre extension pour le marché, les développeurs peuvent utiliser **Extensions et mises à jour** pour y rechercher des extensions nouvelles et mises à jour.

## <a name="prerequisites"></a>Prérequis

 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Créez une Extension Visual Studio

Dans ce cas, nous allons utiliser une extension de VSPackage par défaut, mais les mêmes étapes sont valides pour chaque type d’extension.

1. Créer un VSPackage en c# nommé « TestPublish » qui dispose d’une commande de menu. Pour plus d’informations, consultez [création de votre première Extension : Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Empaqueter votre Extension

1. Mettre à jour l’extension vsixmanifest avec les informations correctes sur le nom de produit, auteur et la version.

  ![mise à jour extension vsixmanifest](media/update-extension-vsixmanifest.png)

2. Générer votre extension **version** mode. Maintenant, votre extension est empaquetée en tant qu’une extension VSIX dans le dossier \bin\Release.

3. Vous pouvez double-cliquer sur l’extension VSIX pour vérifier l’installation.

## <a name="test-the-extension"></a>Tester l’Extension

 Avant de distribuer l’extension, générer et tester pour vous assurer qu’il est correctement installé dans l’instance expérimentale de Visual Studio.

1. Dans Visual Studio, démarrez le débogage. Pour ouvrir une instance expérimentale de Visual Studio.

2. Dans l’instance expérimentale, accédez à la **outils** menu et cliquez sur **Extensions et mises à jour...** . L’extension TestPublish doit apparaître dans le volet central et être activée.

3. Sur le **outils** menu, vérifiez que la commande de test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publier l’Extension de Visual Studio Marketplace

1. Assurez-vous que vous avez créé la version Release de votre extension, et qu’il est à jour.

2. Dans un navigateur web, ouvrez le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) site Web.

3. Dans le coin supérieur droit, cliquez sur **connectez-vous**.

4. Utilisez votre compte Microsoft pour vous connecter. Si vous n’avez pas d’un compte Microsoft, vous pouvez en créer un à ce stade.

5. Cliquez sur **publier des extensions**.  Cela vous permet d’accéder à la page de gestion pour toutes les extensions de votre.  Si vous n’avez pas un compte de serveur de publication, vous devrez créer un pour l’instant.

  ![Télécharger sur le Marketplace](media/upload-to-marketplace.png)

6. Choisissez le serveur de publication que vous souhaitez utiliser pour télécharger votre extension.  Vous pouvez modifier les serveurs de publication en cliquant sur le nom du serveur de publication dans le coin supérieur gauche.

  ![Publication des changements Marketplace](media/change-marketplace-publisher.png)

7. Dans **1 : télécharger l’extension**, vous pouvez choisir de télécharger un fichier VSIX directement à Visual Studio Marketplace ou simplement ajouter un lien vers votre site Web. Dans ce cas, nous télécharger notre extension, TestPublish.vsix.  Faites glisser et déposez votre extension ou utilisez le **cliquez sur** lien pour rechercher le fichier.  Vous trouverez votre extension dans le dossier \bin\Release du projet.  Cliquez sur **Continuer**.

8. Dans **2 : fournir des détails de l’extension**, certains champs sont remplis automatiquement à partir du fichier source.extension.vsixmanifest à partir de votre extension.  Vous trouverez plus d’informations sur chacune d’elles ci-dessous :

    * **Nom interne** sera utilisé dans l’URL de la page des détails de l’extension. Pour obtenir un exemple, une extension sous le nom du serveur de publication « myname » de la publication et en spécifiant le nom interne pour être « myextension » entraîne une URL de « marketplace.visualstudio\.com/items?itemName=myname.myextension » pour votre extension page de détails.
    
    * **Nom d’affichage** de votre extension.  Cela est remplie automatiquement à partir du fichier source.extension.vsixmanifest.
   
    * **Version** numéro de l’extension que vous téléchargez.  Cela est remplie automatiquement à partir du fichier source.extension.vsixmanifest.
    
    * **ID VSIX** est l’identificateur unique que Visual Studio utilise pour votre extension.  Cela est nécessaire si vous souhaitez que votre extension pour une mise à jour automatique.  Cela est remplie automatiquement à partir du fichier source.extension.vsixmanifest.
    
    * **Logo** qui sera utilisé pour votre extension.  Il s’agit et rempli automatiquement à partir du fichier source.extension.vsixmanifest si fourni.
    
    * **Brève description** de ce que fait votre extension.  Il s’agit et rempli automatiquement à partir du fichier source.extension.vsixmanifest.
    
    * **Vue d’ensemble** est un bon emplacement pour inclure des captures d’écran et des informations détaillées sur ce que fait votre extension.
    
    * **Prise en charge des versions de Visual Studio** vous permet de choisir les versions de Visual Studio, votre extension fonctionne sur.  Votre extension sera installée uniquement pour ces versions.
    
    * **Prise en charge des éditions de Visual Studio** vous permet de choisir les éditions de Visual Studio, votre extension fonctionne sur.  Votre extension sera installée uniquement pour ces éditions.
    
    * **Type**.  Le type le plus courant des extensions sont **outils**.
    
    * **Catégories**.  Sélectionner jusqu'à trois qui sont le mieux pour votre extension.
    
    * **Balises** sont les mots clés qui permettent aux utilisateurs de trouver votre extension. Les balises peuvent aider à augmenter la pertinence de la recherche de vos extensions dans le Marketplace.
    
    * **Catégorie de tarification** est le coût de votre extension.
    
    * **Référentiel de code source** vous permet de partager un lien vers votre code source avec la Communauté.
    
    * **Autoriser Q & r pour votre extension** permettra aux utilisateurs de laisser des questions sur la page d’entrée de votre extension.

9. Cliquez sur **enregistrer et charger**. Vous accéderez page Gérer le retour à votre serveur de publication.  Votre extension n’a pas encore été publiée.  Pour publier votre hover extension sur l’entrée de votre extension, puis cliquez sur **...**  , puis **rendre publique**.  Vous pouvez afficher la façon dont votre extension ressemblera sur Marketplace en sélectionnant **afficher les détails**.  Pour les numéros d’acquisition, cliquez sur **rapports**.  Pour apporter des modifications à votre extension, cliquez sur **modifier*.

  ![Menu de l’entrée extension](media/extension-entry-menu.png)

10. Après avoir cliqué sur **rendre Public**, votre extension est désormais publique.  Rechercher le Visual Studio Marketplace pour votre extension.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installer l’Extension à partir de Visual Studio Marketplace

Maintenant que l’extension est publiée, installez-le dans Visual Studio et testez-le.

1. Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour...** .

2. Cliquez sur **Online** , puis recherchez TestPublish.

3. Cliquez sur **Télécharger**. L’extension sera ensuite être planifiée pour l’installation.

4. Pour terminer l’installation, fermez toutes les instances de Visual Studio.

## <a name="removing-the-extension"></a>Suppression de l’Extension

Vous pouvez supprimer l’extension à partir de Visual Studio Marketplace et de votre ordinateur.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Pour supprimer l’extension de Visual Studio Marketplace

1. Ouvrez le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) site Web.

2. Dans le coin supérieur droit, cliquez sur **publier** extensions.  Choisissez le serveur de publication que vous avez utilisé pour publier TestPublish.  La liste de TestPublish s’affiche.

3. Pointez sur l’entrée d’extension et cliquez sur **...**  et **supprimer...** Vous devrez confirmer si vous souhaitez supprimer l’extension.  Cliquez sur **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension à partir de votre ordinateur.

1. Dans Visual Studio, sur le **outils** menu, cliquez sur **Extension et les mises à jour...** .

2. Sélectionnez TestPublish, puis cliquez **désinstallation**. L’extension sera ensuite être planifiée pour la désinstallation.

3. Pour terminer la désinstallation, fermez toutes les instances de Visual Studio.
