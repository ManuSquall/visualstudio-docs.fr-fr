---
title: Publier l’extension à l’aide de la ligne de commande
description: Découvrez comment utiliser la ligne de commande pour publier une extension dans le Visual Studio Marketplace, ce qui permet aux développeurs de rechercher les extensions nouvelles et mises à jour.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98c73da67e607346138d7d6fae124a86b7a34618
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961844"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Procédure pas à pas : publication d’une extension Visual Studio à l’aide de la ligne de commande

Cette procédure pas à pas vous montre comment publier une extension Visual Studio dans le Visual Studio Marketplace à l’aide de la ligne de commande. Lorsque vous ajoutez votre extension sur la place de marché, les développeurs peuvent utiliser la boîte de dialogue [**extensions et mises à jour**](../ide/finding-and-using-visual-studio-extensions.md) pour y rechercher des extensions nouvelles et mises à jour.

VsixPublisher.exe est l’outil en ligne de commande pour la publication d’extensions Visual Studio sur Marketplace. Elle est accessible à partir de $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Les commandes disponibles pour cet outil sont : **Publish**, **createPublisher**, **deletePublisher**, **deleteExtension**, **login**, **logout**.

## <a name="commands"></a>Commandes

### <a name="publish"></a>Publier

Publie une extension sur la place de marché. L’extension peut être une extension VSIX, un fichier exe/MSI ou un lien. Si l’extension existe déjà avec la même version, elle remplacera l’extension. Si l’extension n’existe pas encore, elle crée une nouvelle extension.

|Options de commande |Description |
|---------|---------|
|charge utile (obligatoire) | Chemin d’accès à la charge utile à publier ou lien à utiliser comme « plus d’informations ». |
|publishManifest (obligatoire) | Chemin d’accès au fichier manifeste de publication à utiliser. |
|ignoreWarnings | Liste d’avertissements à ignorer lors de la publication d’une extension. Ces avertissements s’affichent sous la forme de messages de ligne de commande lors de la publication d’une extension. (par exemple, « VSIXValidatorWarning01, VSIXValidatorWarning02 »)
|personalAccessToken | Le jeton d’accès personnel (PAT) utilisé pour authentifier le serveur de publication. S’il n’est pas fourni, le PAT est acquis auprès des utilisateurs connectés. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Crée un serveur de publication sur la place de marché. Consigne également le serveur de publication sur l’ordinateur pour les actions ultérieures (par exemple, la suppression ou la publication d’une extension).

|Options de commande |Description |
|---------|---------|
|displayName (obligatoire) | Nom complet du serveur de publication. |
|publisherName (obligatoire) | Nom du serveur de publication (par exemple, l’identificateur). |
|personalAccessToken (obligatoire) | Jeton d’accès personnel utilisé pour authentifier le serveur de publication. |
|shortDescription | Brève description du serveur de publication (pas un fichier). |
|longDescription | Description longue du serveur de publication (pas un fichier). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Supprime un serveur de publication sur la place de marché.

|Options de commande |Description |
|---------|---------|
|publisherName (obligatoire) | Nom du serveur de publication (par exemple, l’identificateur). |
|personalAccessToken (obligatoire) | Jeton d’accès personnel utilisé pour authentifier le serveur de publication. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Supprime une extension de la place de marché.

|Options de commande |Description |
|---------|---------|
|extensionName (obligatoire) | Nom de l’extension à supprimer. |
|publisherName (obligatoire) | Nom du serveur de publication (par exemple, l’identificateur). |
|personalAccessToken | Jeton d’accès personnel utilisé pour authentifier le serveur de publication. S’il n’est pas fourni, le Pat est acquis auprès des utilisateurs connectés. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Enregistre un serveur de publication sur l’ordinateur.

