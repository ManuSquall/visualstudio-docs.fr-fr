---
title: "Procédure pas à pas : Publication d’une Extension Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 574af4ff2b3858201c13121475de02a763572f6b
ms.openlocfilehash: fcfb0724b89d60553d6686a0705ab1e9459014ce
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Procédure pas à pas : Publication d’une Extension Visual Studio
Cette procédure pas à pas vous montre comment publier une extension Visual Studio dans la galerie Visual Studio. Lorsque vous ajoutez votre extension vers la galerie, les développeurs peuvent utiliser **Extensions et mises à jour** pour y rechercher des extensions nouvelles et mises à jour.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-a-visual-studio-extension"></a>Créez une Extension Visual Studio  
 Dans ce cas, nous utiliserons une VSPackage l’extension par défaut, mais les mêmes étapes sont valides pour chaque type d’extension.  
  
1.  Créez un VSPackage dans Visual c# nommé `TestPublishing` ayant une commande de menu. Pour plus d’informations, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="test-the-extension"></a>Tester l’Extension  
 Avant de distribuer l’extension, générer et tester pour vous assurer qu’il est correctement installé dans l’instance expérimentale de Visual Studio.  
  
1.  Dans Visual Studio, démarrez le débogage. Pour ouvrir une instance expérimentale de Visual Studio.  
  
2.  Dans l’instance expérimentale, accédez à la **outils** menu et cliquez sur **le Gestionnaire d’extensions**. L’extension TestPublishing doit apparaître dans le volet central et être activée.  
  
3.  Sur le **outils** menu, vérifiez que la commande de test.  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publier l’Extension sur la galerie Visual Studio  
 Maintenant, vous pouvez publier l’extension sur la galerie Visual Studio.  
  
1.  Assurez-vous que vous avez créé la version Release de votre extension, et qu’il est à jour.  
  
2.  Dans un navigateur web, ouvrez le site web de la [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) .  
  
3.  Dans le coin supérieur droit, cliquez sur **SIGN IN**.  
  
4.  Utilisez votre compte Microsoft pour vous connecter. Si vous n’avez pas de compte Microsoft, vous pouvez en créer un à ce stade.  
  
5.  Cliquez sur **Upload**.  
  
6.  Dans **étape 1 : Type d’Extension**, sélectionnez **outil** , puis **suivant**.  
  
7.  Dans **étape 2 : télécharger**, vous pouvez choisir de télécharger directement vers la galerie Visual Studio ou simplement ajouter un lien vers votre site Web. Dans ce cas sélectionner **je voudrais télécharger mon outil**. Le **Sélectionnez votre contrôle** boîte s’affiche. Cliquez sur **Parcourir** , puis sélectionnez TestPublish.vsix dans le dossier \bin\Release du projet. Cliquez sur **Next**.  
  
8.  Dans **étape 3 : informations de base**, les champs du fichier source.extension.vsixmanifest sont affichées. Sélectionnez un **catégorie** et ajoutez **balises** pour aider les utilisateurs à trouver votre extension. Voulez-vous ajouter une synthèse plus détaillée et une description (la description doit comporter au moins 280 caractères). Laissez **Type d’Extension** en tant que **pas une Extension Microsoft** et **la catégorie de coûts** en tant que **version d’évaluation**.  
  
9. Lisez l’accord de Contribution au bas de la page **J’accepte**.  
  
10. Cliquez sur **créer une Contribution**. Cela affiche la page que votre extension aura sur la galerie Visual Studio, avec un message que la page n’a pas encore été publiée.  
  
11. Cliquez sur **Publier**.  
  
12. Rechercher la galerie Visual Studio pour votre extension. La liste pour l’extension TestPublish doit-elle apparaître.  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Installer l’Extension à partir de la galerie Visual Studio  
 Maintenant que l’extension est publiée, l’installer dans Visual Studio et test.  
  
1.  Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.  
  
2.  Cliquez sur **Online** , puis recherchez TestPublish. La liste pour l’extension TestPublish doit-elle apparaître.  
  
3.  Cliquez sur **Télécharger**. Une fois l’extension téléchargée, cliquez sur **Installer**.  
  
4.  Pour terminer l’installation, redémarrez Visual Studio.  
  
## <a name="removing-the-extension"></a>Suppression de l’Extension  
 Vous pouvez supprimer l’extension à partir de la galerie Visual Studio et à partir de votre ordinateur.  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Pour supprimer l’extension à partir de la galerie Visual Studio  
  
1.  Ouvrez la [la galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) site Web.  
  
2.  Dans le centre, cliquez sur **mes Extensions**. La liste de TestPublish s’affiche.  
  
3.  Cliquez sur **supprimer**.  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension de votre ordinateur  
  
1.  Dans Visual Studio, dans le menu **Outils** , cliquez sur **Gestionnaire d’extensions**.  
  
2.  Sélectionnez TestPublish **désinstallation**.  
  
3.  Pour terminer la désinstallation, redémarrez Visual Studio.

