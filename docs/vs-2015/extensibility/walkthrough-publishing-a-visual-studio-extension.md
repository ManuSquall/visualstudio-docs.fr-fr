---
title: Publier une extension | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201967"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Procédure pas à pas : publication d’une extension Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Remarque**: la Galerie Visual Studio est remplacée par le Visual Studio Marketplace. Pour plus d’informations, consultez la version la plus récente de cette rubrique.

Cette procédure pas à pas vous montre comment publier une extension Visual Studio dans la Galerie Visual Studio. Lorsque vous ajoutez votre extension à la Galerie, les développeurs peuvent utiliser des **extensions et des mises à jour** pour y rechercher des extensions nouvelles et mises à jour.

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Créer une extension Visual Studio
 Dans ce cas, nous utiliserons une extension VSPackage par défaut, mais les mêmes étapes sont valides pour chaque type d’extension.

1. Créez un VSPackage en C# nommé `TestPublishing` qui comporte une commande de menu. Pour plus d’informations, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Tester l’extension
 Avant de distribuer l’extension, générez et testez-la pour vous assurer qu’elle est installée correctement dans l’instance expérimentale de Visual Studio.

1. Dans Visual Studio, démarrez le débogage. pour ouvrir une instance expérimentale de Visual Studio.

2. Dans l’instance expérimentale, accédez au menu **Outils** , puis cliquez sur **Gestionnaire d’extensions**. L’extension TestPublishing doit apparaître dans le volet central et être activée.

3. Dans le menu **Outils** , vérifiez que vous voyez la commande test.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publier l’extension dans la Galerie Visual Studio
 Vous pouvez maintenant publier l’extension dans la Galerie Visual Studio.

1. Assurez-vous que vous avez créé la version Release de votre extension et qu’elle est à jour.

2. Dans un navigateur Web, ouvrez le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

3. Dans l’angle supérieur droit, cliquez sur **se connecter**.

4. Utilisez votre compte Microsoft pour vous connecter. Si vous n’avez pas de compte Microsoft, vous pouvez en créer un à ce stade.

5. Cliquez sur **Télécharger**.

6. Dans **étape 1 : type d’extension**, sélectionnez **outil** , puis cliquez sur **suivant**.

7. À l' **étape 2 : Télécharger**, vous pouvez choisir de télécharger directement vers la Galerie Visual Studio ou simplement ajouter un lien vers votre propre site Web. Dans ce cas, sélectionnez **je souhaite télécharger mon outil**. La zone **sélectionner votre contrôle** s’affiche. Cliquez sur **Parcourir** , puis sélectionnez TestPublish. VSIX dans le dossier \bin\release du projet. Cliquez sur **Suivant**.

8. Dans **Step 3 : Basic information**, les champs du fichier source. extension. vsixmanifest s’affichent. Sélectionnez une **catégorie** appropriée et ajoutez des **balises** pour aider les utilisateurs à trouver votre extension. Vous pouvez ajouter un résumé et une description plus détaillés (la description doit comporter au moins 280 caractères). Laissez **le type d’extension** n’est **pas une extension Microsoft et une** catégorie de **coût** comme **version d’évaluation**.

9. Lisez l’accord de contribution situé en bas de la page et cochez la case **J’accepte**.

10. Cliquez sur **créer une contribution**. Cela affiche la page que votre extension aura sur la Galerie Visual Studio, avec un message indiquant que la page n’a pas encore été publiée.

11. Cliquez sur **Publier**.

12. Recherchez votre extension dans la Galerie Visual Studio. La liste de l’extension TestPublish doit s’afficher.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Installer l’extension à partir de la Galerie Visual Studio
 Maintenant que l’extension est publiée, installez-la dans Visual Studio et testez-la ici.

1. Dans Visual Studio, dans le menu **Outils** , cliquez sur **extensions et mises à jour**.

2. Cliquez sur **en ligne** , puis recherchez TestPublish. La liste de l’extension TestPublish doit s’afficher.

3. Cliquez sur **Télécharger**. Une fois l’extension téléchargée, cliquez sur **Installer**.

4. Pour terminer l’installation, redémarrez Visual Studio.

## <a name="removing-the-extension"></a>Suppression de l’extension
 Vous pouvez supprimer l’extension de la Galerie Visual Studio et de votre ordinateur.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Pour supprimer l’extension de la Galerie Visual Studio

1. Ouvrez le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

2. Dans l’angle supérieur droit, cliquez sur **My Extenions**. La liste de TestPublish s’affiche.

3. Cliquez sur **Supprimer**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension de votre ordinateur

1. Dans Visual Studio, dans le menu **Outils** , cliquez sur **Gestionnaire d’extensions**.

2. Sélectionnez TestPublish, puis cliquez sur **désinstaller**.

3. Pour terminer la désinstallation, redémarrez Visual Studio.
