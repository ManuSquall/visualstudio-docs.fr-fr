---
title: "Comment : mettre à jour une Extension Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 098d8ca0d779b7a7877c47125017dd2cd6880445
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-update-a-visual-studio-extension"></a>Comment : mettre à jour une Extension Visual Studio
Vous pouvez mettre à jour une extension Visual Studio sur votre système à l’aide de **Extensions et mises à jour** pour installer la version mise à jour. Si vous créez une version mise à jour d’une extension, vous pouvez indiquer qu’elle a mis à jour en incrémentant le numéro de version dans le manifeste VSIX.  
  
 Mises à jour sont installées lorsque le manifeste VSIX de l’extension entrante a la même `ID` en tant que celle installée et un degré plus élevé `Version` nombre. Si le `Version` numéro est identique ou inférieur, le package ne peut pas être installé. Si le `ID` valeurs ne correspondent pas, le package n’est pas encore installé est reconnu comme une extension distincte.  
  
 Pour vous aider à éviter les conflits pendant le développement, nous vous recommandons de désinstaller les versions antérieures d’extensions en cours d’exécution et également désinstaller ou désactiver toutes les extensions potentiellement en conflit.  
  
### <a name="to-update-an-extension-on-your-system"></a>Pour mettre à jour une extension sur votre système.  
  
1.  Dans le menu **Outils** , choisissez **Extensions et mises à jour**.  
  
2.  Dans le volet gauche, cliquez sur **mises à jour**.  
  
3.  Dans le volet central, cliquez sur la mise à jour que vous souhaitez installer.  
  
     Le numéro de version de l’extension de mise à jour s’affiche dans le volet droit, ainsi que d’autres informations.  
  
4.  Au bas du volet droit, cliquez sur **mise à jour**.  
  
### <a name="to-publish-an-update-of-an-extension"></a>Pour publier une mise à jour d’une extension  
  
1.  Dans Visual Studio, ouvrez la solution pour l’extension que vous souhaitez mettre à jour. Apportez les modifications.  
  
    > [!IMPORTANT]
    >  Non signé que toutes les extensions de l’utilisateur plus mis à jour automatiquement. Vous devez toujours signer vos extensions.  
  
2.  Dans **l’Explorateur de solutions**, ouvrez source.extension.manifest.  
  
3.  Dans le Concepteur de manifestes, augmentez la valeur du nombre figurant dans le **Version** champ.  
  
4.  Enregistrez la solution et générez-le.  
  
5.  Télécharger le nouveau fichier .vsix (dans le dossier \bin\Debug\ du projet) dans le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) site Web.  
  
     Lorsqu’un utilisateur disposant d’une version antérieure de l’extension ouvre **Extensions et mises à jour**, la nouvelle version s’affiche dans le **mises à jour** répertorier, sous réserve que l’outil est configuré pour rechercher automatiquement les mises à jour.  
  
     Vous pouvez activer ou désactiver la vérification automatique des mises à jour en bas de la **mises à jour** volet (**activer/désactiver la détection automatique des mises à jour disponibles**), les modifications qui le **recherchez les mises à jour** définissant dans **Outils / Options / environnement / Extensions et mises à jour**.  
  
    > [!NOTE]
    >  À partir de Visual Studio 2015 Update 2, vous pouvez spécifier (dans **Outils / Options / Environnement / Extensions et mises à jour**) si vous souhaitez des mises à jour automatiques pour les extensions par utilisateur, pour toutes les extensions utilisateur ou pour les deux (le paramètre par défaut).  
  
## <a name="see-also"></a>Voir aussi  
 [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
