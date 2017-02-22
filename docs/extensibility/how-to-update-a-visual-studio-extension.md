---
title: "Comment&#160;: mettre &#224; jour une Extension Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "package de mise à jour"
  - "extension de la mise à jour"
  - "nouvelle version du package"
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: mettre &#224; jour une Extension Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez mettre à jour une extension Visual Studio sur votre système à l’aide de **Extensions et mises à jour** pour installer la version mise à jour. Si vous créez une version mise à jour d’une extension, vous pouvez l’indiquer comme mis à jour en incrémentant le numéro de version dans le manifeste VSIX.  
  
 Mises à jour sont installées lorsque le manifeste VSIX de l’extension entrante a le même `ID` que celle installée et un degré plus élevé `Version` nombre. Si le `Version` numéro est identique ou inférieur, le package ne peut pas être installé. Si le `ID` valeurs ne correspondent pas, le package n’est pas encore installé est reconnu comme une extension distincte.  
  
 Pour éviter les conflits pendant le développement, nous vous recommandons de désinstaller les versions antérieures d’extensions en cours et également désinstaller ou désactiver toutes les extensions pouvant être en conflit.  
  
### Pour mettre à jour une extension sur votre système  
  
1.  Dans le menu **Outils**, choisissez **Extensions et mises à jour**.  
  
2.  Dans le volet gauche, cliquez sur **mises à jour**.  
  
3.  Dans le volet central, cliquez sur la mise à jour à installer.  
  
     Le numéro de version de l’extension de mise à jour s’affiche dans le volet droit, ainsi que d’autres informations.  
  
4.  En bas du volet droit, cliquez sur **mise à jour**.  
  
### Pour publier une mise à jour d’une extension  
  
1.  Dans Visual Studio, ouvrez la solution pour l’extension que vous souhaitez mettre à jour. Apportez les modifications.  
  
    > [!IMPORTANT]
    >  Non signé que toutes les extensions utilisateur ne pas mis à jour automatiquement. Vous devez toujours signer vos extensions.  
  
2.  Dans **l’Explorateur de solutions**, ouvrez source.extension.manifest.  
  
3.  Dans le Concepteur de manifestes, augmentez la valeur du nombre dans le **Version** champ.  
  
4.  Enregistrez la solution et générez\-le.  
  
5.  Télécharger le nouveau fichier .vsix \(dans le dossier \\bin\\Debug\\ du projet\) dans le [la galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site Web.  
  
     Lorsqu’un utilisateur qui possède une version antérieure de l’extension ouvre **Extensions et mises à jour**, la nouvelle version s’affiche dans le **mises à jour** liste, sous réserve que l’outil est configuré pour rechercher automatiquement les mises à jour.  
  
     Vous pouvez activer ou désactiver la vérification automatique des mises à jour en bas de la **mises à jour** volet \(**Activer\/désactiver la détection automatique des mises à jour disponibles**\), les modifications du **des mises à jour** dans **Outils \/ Options \/ environnement \/ Extensions et mises à jour**.  
  
    > [!NOTE]
    >  À partir de Visual Studio 2015 Update 2, vous pouvez spécifier \(dans **Outils \/ Options \/ environnement \/ Extensions et mises à jour**\) que vous souhaitez les mises à jour automatiques pour les extensions par utilisateur, toutes les extensions de l’utilisateur ou les deux \(le paramètre par défaut\).  
  
## Voir aussi  
 [Anatomie d'un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)