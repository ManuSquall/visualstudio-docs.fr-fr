---
title: Créer un Pack d’Extension avec le modèle d’élément Extension Pack | Microsoft Docs
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: gregvanl
ms.author: gregvanl
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 7899a096bb2a56e93ea55a4ba0a17cde272bd615
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58193703"
---
# <a name="walkthrough-create-an-extension-pack"></a>Procédure pas à pas : Créer un pack d’extensions

Un Pack d’Extension est un ensemble d’extensions qui peuvent être installés ensemble. Packs d’extension permettent de facilement partager vos extensions préférées avec d’autres utilisateurs ou de regrouper un ensemble d’extensions ensemble pour un scénario particulier.

## <a name="prerequisites"></a>Prérequis

À partir de Visual Studio 2015, le SDK Visual Studio est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

La fonctionnalité de Pack d’Extension est disponible à partir de Visual Studio 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Créer une extension avec un modèle d’élément de Pack d’Extension

Le modèle d’élément de Pack d’Extension crée un Pack d’Extension avec un ensemble d’extensions qui peuvent être installés ensemble.

1. Dans le **nouveau projet** boîte de dialogue, recherchez « vsix » et sélectionnez **projet VSIX**. Pour **nom_projet**, tapez « Pack d’Extension de Test ». Sélectionnez **Créer**.

2. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **ajouter** > **un nouvel élément**. Accédez à Visual C# **extensibilité** nœud et sélectionnez **Pack d’Extension**. Laissez le nom de fichier par défaut (ExtensionPack1.cs).

3. ExtensionPack1.vsext fichier est ajouté, qui contient le code suivant

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

4. Vous trouverez le vsixid de l’extension à inclure dans le Pack d’Extension sur le [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Recherchez l’extension que vous souhaitez inclure, puis cliquez sur **ID de copie**. Vous pouvez mettre à jour existantes **vsixId** dans l’exemple ci-dessus de fichiers ou d’ajouter une autre extension à la liste.

    ![VsixId de copie à partir de la place de marché](media/vsixid-marketplace.png)

5. Générez le projet et télécharger votre extension à la place de marché. Consultez [publication d’une extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Un pack d’Extension permettre installer uniquement les extensions qui sont disponibles sur le [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou [galerie privée](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installer le Pack d’Extension à partir de la place de marché Visual Studio

Maintenant que l’extension est publiée, installez-le dans Visual Studio et testez-le.

::: moniker range="vs-2017"

1. Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, sur le **Extensions** menu, cliquez sur **Extensions managées**.

::: moniker-end

2. Cliquez sur **Online** , puis recherchez « Pack d’Extension de Test ».

3. Cliquez sur **Télécharger**. L’extension et sa liste d’extensions incluses dans le Pack d’Extension sera ensuite prévue pour l’installation.

4. Voici un exemple de vue de téléchargement de Pack d’Extension de la **gérer les Extensions** boîte de dialogue. Si vous préférez installer uniquement certaines des extensions incluses dans le pack d’Extension, vous pouvez modifier la liste des extensions dans **planifiée pour installer**.

    ![Télécharger le Pack d’Extension à partir de la place de marché](media/vside-extensionpack.png)

5. Pour terminer l’installation, fermez toutes les instances de Visual Studio.

## <a name="remove-the-extension"></a>Supprimer l’extension

Pour supprimer l’extension de votre ordinateur :

::: moniker range="vs-2017"

1. Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans Visual Studio, sur le **Extensions** menu, cliquez sur **Extensions managées**.

::: moniker-end

2. Sélectionnez **module d’Extension de Test** puis cliquez sur **désinstallation**. L’extension et sa liste d’extensions incluses dans le Pack d’Extension sera ensuite prévue pour la désinstallation.

3. Pour terminer la désinstallation, fermez toutes les instances de Visual Studio.
