---
title: Automatiser l’installation avec un fichier réponse
description: Découvrez comment créer un fichier réponse JSON qui vous aide à automatiser l’installation de Visual Studio
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7554ac46d7c4171cfb71166c51689ff4ae95c0d5
ms.sourcegitcommit: a8031c1387d2090129ed33e063744f9f31653dcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2021
ms.locfileid: "110724549"
---
# <a name="automate-installs-by-using-settings-in-a-response-file"></a>Automatiser les installations à l’aide des paramètres d’un fichier réponse

Les administrateurs qui déploient Visual Studio peuvent spécifier un fichier réponse à l’aide du paramètre `--in`, comme dans l’exemple suivant :

```cmd
vs_enterprise.exe --in customInstall.json
```

Les fichiers réponse sont des fichiers [JSON](http://json-schema.org/) dont le contenu reflète les arguments de la ligne de commande.  En général, si un paramètre de ligne de commande n’accepte aucun argument (par exemple, `--quiet`, `--passive`, etc.), la valeur dans le fichier réponse doit être true/false.  S’il accepte un argument (par exemple, `--installPath <dir>`), la valeur dans le fichier réponse doit être une chaîne.  S’il accepte un argument et qu’il peut apparaître plusieurs fois sur la ligne de commande (par exemple, `--add <id>`), la valeur doit être un tableau de chaînes.

Les paramètres spécifiés sur la ligne de commande remplacent les paramètres du fichier réponse, sauf si les paramètres acceptent plusieurs entrées (par exemple, `--add`). Lorsque vous avez plusieurs entrées, les entrées fournies sur la ligne de commande sont fusionnées avec les paramètres contenus dans le fichier réponse.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Définition d’une configuration par défaut pour Visual Studio

Si vous avez créé un cache de disposition réseau avec `--layout`, un fichier `response.json` est créé dans la disposition. Si vous créez une disposition partielle, ce fichier réponse inclut les charges de travail et les langues qui étaient englobées dans la disposition.  L’exécution du programme d’installation à partir de cette disposition utilise automatiquement ce fichier response.json qui sélectionne les charges de travail et les composants inclus dans la disposition.  Les utilisateurs peuvent toujours sélectionner ou désélectionner toutes les charges de travail dans l’interface utilisateur du programme d’installation avant d’installer Visual Studio.

Les administrateurs qui créent une disposition peuvent modifier le fichier `response.json` dans la disposition pour contrôler les paramètres par défaut que les utilisateurs voient lorsqu’ils installent Visual Studio à partir de cette disposition.  Par exemple, si un administrateur souhaite que des composants et des charges de travail spécifiques soient installés par défaut, il peut configurer le fichier `response.json` pour les ajouter.

Quand le programme d’installation de Visual Studio est exécuté à partir d’un dossier de disposition, il utilise _automatiquement_ le fichier réponse dans le dossier de disposition.  Vous n’êtes pas obligé d’utiliser l’option `--in`.

Vous pouvez mettre à jour le fichier `response.json` qui est créé dans un dossier de disposition en mode hors connexion, afin de définir les paramètres par défaut des utilisateurs qui procèdent à l’installation à partir de cette disposition.

> [!WARNING]
> Il est primordial de conserver les propriétés existantes qui ont été définies lors de la création de la disposition.

Le fichier `response.json` de base dans une disposition doit ressembler à l’exemple suivant, à ceci près qu’il doit inclure la valeur du produit et du canal que vous souhaitez installer :

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

Lorsque vous créez ou mettez à jour une disposition, un fichier response.template.json est également créé.  Ce fichier contient tous les ID de charge de travail, de composant et de langue qu’il est possible d’utiliser.  Ce fichier est fourni en tant que modèle pour tout ce qui peut être inclus dans une installation personnalisée.  Les administrateurs peuvent utiliser ce fichier comme point de départ d’un fichier réponse personnalisé.  Supprimez simplement les ID des éléments que vous ne souhaitez pas installer et enregistrez-le dans votre propre fichier réponse.  Ne personnalisez pas le fichier response.template.json, sinon vos modifications sont perdues chaque fois que la disposition est mise à jour.

## <a name="example-layout-response-file-content"></a>Exemple de contenu de fichier réponse dans la disposition

L’exemple suivant installe Visual Studio Enterprise avec six charges de travail et composants courants, ainsi que les langues d’interface utilisateur Anglais et Français. Vous pouvez utiliser cet exemple comme modèle ; il vous suffit de remplacer les charges de travail et les composants par ceux que vous voulez installer :

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2019",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [ID de charge de travail et de composant Visual Studio](workload-and-component-ids.md)
* [Résoudre les erreurs liées au réseau lorsque vous installez ou utilisez Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
