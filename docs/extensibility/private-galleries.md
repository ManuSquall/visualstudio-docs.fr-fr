---
title: Galeries privées | Microsoft Docs
description: Découvrez comment partager les contrôles, les modèles et les outils que vous développez dans le kit de développement logiciel (SDK) Visual Studio en les publiant dans une galerie privée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c64c5880fcdb1d6a1fb3d6fc7c71f55abf7cbbc1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069034"
---
# <a name="private-galleries"></a>Galeries privées
Vous pouvez partager les contrôles, les modèles et les outils que vous développez en les publiant dans une *Galerie privée* sur l’intranet de votre organisation, comme suit :

- Créez un flux Atom (RSS) à un emplacement central correctement configuré (référentiel) sur votre intranet. Pour plus d’informations, consultez [Comment : créer un flux Atom pour une galerie privée](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Distribuez un fichier *. pkgdef* qui décrit la galerie privée. Nous recommandons cette configuration pour les administrateurs qui souhaitent connecter une galerie privée à plusieurs ordinateurs en même temps.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Ajouter une galerie privée à des extensions et des mises à jour dans Visual Studio
 Quand une galerie privée est disponible, vous pouvez l’ajouter aux **extensions et aux mises à jour** dans Visual Studio.

 ![Boîte de dialogue d'ajout de gestionnaire d'extensions](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Pour ajouter une galerie privée aux extensions et mises à jour

1. Dans la barre de menus, choisissez **Outils**  >  **options**.

2. Dans le nœud **environnement** , sélectionnez **extensions et mises à jour**.

3. Choisissez le bouton **Ajouter**.

4. Dans le champ **nom** , entrez un nom pour la galerie privée, par exemple `My Gallery` .

5. Dans le champ **URL** , entrez l’URL du flux Atom ou du site SharePoint qui héberge la galerie privée.

    1. Si l’hôte est un flux Atom qui se connecte à la galerie privée, l’URL ressemble à celle-ci : `http://www.mywebsite/mygallery/atom.xml` .  Cette URL peut faire référence à un fichier ou à un chemin d’accès réseau.

    2. Si l’hôte est un site SharePoint, l’URL ressemble à celle-ci : `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .

### <a name="manage-private-galleries"></a>Gérer les galeries privées
 Un administrateur peut mettre une galerie privée à la disposition de plusieurs ordinateurs en même temps en modifiant le registre système sur chaque ordinateur. Pour ce faire, créez un fichier *. pkgdef* qui décrit les nouvelles clés de Registre et leurs valeurs.  Le format de ce fichier est le suivant.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Pour plus d’informations, consultez [Comment : gérer une galerie privée à l’aide des paramètres du Registre](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Installer des extensions à partir d’une galerie privée
 Vous pouvez rechercher et installer des extensions Visual Studio à partir d’une galerie privée dans **extensions et mises à jour**. Les étapes suivantes utilisent une galerie privée nommée `My Gallery` .

 ![Galerie privée d'installation du gestionnaire d'extensions](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Pour rechercher et installer des extensions à partir d’une galerie privée

1. Dans la barre de menus, choisissez **Outils**  >  **extensions et mises à jour**.

2. Dans le volet gauche, sélectionnez **extensions en ligne**, puis sélectionnez **ma galerie**.

3. Dans le volet droit, sélectionnez une extension, puis cliquez sur le bouton **Télécharger** .

## <a name="update-extensions-from-a-private-gallery"></a>Mettre à jour des extensions à partir d’une galerie privée
 À mesure que de nouvelles versions des extensions Visual Studio sont publiées dans la galerie privée, vous pouvez mettre à jour les extensions que vous avez installées. Les étapes suivantes utilisent une galerie privée nommée `My Repository` .

 ![Mise à jour de la galerie privée du gestionnaire d’extensions](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Pour mettre à jour une extension installée à partir d’une galerie privée

1. Dans la barre de menus, choisissez **Outils**  >  **extensions et mises à jour**.

2. Dans le volet gauche, sélectionnez **mises à jour**, puis sélectionnez **mon référentiel**.

3. Dans le volet droit, sélectionnez une extension, puis cliquez sur le bouton **mettre à jour** .

## <a name="see-also"></a>Voir aussi
- [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Envoyer des extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
