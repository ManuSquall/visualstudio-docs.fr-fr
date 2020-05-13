---
title: 'Comment : Mettre à jour une extension de studio visuel (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710655"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Comment: Mettre à jour une extension Visual Studio
Vous pouvez mettre à jour une extension Visual Studio sur votre système en utilisant **Extensions et Mises** à jour pour installer la version mise à jour. Si vous créez une version mise à jour d’une extension, vous pouvez la signifier mise à jour en incrémentant le numéro de version dans le manifeste VSIX.

 Des mises à jour sont installées lorsque `ID` le manifeste VSIX `Version` de l’extension entrante a le même nombre que celui installé et un nombre plus élevé. Si `Version` le nombre est le même ou inférieur, le paquet ne peut pas être installé. Si `ID` les valeurs ne correspondent pas, le paquet qui n’est pas encore installé est reconnu comme une extension distincte.

 Pour aider à prévenir les conflits pendant le développement, nous vous recommandons de désinstaller les versions antérieures des extensions en cours, et aussi désinstaller ou désactiver toute autre extension potentiellement contradictoire.

## <a name="to-update-an-extension-on-your-system"></a>Mettre à jour une extension de votre système

1. Dans le menu **Outils** , choisissez **Extensions et mises à jour**.

2. Dans la vitre gauche, cliquez sur **Mises à jour**.

3. Dans la vitre du milieu, cliquez sur la mise à jour que vous souhaitez installer.

     Le numéro de version de l’extension mise à jour est affiché dans le volet droit, ainsi que d’autres informations.

4. Au bas de la vitre droite, cliquez sur **Mise à jour**.

## <a name="to-publish-an-update-of-an-extension"></a>Pour publier une mise à jour d’une extension

1. Dans Visual Studio, ouvrez la solution pour l’extension que vous souhaitez mettre à jour. Effectuez les modifications.

    > [!IMPORTANT]
    > Toutes les extensions d’utilisateurs non signées ne sont pas mises à jour automatiquement. Vous devriez toujours signer vos extensions.

2. Dans **Solution Explorer**, open *source.extension.manifest*.

3. Dans le concepteur manifeste, augmenter la valeur du nombre dans le domaine **version.**

4. Enregistrer la solution et la construire.

5. Téléchargez le nouveau fichier *.vsix* (dans le\* dossier de l’image du projet) sur le site Web [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

     Lorsqu’un utilisateur qui a une version antérieure de l’extension ouvre **extensions et mises à jour**, la nouvelle version apparaîtra dans la liste des mises à **jour,** à condition que l’outil soit configuré pour rechercher automatiquement les mises à jour.

     Vous pouvez activer ou désactiver la vérification automatique des mises à jour au bas du volet **Mises à jour** **(Activer/désactiver**la détection automatique des mises à jour disponibles ), qui modifie le réglage de la vérification des mises à **jour** dans les**extensions et mises à jour**de l’environnement des options **d’outils** > **Options** > **Environment** > .

    > [!NOTE]
    > À partir de Visual Studio 2015 Mise à jour 2, vous pouvez spécifier (dans **Tools** > **Options** > **Environment** > **Extensions and Updates**) si vous voulez des mises à jour automatiques pour les extensions par utilisateur, toutes les extensions d’utilisateur ou les deux (le paramètre par défaut).

## <a name="see-also"></a>Voir aussi
- [Anatomie d’un paquet VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Trouver et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
