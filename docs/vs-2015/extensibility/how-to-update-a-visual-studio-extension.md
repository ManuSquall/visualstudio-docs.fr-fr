---
title: Mettre à jour une extension | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0d1464cdd2be79cd93a3e98bcf8769e8f4b8b89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840206"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Guide pratique pour mettre à jour une extension Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez mettre à jour une extension Visual Studio sur votre système en utilisant des **extensions et des mises à jour** pour installer la version mise à jour. Si vous créez une version mise à jour d’une extension, vous pouvez la signaler comme étant mise à jour en incrémentant le numéro de version dans le manifeste VSIX.

 Les mises à jour sont installées lorsque le manifeste VSIX de l’extension entrante a le même `ID` que le numéro installé et un nombre plus élevé `Version` . Si le `Version` nombre est identique ou inférieur, le package ne peut pas être installé. Si les `ID` valeurs ne correspondent pas, le package qui n’est pas encore installé est reconnu comme une extension distincte.

 Pour éviter les conflits lors du développement, nous vous recommandons de désinstaller les versions antérieures des extensions en cours et de désinstaller ou désactiver toute autre extension potentiellement conflictuelle.

### <a name="to-update-an-extension-on-your-system"></a>Pour mettre à jour une extension sur votre système

1. Dans le menu **Outils**, cliquez sur **Extensions et mises à jour**.

2. Dans le volet gauche, cliquez sur **mises à jour**.

3. Dans le volet central, cliquez sur la mise à jour que vous souhaitez installer.

     Le numéro de version de l’extension mise à jour s’affiche dans le volet droit, ainsi que d’autres informations.

4. En bas du volet droit, cliquez sur **mettre à jour**.

### <a name="to-publish-an-update-of-an-extension"></a>Pour publier une mise à jour d’une extension

1. Dans Visual Studio, ouvrez la solution pour l’extension que vous souhaitez mettre à jour. Apportez les modifications nécessaires.

    > [!IMPORTANT]
    > Les extensions utilisateur non signées ne sont pas mises à jour automatiquement. Vous devez toujours signer vos extensions.

2. Dans **Explorateur de solutions**, ouvrez source. extension. manifest.

3. Dans le concepteur de manifeste, augmentez la valeur du nombre dans le champ **version** .

4. Enregistrez la solution et générez-la.

5. Téléchargez le nouveau fichier. vsix (dans le dossier \bin\Debug\ du projet) sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

     Lorsqu’un utilisateur qui dispose d’une version antérieure de l’extension ouvre **extensions et mises à jour**, la nouvelle version s’affiche dans la liste des **mises à jour** , à condition que l’outil soit configuré pour rechercher automatiquement les mises à jour.

     Vous pouvez activer ou désactiver la vérification automatique des mises à jour en bas du volet **mises à jour** (**activer/désactiver la détection automatique des mises à jour disponibles**), qui modifie le paramètre **vérifier les mises à jour** dans **Outils/Options/environnement/extensions et mises à jour**.

    > [!NOTE]
    > À partir de Visual Studio 2015 Update 2, vous pouvez spécifier (dans **Outils / Options / Environnement / Extensions et mises à jour**) si vous souhaitez des mises à jour automatiques pour les extensions par utilisateur, pour toutes les extensions utilisateur ou pour les deux (le paramètre par défaut).

## <a name="see-also"></a>Voir aussi
 [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md) [recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
