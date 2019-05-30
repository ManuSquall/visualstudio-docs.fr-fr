---
title: Publier l’extension à l’aide de la ligne de commande
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6b5531bc5dc138f2f90a0a67da39f9583bc4b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320650"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Procédure pas à pas : Publication d’une extension de Visual Studio via la ligne de commande

Cette procédure pas à pas vous montre comment publier une extension Visual Studio sur la place de marché Visual Studio à l’aide de la ligne de commande. Lorsque vous ajoutez votre extension à la place de marché, les développeurs peuvent utiliser le [ **Extensions et mises à jour** ](../ide/finding-and-using-visual-studio-extensions.md) boîte de dialogue pour y rechercher des extensions nouvelles et mises à jour.

VsixPublisher.exe est l’outil de ligne de commande pour la publication des extensions de Visual Studio à la place de marché. Il est accessible à partir de ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Les commandes disponibles sur cet outil sont : **publier**, **createPublisher**, **deletePublisher**, **deleteExtension**,  **connexion**, **déconnexion**.

## <a name="commands"></a>Commandes

### <a name="publish"></a>publish

Publie une extension à la place de marché. L’extension peut être une extension vsix, un fichier exe/msi ou un lien. Si l’extension existe déjà avec la même version, elle remplace l’extension. Si l’extension n’existe pas déjà, il crée une nouvelle extension.

|Options de commande |Description |
|---------|---------|
|charge utile (obligatoire) | Soit un chemin d’accès à la charge utile de publier ou d’un lien à utiliser comme la « URL informations ». |
|publishManifest (required) | Chemin d’accès à la publication manifeste de fichier à utiliser. |
|ignoreWarnings | Liste d’avertissements à ignorer lors de la publication d’une extension. Ces avertissements sont affichés sous forme de messages de la ligne de commande lors de la publication d’une extension. (par exemple, « VSIXValidatorWarning01, VSIXValidatorWarning02 »)
|personalAccessToken | Accès jeton (personnel) qui est utilisé pour authentifier le serveur de publication. Si n’est fourni, le jeton d’accès personnel est acquis auprès des utilisateurs connectés. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Crée un serveur de publication sur la place de marché. Enregistre également le serveur de publication à la machine pour les actions futures (par exemple, la suppression/une extension de publication).

|Options de commande |Description |
|---------|---------|
|displayName (obligatoire) | Nom complet du serveur de publication. |
|publisherName (obligatoire) | Le nom du serveur de publication (par exemple, l’identificateur). |
|personalAccessToken (obligatoire) | Jeton d’accès personnel qui est utilisé pour authentifier le serveur de publication. |
|shortDescription | Une brève description du serveur de publication (pas un fichier). |
|longDescription | Longue description du serveur de publication (pas un fichier). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Supprime un serveur de publication sur la place de marché.

|Options de commande |Description |
|---------|---------|
|publisherName (obligatoire) | Le nom du serveur de publication (par exemple, l’identificateur). |
|personalAccessToken (obligatoire) | Jeton d’accès personnel qui est utilisé pour authentifier le serveur de publication. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Supprime une extension de la place de marché.

|Options de commande |Description |
|---------|---------|
|extensionName (required) | Le nom de l’extension à supprimer. |
|publisherName (obligatoire) | Le nom du serveur de publication (par exemple, l’identificateur). |
|personalAccessToken | Jeton d’accès personnel qui est utilisé pour authentifier le serveur de publication. Si n’est fourni, le jeton d’accès personnel est acquis auprès des utilisateurs connectés. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>connexion

Se connecte à un serveur de publication à l’ordinateur.

