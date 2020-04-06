---
title: Publier l’extension à l’aide de la ligne de commande
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697125"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Procédure pas à pas : Publication d’une extension Visual Studio via la ligne de commande

Cette procédure pas à pas vous montre comment publier une extension Visual Studio sur le Visual Studio Marketplace à l’aide de la ligne de commande. Lorsque vous ajoutez votre extension au Marketplace, les développeurs peuvent utiliser le dialogue [**Extensions et Mises à jour**](../ide/finding-and-using-visual-studio-extensions.md) pour y parcourir des extensions nouvelles et mises à jour.

VsixPublisher.exe est l’outil de ligne de commande pour la publication d’extensions Visual Studio sur le Marketplace. Il peut être consulté à partir de $VSInstallDirMD VSSDK-VisualStudioIntegration-Tools-Bin-VsixPublisher.exe. Commandes disponibles sur cet outil sont: **publier**, **createPublisher**, **deletePublisher**, **supprimerExtension**, **login**, **logout**.

## <a name="commands"></a>Commandes

### <a name="publish"></a>Publier

Publie une extension du marché. L’extension peut être un vsix, un fichier exe/msi, ou un lien. Si l’extension existe déjà avec la même version, elle remplacera l’extension. Si l’extension n’existe pas déjà, elle créera une nouvelle extension.

