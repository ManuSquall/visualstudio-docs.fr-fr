---
title: Créer un pack d’extensions
description: Découvrez comment créer un pack d’extension avec le modèle d’élément extension Pack
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 213e3e71503ebea8074594bbc88a06980e3e64b4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905135"
---
# <a name="walkthrough-create-an-extension-pack"></a>Procédure pas à pas : créer un pack d'extensions

Un pack d’extension est un ensemble d’extensions qui peuvent être installées ensemble. Les packs d’extension vous permettent de partager facilement vos extensions favorites avec d’autres utilisateurs ou de regrouper un ensemble d’extensions pour un scénario particulier.

## <a name="prerequisites"></a>Prérequis

À compter de Visual Studio 2015, le kit de développement logiciel (SDK) Visual Studio est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

La fonctionnalité du pack d’extension est disponible à partir de Visual Studio 15,8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Créer une extension avec un modèle d’élément de Pack d’extension

Le modèle d’élément de Pack d’extension crée un pack d’extension avec un ensemble d’extensions qui peuvent être installées ensemble.

1. Dans la boîte de dialogue **nouveau projet** , recherchez « VSIX » et sélectionnez **projet VSIX**. Pour le **nom du projet**, tapez « test extension Pack ». Sélectionnez **Create** (Créer).

2. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >  **un nouvel élément**. Accédez au nœud **extensibilité** Visual C# et sélectionnez **Pack d’extension**. Laissez le nom de fichier par défaut (ExtensionPack1. cs).

3. Le fichier ExtensionPack1. vsext est ajouté et contient le code suivant :

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. Le vsixid de l’extension à inclure dans le pack d’extension est disponible sur le [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Recherchez l’extension que vous souhaitez inclure, puis cliquez sur l' **ID de copie**. Vous pouvez mettre à jour le **vsixId** existant dans le fichier ci-dessus ou ajouter une autre extension à la liste.

    ![Copier VsixId à partir de Marketplace](media/vsixid-marketplace.png)

5. Générez le projet et chargez votre extension sur la place de marché. Consultez [publication d’une extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Un pack d’extension peut uniquement installer les extensions qui sont disponibles dans la [galerie](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md) [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou privée.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installez le pack d’extension à partir du Visual Studio Marketplace

Maintenant que l’extension est publiée, installez-la dans Visual Studio et testez-la ici.

::: moniker range="vs-2017"

1. Dans Visual Studio, dans le menu **Outils** , cliquez sur **extensions et mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, dans le menu **Extensions** , cliquez sur **Extensions managées**.

::: moniker-end

2. Cliquez sur **en ligne** , puis recherchez « Pack d’extensions de test ».

3. Cliquez sur **Télécharger**. L’extension et la liste des extensions incluses dans le pack d’extension seront alors planifiées pour l’installation.

4. Vous trouverez ci-dessous un exemple de vue de téléchargement du pack d’extension de la boîte de dialogue **gérer les extensions** . Si vous préférez installer uniquement certaines des extensions incluses dans le pack d’extension, vous pouvez modifier la liste d’extensions dans **planifié pour l’installation**.

    ![Télécharger le pack d’extension à partir de Marketplace](media/vside-extensionpack.png)

5. Pour terminer l’installation, fermez toutes les instances de Visual Studio.

## <a name="remove-the-extension"></a>Supprimer l’extension

Pour supprimer l’extension de votre ordinateur :

::: moniker range="vs-2017"

1. Dans Visual Studio, dans le menu **Outils** , cliquez sur **extensions et mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, dans le menu **Extensions** , cliquez sur **Extensions managées**.

::: moniker-end

2. Sélectionnez **Pack d’extension de test** , puis cliquez sur **désinstaller**. L’extension et sa liste d’extensions comprises dans le pack d’extension seront alors planifiées pour la désinstallation.

3. Pour terminer la désinstallation, fermez toutes les instances de Visual Studio.
