---
title: "Automatiser l’installation de Visual Studio avec un fichier réponse | Microsoft Docs"
description: "{{ESPACE RÉSERVÉ}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 448C738E-121F-4B64-8CA8-3BC997817A14
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: c77f0321e50a27635e083d656cf6ba8011a4ef4d
ms.contentlocale: fr-fr
ms.lasthandoff: 05/11/2017

---
# <a name="how-to-define-settings-in-a-response-file"></a>Guide pratique pour définir des paramètres dans un fichier réponse
Les administrateurs qui déploient Visual Studio peuvent spécifier un fichier réponse en utilisant le paramètre `--in`, par exemple :

```
vs_enterprise.exe --in customInstall.json
```

Les fichiers réponse sont des fichiers [JSON](http://json-schema.org/) dont le contenu reflète les arguments de la ligne de commande.  En général, si un paramètre de ligne de commande n’accepte aucun argument (par exemple, `--quiet`, `--passive`, etc.), la valeur dans le fichier réponse doit être true/false.  S’il accepte un argument (par exemple, `--installPath <dir>`), la valeur dans le fichier réponse doit être une chaîne.  S’il accepte un argument et peut apparaître plusieurs fois sur la ligne de commande (par exemple, `--add <id>`), la valeur doit être un tableau de chaînes.

Les paramètres spécifiés sur la ligne de commande remplacent les paramètres du fichier réponse, sauf dans le cas des paramètres qui acceptent plusieurs entrées (par exemple, `--add`), où les entrées fournies sur la ligne de commande sont fusionnées avec les paramètres du fichier réponse.

# <a name="setting-a-default-configuration-for-visual-studio"></a>Définition d’une configuration par défaut pour Visual Studio

Si vous avez créé un cache de disposition réseau avec `--layout`, un fichier `response.json` est créé dans la disposition.

Les administrateurs qui créent une disposition peuvent modifier le fichier `response.json` dans la disposition pour contrôler les paramètres par défaut que les utilisateurs verront lors de l’installation de Visual Studio à partir de la disposition.  Par exemple, si un administrateur souhaite que des charges de travail spécifiques et des composants sélectionnés soient installés par défaut, il peut configurer le fichier `response.json` pour les ajouter.

Quand le programme d’installation de Visual Studio est exécuté à partir d’un dossier de disposition, il utilise _automatiquement_ le fichier réponse dans le dossier de disposition.  Il n’est pas obligatoire d’utiliser l’option `--in`.

Vous pouvez mettre à jour le fichier `response.json` qui est créé dans un dossier de disposition en mode hors connexion pour définir le paramètre par défaut pour les utilisateurs qui procèdent à l’installation à partir de cette disposition. **Toutefois, il est essentiel de conserver les propriétés existantes qui ont été définies lors de la création de la disposition.**

Le fichier `response.json` de base dans une disposition ressemble à ceci, mais avec une valeur pour le produit et le canal que vous installez :

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

## <a name="example-layout-response-file-content"></a>Exemple de contenu de fichier réponse dans la disposition
Cet exemple installe Visual Studio Enterprise avec six charges de travail et composants courants, ainsi que les langues d’interface utilisateur Anglais et Français. Vous pouvez l’utiliser comme modèle : il vous suffit de remplacer les charges de travail et composants par ceux que vous voulez installer.

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
## <a name="see-also"></a>Voir aussi
* [ID de charge de travail et de composant Visual Studio 2017](workload-and-component-ids.md)