|Options de commande |Description |
|---------|---------|
|charge utile (nécessaire) | Soit un chemin vers la charge utile à publier ou un lien à utiliser comme "URL plus d’infos". |
|publierManifest (requis) | Chemin vers le fichier manifeste de publication à utiliser. |
|ignorerWarnings | Liste des avertissements à ignorer lors de la publication d’une prolongation. Ces avertissements sont affichés sous forme de messages de ligne de commande lors de la publication d’une extension. (par exemple, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Personal Access Token (PAT) qui est utilisé pour authentifier l’éditeur. Si elle n’est pas fournie, le PAT est acquis auprès des utilisateurs connectés. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Crée un éditeur sur le marché. Connecte également l’éditeur dans la machine pour des actions futures (par exemple, la suppression/ la publication d’une extension).

|Options de commande |Description |
|---------|---------|
|DisplayName (requis) | Afficher le nom de l’éditeur. |
|publisherName (requis) | Le nom de l’éditeur (par exemple, l’identifiant). |
|personalAccessToken (requis) | Un jeton d’accès personnel qui sert à authentifier l’éditeur. |
|courtedescription | Une courte description de l’éditeur (pas un fichier). |
|longue description | Une longue description de l’éditeur (pas un fichier). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>supprimerPublisher

Supprime un éditeur sur le Marché.

|Options de commande |Description |
|---------|---------|
|publisherName (requis) | Le nom de l’éditeur (par exemple, l’identifiant). |
|personalAccessToken (requis) | Un jeton d’accès personnel qui sert à authentifier l’éditeur. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>supprimerExtension

Supprime une extension du Marché.

|Options de commande |Description |
|---------|---------|
|extensionName (requis) | Le nom de l’extension à supprimer. |
|publisherName (requis) | Le nom de l’éditeur (par exemple, l’identifiant). |
|personalAccessToken | Un jeton d’accès personnel qui sert à authentifier l’éditeur. Si elle n’est pas fournie, la tape est acquise auprès des utilisateurs connectés. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Connecte un éditeur dans la machine.

|Options de commande |Description |
|---------|---------|
|personalAccessToken (requis | Un jeton d’accès personnel qui sert à authentifier l’éditeur. |
|publisherName (requis) | Le nom de l’éditeur (par exemple, l’identifiant). |
|overwrite | Précise que tout éditeur existant doit être écrasé avec le nouveau jeton d’accès personnel. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Enregistre un éditeur hors de la machine.

|Options de commande |Description |
|---------|---------|
|publisherName (requis) | Le nom de l’éditeur (par exemple, l’identifiant). |
|ignorerMissingPublisher | Précise que l’outil ne doit pas se tromper si l’éditeur spécifié n’est pas déjà connecté. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publier le fichierManifest

Un fichier PublishManifest est utilisé par la commande **de publication.** Il représente toutes les métadonnées sur l’extension que le marché doit savoir. Si l’extension téléchargée provient d’une extension VSIX, la propriété « identité » ne doit avoir que l’ensemble « InternalName ». C’est parce que le reste des propriétés "identité" peut être généré à partir du fichier vsixmanifest. Si l’extension est un msi/exe ou une extension de lien, l’utilisateur doit fournir les champs requis dans la propriété « d’identité ». Le reste du manifeste contient des informations spécifiques au marché (par exemple, catégories, si Q&A est activé, etc.).

L’extension VSIX publie l’échantillon de fichiers Dumanifest :

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

MSI/EXE ou LINK publient l’échantillon de fichiers Demanifest :

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

## <a name="asset-files"></a>Fichiers d’actifs

Des fichiers d’actifs peuvent être fournis pour intégrer des choses comme des images dans le fichier readme. Par exemple, si une extension a le document Markdown « aperçu » suivant :

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Afin de résoudre "images/testlogo.png" dans l’exemple précédent, un utilisateur peut fournir "assetFiles" dans leur manifeste de publication comme ci-dessous:

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

## <a name="publishing-walkthrough"></a>Publication pas à pas

### <a name="prerequisites"></a>Prérequis

Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Créer une extension Visual Studio

Dans ce cas, nous utiliserons une extension VSPackage par défaut, mais les mêmes étapes sont valables pour chaque type d’extension.

1. Créez un VSPackage en C nommé "TestPublish" qui a une commande de menu. Pour plus d’informations, voir [Créer votre première extension: Bonjour Monde](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Empaqueter votre extension

1. Mettre à jour l’extension vsixmanifest avec les informations correctes sur le nom du produit, l’auteur et la version.

   ![mise à jour de l’extension vsixmanifest](media/update-extension-vsixmanifest.png)

2. Construisez votre extension en mode **Version.** Maintenant, votre extension sera emballée comme un VSIX dans le dossier 'bin’Release.

3. Vous pouvez cliquer deux fois sur le VSIX pour vérifier l’installation.

### <a name="test-the-extension"></a>Testez l’extension

 Avant de distribuer l’extension, de la construire et de la tester pour vous assurer qu’elle est installée correctement dans l’instance expérimentale de Visual Studio.

1. Dans Visual Studio, commencez à débogage. d’ouvrir une instance expérimentale de Visual Studio.

2. Dans le cas expérimental, allez au menu **Tools** et cliquez sur **Extensions et Mises à jour...**. L’extension TestPublish doit apparaître dans le volet central et être activée.

3. Sur le menu **Tools,** assurez-vous de voir la commande de test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publier l’extension du Marché via la ligne de commande

1. Assurez-vous d’avoir construit la version Version Version de votre extension et qu’elle est à jour.

2. Assurez-vous d’avoir créé des fichiers publishmanifest.json et overview.md.

3. Ouvrez la ligne de commande et naviguez jusqu’à l’annuaire VSInstallDirMD VSSDK-VisualStudioIntegrationMD Tools-BinMD.

4. Pour créer un nouvel éditeur, utilisez la commande suivante :

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Lors de la création réussie de l’éditeur, vous verrez le message de ligne de commande suivant :

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Vous pouvez vérifier le nouvel éditeur que vous avez créé en naviguant vers [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Pour publier une nouvelle extension, utilisez la commande suivante :

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Lors de la création réussie de l’éditeur, vous verrez le message de ligne de commande suivant :

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Vous pouvez vérifier la nouvelle extension que vous avez publiée en naviguant vers [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installer l’extension à partir du marché visual Studio

Maintenant que l’extension est publiée, installez-la dans Visual Studio et testez-la là.

1. Dans Visual Studio, sur le menu **Tools,** cliquez sur **Extensions et Mises à jour...**.

2. Cliquez **en ligne,** puis recherchez TestPublish.

3. Cliquez sur **Télécharger**. L’extension sera alors prévue pour l’installation.

4. Pour compléter l’installation, fermez toutes les instances de Visual Studio.

## <a name="remove-the-extension"></a>Supprimer l’extension

Vous pouvez supprimer l’extension du Visual Studio Marketplace et de votre ordinateur.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Supprimer l’extension du Marketplace via la ligne de commande

1. Si vous souhaitez supprimer une extension, utilisez la commande suivante :

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Lors de la suppression réussie de l’extension, vous verrez le message suivant de la ligne de commande :

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Pour supprimer l’extension de votre ordinateur

1. Dans Visual Studio, sur le menu **Tools,** cliquez sur **Extensions et Mises à jour**.

2. Sélectionnez "MyVsixExtension" puis cliquez sur **Uninstall**. La prolongation sera alors prévue pour un désinstallation.

3. Pour compléter la désinstallation, fermez toutes les instances de Visual Studio.
