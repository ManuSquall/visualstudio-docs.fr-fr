---
title: Outils de détection et de gestion des instances de Visual Studio
titleSuffix: ''
description: Découvrez les outils qui vous permettent de détecter et gérer les installations de Visual Studio sur les machines clientes.
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 006a3fa3d41799a87449b8f9e111ca341a698bf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935410"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Outils de détection et de gestion des instances de Visual Studio

Il existe plusieurs outils qui vous permettent de détecter et gérer les installations de Visual Studio sur les machines clientes.

## <a name="detecting-existing-visual-studio-instances"></a>Détection des instances existantes de Visual Studio

Nous avons mis à disposition plusieurs outils qui vous aideront à détecter et à gérer les instances de Visual Studio installées sur les ordinateurs clients :

* [vswhere](https://github.com/microsoft/vswhere) : exécutable intégré à Visual Studio ou disponible dans le cadre d’une distribution distincte qui permet de trouver l’emplacement de toutes les instances de Visual Studio sur un ordinateur.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell) : Scripts PowerShell qui utilisent l’API de configuration de l’installation pour identifier les instances installées de Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples) : Exemples C# et C++ qui montrent comment utiliser l’API de configuration de l’installation pour interroger une installation existante.

De plus, l’[API de configuration de l’installation](<xref:Microsoft.VisualStudio.Setup.Configuration>) fournit des interfaces destinées aux développeurs qui veulent créer leurs propres utilitaires d’interrogation des instances de Visual Studio.

## <a name="using-vswhereexe"></a>Utilisation de vswhere.exe

`vswhere.exe` est automatiquement inclus dans Visual Studio (à compter de Visual Studio 2017 15.2 et versions ultérieures) ; vous pouvez sinon le télécharger sur la [page des versions de vswhere](https://github.com/Microsoft/vswhere/releases). Utilisez `vswhere -?` pour obtenir des informations d’aide sur l’outil. Par exemple, cette commande affiche toutes les versions de Visual Studio, y compris les anciennes versions du produit et les préversions, et retourne les résultats au format JSON :

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Pour plus d’informations sur l’installation de Visual Studio 2017, consultez les [archives d’installation de Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Modification du Registre pour une instance de Visual Studio

Dans Visual Studio, les paramètres du Registre sont stockés à un emplacement privé, ce qui permet d’avoir plusieurs instances côte à côte de la même version de Visual Studio sur la même machine.

Comme ces entrées ne sont pas stockées dans le Registre global, il existe des instructions spéciales pour l’utilisation de l’Éditeur du Registre afin d’apporter des modifications aux paramètres du Registre :

1. Si vous avez une instance de Visual Studio ouverte, fermez-la.

1. Démarrez `regedit.exe`.

1. Sélectionnez le nœud `HKEY_LOCAL_MACHINE`.

1. Dans le menu principal de Regedit, sélectionnez **Fichier** > **Charger la ruche...**, puis sélectionnez le fichier du Registre privé, qui est stocké dans le dossier **AppData\Local**. Par exemple :

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` correspond à l’instance de Visual Studio que vous souhaitez parcourir.

Vous êtes invité à fournir un nom de ruche, qui devient le nom de votre ruche isolée. Après cela, vous devez être en mesure de parcourir le Registre sous la ruche isolée que vous avez créée.

> [!IMPORTANT]
> Avant de redémarrer Visual Studio, vous devez décharger la ruche isolée que vous avez créée. Pour cela, sélectionnez **Fichier** > **Décharger la ruche** dans le menu principal de Regedit. (Si vous ne le faites pas, le fichier reste verrouillé et Visual Studio n’est pas en mesure de démarrer.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
