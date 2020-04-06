---
title: Créez un pack d’extension avec le modèle d’élément de pack d’extension Microsoft Docs
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697746"
---
# <a name="walkthrough-create-an-extension-pack"></a>Procédure pas à pas : créer un pack d'extensions

Un pack d’extension est un ensemble d’extensions qui peuvent être installées ensemble. Les packs d’extension vous permettent de partager facilement vos extensions préférées avec d’autres utilisateurs ou de regrouper un ensemble d’extensions pour un scénario particulier.

## <a name="prerequisites"></a>Prérequis

À partir de Visual Studio 2015, le Visual Studio SDK est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

La fonction Extension Pack est disponible à partir de Visual Studio 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Créez une extension avec un modèle d’élément Extension Pack

Le modèle d’élément Extension Pack crée un pack d’extension avec un ensemble d’extensions qui peuvent être installées ensemble.

1. Dans le dialogue du **nouveau projet,** recherchez «vsix» et sélectionnez **le projet VSIX**. Pour **le nom du projet**, tapez "Test Extension Pack". Sélectionnez **Create** (Créer).

2. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Rendez-vous sur le nœud Visual **C’Extensibility** et sélectionnez **Extension Pack**. Laissez le nom du fichier par défaut (ExtensionPack1.cs).

3. ExtensionPack1.vsext fichier est ajouté qui contient le code suivant

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

4. Le vsixid de l’extension à inclure dans le pack d’extension peut être trouvé sur le [marché Visual Studio](https://marketplace.visualstudio.com/). Trouvez l’extension que vous souhaitez inclure et cliquez sur **Copy ID**. Vous pouvez mettre à jour le **vsixId** existant dans le fichier ci-dessus ou ajouter une autre extension à la liste.

    ![Copie VsixId de Marketplace](media/vsixid-marketplace.png)

5. Construisez le projet et téléchargez votre extension sur le Marché. Voir [Publishing a Visual Studio extension](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Un pack Extension ne peut installer que des extensions qui sont disponibles sur le [marché visual studio](https://marketplace.visualstudio.com/) ou la galerie [privée.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installer le pack d’extension à partir du marché visual Studio

Maintenant que l’extension est publiée, installez-la dans Visual Studio et testez-la là.

::: moniker range="vs-2017"

1. Dans Visual Studio, sur le menu **Tools,** cliquez sur **Extensions et Mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, sur le menu **Extensions,** cliquez sur **Managed Extensions**.

::: moniker-end

2. Cliquez **en ligne,** puis recherchez "Test Extension Pack".

3. Cliquez sur **Télécharger**. L’extension et sa liste d’extensions incluses dans le pack d’extension seront ensuite prévues pour l’installation.

4. Vous trouverez ci-dessous un exemple de vue de téléchargement d’extension du dialogue **Manage Extensions.** Si vous préférez installer seulement quelques-unes des extensions incluses dans le pack Extension, vous pouvez modifier la liste d’extension dans **Scheduled For Install**.

    ![Télécharger Extension Pack de Marketplace](media/vside-extensionpack.png)

5. Pour compléter l’installation, fermez toutes les instances de Visual Studio.

## <a name="remove-the-extension"></a>Supprimer l’extension

Pour supprimer l’extension de votre ordinateur :

::: moniker range="vs-2017"

1. Dans Visual Studio, sur le menu **Tools,** cliquez sur **Extensions et Mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, sur le menu **Extensions,** cliquez sur **Managed Extensions**.

::: moniker-end

2. Sélectionnez **Test Extension Pack,** puis cliquez sur **Uninstall**. L’extension et sa liste d’extensions incluses dans le pack d’extension seront alors prévues pour un désinstallation.

3. Pour compléter la désinstallation, fermez toutes les instances de Visual Studio.
