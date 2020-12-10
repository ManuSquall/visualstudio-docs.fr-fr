---
title: 'Comment : mettre à jour une extension Visual Studio | Microsoft Docs'
description: Découvrez comment mettre à jour une extension Visual Studio sur votre système en utilisant des extensions et des mises à jour pour installer la version mise à jour.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: be22ca13fd5af8df88501835c8a030cc6469e179
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995602"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Comment : mettre à jour une extension Visual Studio
Vous pouvez mettre à jour une extension Visual Studio sur votre système en utilisant des **extensions et des mises à jour** pour installer la version mise à jour. Si vous créez une version mise à jour d’une extension, vous pouvez la signaler comme étant mise à jour en incrémentant le numéro de version dans le manifeste VSIX.

 Les mises à jour sont installées lorsque le manifeste VSIX de l’extension entrante a le même `ID` que le numéro installé et un nombre plus élevé `Version` . Si le `Version` nombre est identique ou inférieur, le package ne peut pas être installé. Si les `ID` valeurs ne correspondent pas, le package qui n’est pas encore installé est reconnu comme une extension distincte.

 Pour éviter les conflits lors du développement, nous vous recommandons de désinstaller les versions antérieures des extensions en cours et de désinstaller ou désactiver toute autre extension potentiellement conflictuelle.

## <a name="to-update-an-extension-on-your-system"></a>Pour mettre à jour une extension sur votre système

1. Dans le menu **Outils**, cliquez sur **Extensions et mises à jour**.

2. Dans le volet gauche, cliquez sur **mises à jour**.

3. Dans le volet central, cliquez sur la mise à jour que vous souhaitez installer.

     Le numéro de version de l’extension mise à jour s’affiche dans le volet droit, ainsi que d’autres informations.

4. En bas du volet droit, cliquez sur **mettre à jour**.

## <a name="to-publish-an-update-of-an-extension"></a>Pour publier une mise à jour d’une extension

1. Dans Visual Studio, ouvrez la solution pour l’extension que vous souhaitez mettre à jour. Apportez les modifications nécessaires.

    > [!IMPORTANT]
    > Les extensions utilisateur non signées ne sont pas mises à jour automatiquement. Vous devez toujours signer vos extensions.

2. Dans **Explorateur de solutions**, ouvrez *source. extension. manifest*.

3. Dans le concepteur de manifeste, augmentez la valeur du nombre dans le champ **version** .

4. Enregistrez la solution et générez-la.

5. Téléchargez le nouveau fichier *. vsix* (dans le dossier * \bin\debug \* du projet) sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) .

     Lorsqu’un utilisateur qui dispose d’une version antérieure de l’extension ouvre **extensions et mises à jour**, la nouvelle version s’affiche dans la liste des **mises à jour** , à condition que l’outil soit configuré pour rechercher automatiquement les mises à jour.

     Vous pouvez activer ou désactiver la vérification automatique des mises à jour en bas du volet **mises à jour** (**activer/désactiver la détection automatique des mises à jour disponibles**), qui modifie le paramètre **vérifier les mises à jour** dans **Outils**  >  **options** extensions de l'  >  **environnement**  >  **et mises à jour**.

    > [!NOTE]
    > À compter de Visual Studio 2015 Update 2, vous pouvez spécifier (dans **Outils**  >  **options**  >  **environnement**  >  **et mises à jour**) si vous souhaitez des mises à jour automatiques pour les extensions par utilisateur, pour toutes les extensions utilisateur ou pour les deux (paramètre par défaut).

## <a name="see-also"></a>Voir aussi
- [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