|Options de commande |Description |
|---------|---------|
|personalAccessToken (required | Jeton d’accès personnel qui est utilisé pour authentifier le serveur de publication. |
|publisherName (obligatoire) | Le nom du serveur de publication (par exemple, l’identificateur). |
|overwrite | Spécifie que n’importe quel éditeur existant doit être remplacé par le nouveau jeton d’accès personnel. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>déconnexion

Enregistre un serveur de publication en dehors de l’ordinateur.

|Options de commande |Description |
|---------|---------|
|publisherName (obligatoire) | Le nom du serveur de publication (par exemple, l’identificateur). |
|ignoreMissingPublisher | Spécifie que l’outil ne doit pas d’erreur si le serveur de publication spécifié n'est pas déjà connecté en. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>fichier de publishManifest

Un fichier publishManifest est utilisé par le **publier** commande. Il représente toutes les métadonnées concernant l’extension de la place de marché doit connaître. Si l’extension en cours de téléchargement est à partir d’une extension VSIX, la propriété « identity » doit avoir uniquement de « internalName » définie. Il s’agit, car le reste des propriétés « identity » peut être généré à partir du fichier vsixmanifest. Si l’extension est un fichier msi/exe ou une extension de lien, l’utilisateur doit fournir les champs requis dans la propriété « identity ». Le reste du manifeste contient des informations spécifiques à la place de marché (par exemple, les catégories, que Q & r sont activée, etc..).

Exemple de fichier VSIX extension publishManifest :

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

Exemple de fichier publishManifest MSI/EXE ou de lien :

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Fichiers de ressources

Fichiers de ressources peuvent être fournis pour l’incorporation des éléments tels que des images dans le fichier Lisez-moi. Par exemple, si une extension a le document de Markdown suivant « présentation » :

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Afin de résoudre « images/testlogo.png » dans l’exemple précédent, un utilisateur peut fournir des « assetFiles » dans leur publication manifeste comme ci-dessous :

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Procédure pas à pas publication

### <a name="prerequisites"></a>Prérequis

Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Créer une extension Visual Studio

Dans ce cas, nous allons utiliser une extension de package Visual Studio par défaut, mais les mêmes étapes sont valides pour chaque type d’extension.

1. Créer un VSPackage en c# nommé « TestPublish » qui comporte une commande de menu. Pour plus d’informations, consultez [créer votre première Extension : Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Votre extension de package

1. Mettre à jour l’extension vsixmanifest avec les informations correctes sur le nom de produit, auteur et la version.

   ![mettre à jour d’extension vsixmanifest](media/update-extension-vsixmanifest.png)

2. Générer votre extension **version** mode. Maintenant, votre extension est empaquetée en tant qu’une extension VSIX dans le dossier \bin\Release.

3. Vous pouvez double-cliquer sur l’extension VSIX pour vérifier l’installation.

### <a name="test-the-extension"></a>Tester l’extension

 Avant de distribuer l’extension, générer et tester pour vous assurer qu’il est installé correctement dans l’instance expérimentale de Visual Studio.

1. Dans Visual Studio, démarrez le débogage. Pour ouvrir une instance expérimentale de Visual Studio.

2. Dans l’instance expérimentale, accédez à la **outils** menu et cliquez sur **Extensions et mises à jour...** . L’extension TestPublish doit apparaître dans le volet central et être activée.

3. Sur le **outils** menu, vérifiez que vous voyez la commande de test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publier l’extension à la place de marché via la ligne de commande

1. Assurez-vous que vous avez créé la version Release de votre extension et qu’il est à jour.

2. Assurez-vous que vous avez créé des fichiers publishmanifest.json et overview.md.

3. Ouvrez la ligne de commande et accédez au répertoire de \VSSDK\VisualStudioIntegration\Tools\Bin\ ${VSInstallDir}.

4. Pour créer un nouveau serveur de publication, utilisez la commande suivante :

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Sur la création réussie du serveur de publication, vous verrez le message de ligne de commande suivant :

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Vous pouvez vérifier le nouveau serveur de publication que vous avez créé en accédant à [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Pour publier une nouvelle extension, utilisez la commande suivante :

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Sur la création réussie du serveur de publication, vous verrez le message de ligne de commande suivant :

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Vous pouvez vérifier la nouvelle extension que vous avez publié en accédant à [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installer l’extension à partir de Visual Studio Marketplace

Maintenant que l’extension est publiée, installez-le dans Visual Studio et testez-le.

1. Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour...** .

2. Cliquez sur **Online** , puis recherchez TestPublish.

3. Cliquez sur **Télécharger**. L’extension sera ensuite être planifiée pour l’installation.

4. Pour terminer l’installation, fermez toutes les instances de Visual Studio.

## <a name="remove-the-extension"></a>Supprimer l’extension

Vous pouvez supprimer l’extension à partir de Visual Studio Marketplace et à partir de votre ordinateur.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Pour supprimer l’extension à partir de la place de marché via la ligne de commande

1. Si vous souhaitez supprimer une extension, utilisez la commande suivante :

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Sur la suppression réussie de l’extension, vous verrez le message de ligne de commande suivant :

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension à partir de votre ordinateur

1. Dans Visual Studio, sur le **outils** menu, cliquez sur **Extensions et mises à jour**.

2. Sélectionnez « MyVsixExtension », puis cliquez **désinstallation**. L’extension sera ensuite être planifiée pour la désinstallation.

3. Pour terminer la désinstallation, fermez toutes les instances de Visual Studio.
