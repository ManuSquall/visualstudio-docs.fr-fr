---
title: Modèle de projet VSIX (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697937"
---
# <a name="vsix-project-template"></a>Modèle de projet VSIX

Vous pouvez utiliser le modèle vsIX Project pour envelopper une ou plusieurs extensions Visual Studio dans un projet VSIX, puis publier le paquet sur le site Web [Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

 Le déploiement VSIX prend en charge VSPackages, assemblages, composants MEF, modèles de projets, modèles d’éléments, contrôles de boîte à outils et types d’extension personnalisés.

> [!NOTE]
> Pour utiliser les projets VSIX, vous devez installer le Visual Studio SDK. Pour plus d’informations sur le Visual Studio SDK, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Où trouver le modèle de projet VSIX

Le modèle de projet VSIX est disponible dans la boîte de dialogue **du nouveau projet** en recherchant le « vsix ».  Il existe à la fois une version C et Visual Basic.

> [!TIP]
> Vous devez vous assurer que le cadre .NET 4.5 ou plus est spécifié dans la case de liste de décrochage en haut du dialogue **du nouveau projet.**

## <a name="uses-of-the-vsix-project-template"></a>Utilisations du modèle de projet VSIX

Le modèle de projet VSIX a deux utilisations principales :

- Pour déployer des modèles de projet, des modèles d’éléments et des extensions.

- Pour envelopper les sorties de plusieurs extensions en un seul paquet de déploiement.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Emballage d’une extension dans un projet VSIX vide

Vous pouvez emballer une extension existante, ou une extension qui n’a pas déjà de support VSIX, en l’enveloppant dans un projet VSIX vide. L’extension à envelopper doit être d’un type qui est soutenu par le [schéma VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Pour emballer une extension en utilisant un projet VSIX

1. Construisez les projets qui composent votre extension.

2. Créez un projet VSIX en utilisant le modèle **de projet VSIX.**

    *Source.extension.vsixmanifest* ouvre dans **Manifest Designer**.

3. Sur l’onglet **Actifs,** choisissez le **nouveau** bouton.

    La boîte de dialogue **Add New Asset** apparaît.

4. Dans la liste **type,** choisissez le type d’extension à ajouter.

5. Pour ajouter un élément d’extension ou de contenu inclus dans la solution actuelle (par exemple, un modèle d’élément ou un assemblage compilé), effectuez les étapes suivantes :

   1. Dans la liste **Source,** choisissez **un projet dans la solution actuelle**.

   2. Dans la liste **du projet,** choisissez le nom de l’extension.

   3. Dans **l’Embed dans cette** boîte de dossier, entrez le nom d’un dossier dans lequel intégrer l’actif, puis choisissez le bouton **OK.**

6. Pour ajouter un élément d’extension ou de contenu qui n’est pas inclus dans la solution actuelle, effectuez les étapes suivantes :

   1. Dans la case **source,** choisissez **Fichier sur le système de fichiers**.

   2. Dans le champ **Path,** entrez le chemin complet vers le fichier d’extension compilé ou compressé, ou utilisez le bouton **Parcourir** pour naviguer vers le fichier.

   3. Dans **l’Embed dans cette** boîte de dossier, entrez le nom d’un dossier dans lequel intégrer l’actif, puis choisissez le bouton **OK.**

7. Si vous voulez que votre colis inclue des extensions supplémentaires, ajoutez-les de la même manière.

8. Générez la solution.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]construit un fichier *.vsix* qui contient un fichier manifeste VSIX, un fichier [Content_Types]*.xml,* et tous les actifs de vulgarisation que vous avez ajouté au projet.

## <a name="see-also"></a>Voir aussi

- [SCHÉMA d’extension VSIX 2.0 référence](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
