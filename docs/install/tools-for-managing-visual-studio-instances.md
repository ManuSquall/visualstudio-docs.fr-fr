---
title: Outils de détection et de gestion des instances de Visual Studio
titleSuffix: ''
description: Découvrez les outils qui vous permettent de détecter et gérer les installations de Visual Studio sur les machines clientes.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 914449fe1db792614af1f9ed22464cb9fdb91481
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306889"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Outils de détection et de gestion des instances de Visual Studio

Il existe plusieurs outils que vous pouvez utiliser pour détecter les installations de Visual Studio sur les ordinateurs clients et pour gérer les installations.

## <a name="detecting-existing-visual-studio-instances"></a>Détection des instances existantes de Visual Studio

Les outils et utilitaires suivants vous aideront à détecter et à gérer les instances de Visual Studio installées sur les ordinateurs clients :

* [**vswhere**](https://github.com/microsoft/vswhere): fichier exécutable intégré à Visual Studio ou disponible pour une distribution distincte qui vous permet de trouver l’emplacement de toutes les instances de Visual Studio sur un ordinateur particulier.
* [**Vssetup. PowerShell**](https://github.com/microsoft/vssetup.powershell): scripts PowerShell qui utilisent l’API de configuration de l’installation pour identifier les instances installées de Visual Studio.
* [**Vs-Setup-Samples**](https://github.com/microsoft/vs-setup-samples): exemples C# et C++ qui montrent comment utiliser l’API de configuration du programme d’installation pour interroger une installation existante.
* [**Windows Management Instrumentation (WMI)**](/windows/win32/wmisdk/wmi-start-page): les informations de l’instance de Visual Studio peuvent être interrogées par le biais de la MSFT_VSInstance de la classe Visual Studio.
* L' [**API de configuration**](<xref:Microsoft.VisualStudio.Setup.Configuration>) de l’installation fournit des interfaces pour les développeurs qui souhaitent créer leurs propres utilitaires pour interroger des instances de Visual Studio.
* [**Inventaire logiciel des Configuration Manager de point de terminaison Microsoft**](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory): peut être utilisé pour collecter des informations sur les instances de Visual Studio sur des appareils clients.

## <a name="using-vswhereexe"></a>Utilisation de vswhere.exe

`vswhere.exe` est inclus automatiquement dans Visual Studio 2017 et versions ultérieures, ou vous pouvez le télécharger à partir de [la page des versions de vswhere](https://github.com/Microsoft/vswhere/releases). Utilisez `vswhere -?` pour obtenir des informations d’aide sur l’outil. Par exemple, cette commande affiche toutes les versions de Visual Studio, y compris les versions antérieures du produit et les versions préliminaires, et renvoie les résultats au format JSON :

```shell
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Utilisation de Windows Management Instrumentation (WMI)

Si l’utilitaire de détection du client Visual Studio est installé sur l’ordinateur, vous pouvez interroger les informations de l’instance Visual Studio à l’aide de WMI. L’utilitaire de détection du client Visual Studio est installé par défaut avec toutes les mises à jour Visual Studio 2017, Visual Studio 2019 et Visual Studio 2022 publiées le 12 mai ou après le 2020 12 mai. Il est également disponible sur le [catalogue Microsoft Update](https://catalog.update.microsoft.com/) si vous souhaitez l’installer indépendamment.  Pour obtenir un exemple d’utilisation de l’utilitaire pour retourner les informations de l’instance de Visual Studio, ouvrez PowerShell en tant qu’administrateur sur l’ordinateur client, puis tapez la commande suivante :

```shell
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Utilisation des Configuration Manager de point de terminaison Microsoft

Les fonctionnalités d' [inventaire logiciel de Microsoft Endpoint Configuration Manager](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) peuvent être utilisées pour interroger et collecter des informations sur les instances de Visual Studio sur les périphériques clients. Par exemple, la requête suivante retourne le nom complet, la version et le nom de l’appareil sur lequel Visual Studio est installé pour toutes les instances de Visual Studio 2017 et 2019 installées :

```WQL
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
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

1. Dans le menu principal de regedit, sélectionnez **fichier**  >  **charger la ruche...** , puis sélectionnez le fichier de Registre privé, qui est stocké dans le dossier **AppData\Local** . Exemple :

   ```shell
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` correspond à l’instance de Visual Studio que vous souhaitez parcourir.

Vous êtes invité à fournir un nom de ruche, qui devient le nom de votre ruche isolée. Après cela, vous devez être en mesure de parcourir le Registre sous la ruche isolée que vous avez créée.

> [!IMPORTANT]
> Avant de redémarrer Visual Studio, vous devez décharger la ruche isolée que vous avez créée. Pour ce faire, sélectionnez **fichier**  >  **décharger Hive** dans le menu principal de Regedit. (Si vous ne le faites pas, le fichier reste verrouillé et Visual Studio n’est pas en mesure de démarrer.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Guide de l’administrateur Visual Studio](../install/visual-studio-administrator-guide.md)
