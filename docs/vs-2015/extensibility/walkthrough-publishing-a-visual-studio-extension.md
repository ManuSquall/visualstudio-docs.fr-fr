---
title: 'Procédure pas à pas : Publication d’une Extension de Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66f6c6e4f59f271999294991dc66f71f16cf4a2f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495391"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Procédure pas à pas : publication d’une extension Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Remarque**: la galerie Visual Studio est remplacée par la place de marché Visual Studio. Consultez la dernière version de cette rubrique pour plus d’informations.

Vous trouverez la dernière version de cette rubrique dans [procédure pas à pas : publication d’une Extension Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-publishing-a-visual-studio-extension).  
  
Cette procédure pas à pas vous montre comment publier une extension Visual Studio sur la galerie Visual Studio. Lorsque vous ajoutez votre extension dans la galerie, les développeurs peuvent utiliser **Extensions et mises à jour** pour y rechercher des extensions nouvelles et mises à jour.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-a-visual-studio-extension"></a>Créer une Extension Visual Studio  
 Dans ce cas, nous allons utiliser une extension de package Visual Studio par défaut, mais les mêmes étapes sont valides pour chaque type d’extension.  
  
1.  Créer un VSPackage en c# nommé `TestPublishing` qui a une commande de menu. Pour plus d’informations, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="test-the-extension"></a>Tester l’Extension  
 Avant de distribuer l’extension, générer et tester pour vous assurer qu’il est installé correctement dans l’instance expérimentale de Visual Studio.  
  
1.  Dans Visual Studio, démarrez le débogage. Pour ouvrir une instance expérimentale de Visual Studio.  
  
2.  Dans l’instance expérimentale, accédez à la **outils** menu et cliquez sur **Gestionnaire d’extensions**. L’extension TestPublishing doit apparaître dans le volet central et être activée.  
  
3.  Sur le **outils** menu, vérifiez que vous voyez la commande de test.  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publier l’Extension à la galerie Visual Studio  
 Vous pouvez maintenant publier l’extension à la galerie Visual Studio.  
  
1.  Assurez-vous que vous avez créé la version Release de votre extension et qu’il est à jour.  
  
2.  Dans un navigateur web, ouvrez le site web de la [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) .  
  
3.  Dans le coin supérieur droit, cliquez sur **SIGN IN**.  
  
4.  Utilisez votre compte Microsoft pour vous connecter. Si vous n’avez pas d’un compte Microsoft, vous pouvez en créer une à ce stade.  
  
5.  Cliquez sur **Upload**.  
  
6.  Dans **étape 1 : Type d’Extension**, sélectionnez **outil** puis cliquez sur **suivant**.  
  
7.  Dans **étape 2 : télécharger**, vous pouvez choisir de charger directement dans la galerie Visual Studio ou simplement ajouter un lien vers votre propre site Web. Dans ce cas sélectionner **je voudrais télécharger mon outil**. Le **Sélectionnez votre contrôle** boîte s’affiche. Cliquez sur **Parcourir** puis TestPublish.vsix dans le dossier \bin\Release du projet. Cliquez sur **Suivant**.  
  
8.  Dans **étape 3 : informations de base**, les champs à partir du fichier source.extension.vsixmanifest sont affichées. Sélectionnez un **catégorie** et ajoutez **balises** pour aider les utilisateurs à trouver votre extension. Voulez-vous ajouter un résumé et une description (la description doit être au moins de 280 caractères) plus détaillée. Laissez **Type d’Extension** comme **pas une Extension Microsoft** et **catégorie de coûts** comme **essai**.  
  
9. Lisez le contrat de Contribution au bas de la page et vérifiez **J’accepte**.  
  
10. Cliquez sur **créer Contribution**. Cela affiche la page de que votre extension aura sur la galerie Visual Studio, avec un message que la page n’a pas encore été publiée.  
  
11. Cliquez sur **Publier**.  
  
12. Rechercher la galerie Visual Studio pour votre extension. La liste pour l’extension TestPublish doit apparaître.  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Installer l’Extension à partir de la galerie Visual Studio  
 Maintenant que l’extension est publiée, installez-le dans Visual Studio et testez-le.  
  
1.  Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.  
  
2.  Cliquez sur **Online** , puis recherchez TestPublish. La liste pour l’extension TestPublish doit apparaître.  
  
3.  Cliquez sur **Télécharger**. Une fois l’extension téléchargée, cliquez sur **Installer**.  
  
4.  Pour terminer l’installation, redémarrez Visual Studio.  
  
## <a name="removing-the-extension"></a>Suppression de l’Extension  
 Vous pouvez supprimer l’extension à partir de la galerie Visual Studio et à partir de votre ordinateur.  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Pour supprimer l’extension à partir de la galerie Visual Studio  
  
1.  Ouvrez le [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) site Web.  
  
2.  Dans le coin supérieur droit, cliquez sur **Extenions Mes**. La liste de TestPublish s’affiche.  
  
3.  Cliquez sur **Delete**.  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension à partir de votre ordinateur  
  
1.  Dans Visual Studio, dans le menu **Outils** , cliquez sur **Gestionnaire d’extensions**.  
  
2.  Sélectionnez TestPublish, puis cliquez **désinstallation**.  
  
3.  Pour terminer la désinstallation, redémarrez Visual Studio.