|Options de commande |Description |
|---------|---------|
|personalAccessToken (obligatoire | Jeton d’accès personnel utilisé pour authentifier le serveur de publication. |
|publisherName (obligatoire) | Nom du serveur de publication (par exemple, l’identificateur). |
|overwrite | Spécifie que tout serveur de publication existant doit être remplacé par le nouveau jeton d’accès personnel. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Déconnecte un serveur de publication de l’ordinateur.

|Options de commande |Description |
|---------|---------|
|publisherName (obligatoire) | Nom du serveur de publication (par exemple, l’identificateur). |
|ignoreMissingPublisher | Spécifie que l’outil ne doit pas être erroné si le serveur de publication spécifié n’est pas déjà connecté. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>fichier publishManifest

Un fichier publishManifest est utilisé par la commande **publier** . Il représente toutes les métadonnées relatives à l’extension que la place de marché doit connaître. Si l’extension téléchargée provient d’une extension VSIX, la propriété « Identity » doit uniquement avoir le « internalName » défini. Cela est dû au fait que le reste des propriétés « Identity » peut être généré à partir du fichier vsixmanifest. Si l’extension est un fichier MSI/exe ou une extension de lien, l’utilisateur doit fournir les champs requis dans la propriété « Identity ». Le reste du manifeste contient des informations spécifiques à la place de marché (par exemple, des catégories, si Q&a est activé, etc.).

Exemple de fichier publishManifest d’extension VSIX :

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

Exemple de fichier MSI/EXE ou LINK publishManifest :

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

Des fichiers de ressources peuvent être fournis pour incorporer des éléments tels que des images dans le fichier Lisez-moi. Par exemple, si une extension contient le document « vue d’ensemble » de la démarque suivante :

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Afin de résoudre « images/testlogo.png » dans l’exemple précédent, un utilisateur peut fournir « assetFiles » dans son manifeste de publication, comme ci-dessous :

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

## <a name="publishing-walkthrough"></a>Procédure de publication

### <a name="prerequisites"></a>Prérequis

Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Créer une extension Visual Studio

Dans ce cas, nous utiliserons une extension VSPackage par défaut, mais les mêmes étapes sont valides pour chaque type d’extension.

1. Créez un VSPackage en C# nommé « TestPublish » avec une commande de menu. Pour plus d’informations, consultez [création de votre première extension : Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Empaqueter votre extension

1. Mettez à jour l’extension vsixmanifest avec les informations correctes sur le nom du produit, l’auteur et la version.

   ![mettre à jour l’extension vsixmanifest](media/update-extension-vsixmanifest.png)

2. Générez votre extension en mode **Release** . À présent, votre extension sera empaquetée en tant que VSIX dans le dossier \bin\Release

3. Vous pouvez double-cliquer sur le VSIX pour vérifier l’installation.

### <a name="test-the-extension"></a>Tester l’extension

 Avant de distribuer l’extension, générez-la et testez-la pour vous assurer qu’elle est installée correctement dans l’instance expérimentale de Visual Studio.

1. Dans Visual Studio, démarrez le débogage. pour ouvrir une instance expérimentale de Visual Studio.

2. Dans l’instance expérimentale, accédez au menu **Outils** , puis cliquez sur **extensions et mises à jour..**.. L’extension TestPublish doit apparaître dans le volet central et être activée.

3. Dans le menu **Outils** , vérifiez que vous voyez la commande test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publier l’extension sur la place de marché via la ligne de commande

1. Assurez-vous que vous avez créé la version Release de votre extension et qu’elle est à jour.

2. Assurez-vous que vous avez créé publishmanifest.jsles fichiers et overview.md.

3. Ouvrez la ligne de commande et accédez au répertoire $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\.

4. Pour créer un serveur de publication, utilisez la commande suivante :

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Au terme de la création du serveur de publication, le message de ligne de commande suivant s’affiche :

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Vous pouvez vérifier le nouveau serveur de publication que vous avez créé en accédant à [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Pour publier une nouvelle extension, utilisez la commande suivante :

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Au terme de la création du serveur de publication, le message de ligne de commande suivant s’affiche :

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Vous pouvez vérifier la nouvelle extension que vous avez publiée en accédant à [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installer l’extension à partir de la Visual Studio Marketplace

Maintenant que l’extension est publiée, installez-la dans Visual Studio et testez-la ici.

1. Dans Visual Studio, dans le menu **Outils** , cliquez sur **extensions et mises à jour...**.

2. Cliquez sur **en ligne** , puis recherchez TestPublish.

3. Cliquez sur **Télécharger**. L’extension sera alors planifiée pour l’installation.

4. Pour terminer l’installation, fermez toutes les instances de Visual Studio.

## <a name="remove-the-extension"></a>Supprimer l’extension

Vous pouvez supprimer l’extension de la Visual Studio Marketplace et de votre ordinateur.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Pour supprimer l’extension de la place de marché via la ligne de commande

1. Si vous souhaitez supprimer une extension, utilisez la commande suivante :

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. En cas de suppression réussie de l’extension, le message de ligne de commande suivant s’affiche :

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension de votre ordinateur

1. Dans Visual Studio, dans le menu **Outils** , cliquez sur **extensions et mises à jour**.

2. Sélectionnez « MyVsixExtension », puis cliquez sur **désinstaller**. La désinstallation de l’extension sera alors planifiée.

3. Pour terminer la désinstallation, fermez toutes les instances de Visual Studio.
