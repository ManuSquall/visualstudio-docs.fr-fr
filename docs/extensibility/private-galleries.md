---
title: Galeries privées (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4056e4dedf06ffe86755bf946c77032d6f6782dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702037"
---
# <a name="private-galleries"></a>Galeries privées
Vous pouvez partager les contrôles, les modèles et les outils que vous développez en les affichant dans une *galerie privée* sur l’intranet pour votre organisation, comme suit :

- Créez un flux Atom (RSS) à un emplacement central configuré (référentiel) sur votre intranet. Pour plus d’informations, voir [Comment : Créer un flux Atom pour une galerie privée.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

- Distribuez un fichier *.pkgdef* qui décrit la galerie privée. Nous recommandons cette configuration pour les administrateurs qui veulent connecter une galerie privée à de nombreux ordinateurs en même temps.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Ajouter une galerie privée aux extensions et mises à jour dans Visual Studio
 Lorsqu’une galerie privée est disponible, vous pouvez l’ajouter à **Extensions et Mises à jour** dans Visual Studio.

 ![Boîte de dialogue d'ajout de gestionnaire d'extensions](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Pour ajouter une galerie privée aux extensions et mises à jour

1. Sur la barre de menu, choisissez **Tools** > **Options**.

2. Dans le nœud **environnement,** sélectionnez **Extensions et Mises à jour**.

3. Choisissez le bouton **Ajouter**.

4. Dans le champ **Name,** entrez un nom `My Gallery`pour la galerie privée, par exemple, .

5. Dans le champ **URL,** entrez l’URL du flux Atom ou du site SharePoint qui héberge la galerie privée.

    1. Si l’hôte est un flux Atom qui se connecte à http://www.mywebsite/mygallery/atom.xmlla galerie privée, l’URL ressemblerait à celle-ci: .  Cette URL peut se référer à un fichier ou à un chemin réseau.

    2. Si l’hôte est un site SharePoint, http://mysharepoint/sites/mygallery/forms/AllItems.aspxl’URL ressemblerait à celui-ci: .

### <a name="manage-private-galleries"></a>Gérer les galeries privées
 Un administrateur peut mettre une galerie privée à la disposition de plusieurs ordinateurs en même temps en modifiant le registre du système sur chaque ordinateur. Pour ce faire, créez un fichier *.pkgdef* qui décrit les nouvelles clés de registre et leurs valeurs.  Le format de ce fichier est le suivant.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Pour plus d’informations, voir [Comment gérer une galerie privée en utilisant les paramètres du registre](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Installer des extensions à partir d’une galerie privée
 Vous pouvez rechercher et installer des extensions Visual Studio à partir d’une galerie privée dans **Extensions and Updates**. Les étapes suivantes utilisent `My Gallery`une galerie privée nommée .

 ![Galerie privée d'installation du gestionnaire d'extensions](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Rechercher et installer des extensions à partir d’une galerie privée

1. Sur la barre de menu, choisissez des > **extensions d’outils et des mises à jour**. **Tools**

2. Dans la vitre gauche, sélectionnez **extensions en ligne,** puis sélectionnez **My Gallery**.

3. Dans le volet droit, sélectionnez une extension, puis choisissez le bouton **Télécharger.**

## <a name="update-extensions-from-a-private-gallery"></a>Mettre à jour les extensions d’une galerie privée
 Comme de nouvelles versions d’extensions Visual Studio sont affichées dans la galerie privée, vous pouvez mettre à jour les extensions que vous avez installées. Les étapes suivantes utilisent `My Repository`une galerie privée nommée .

 ![Mise à jour de la galerie privée du gestionnaire d’extensions](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Mettre à jour une extension installée à partir d’une galerie privée

1. Sur la barre de menu, choisissez des > **extensions d’outils et des mises à jour**. **Tools**

2. Dans la vitre gauche, sélectionnez **mises à jour,** puis sélectionnez **Mon Dépôt**.

3. Dans le volet droit, sélectionnez une extension, puis choisissez le bouton **Mise à jour.**

## <a name="see-also"></a>Voir aussi
- [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Extensions Ship Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
