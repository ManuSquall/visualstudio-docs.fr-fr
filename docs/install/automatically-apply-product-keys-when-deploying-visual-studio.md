---
title: Appliquer automatiquement des clés de produit
description: Découvrez comment appliquer des clés de produit par programmation quand vous déployez Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a78da89d8e8ce4251bc9288270628bfe784eca7a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307713"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio

Vous pouvez appliquer votre clé de produit par programmation dans le cadre du script qui est utilisé pour automatiser le déploiement de Visual Studio. Vous pouvez définir par programmation une clé de produit sur un appareil, au choix pendant une installation de Visual Studio ou au terme de l’installation.

::: moniker range=">=vs-2022"

> [!IMPORTANT]
> Visual Studio 2022 est actuellement en version préliminaire et, pendant la période d’évaluation, Visual Studio 2022 est disponible sous une licence d’évaluation qui ne nécessite pas l’application d’une clé de produit.

::: moniker-end

::: moniker range="vs-2017"

## <a name="apply-the-license-after-installation"></a>Appliquer la licence après l’installation

Vous pouvez, en mode silencieux, activer une version installée de Visual Studio avec une clé de produit par l’intermédiaire de l’utilitaire `StorePID.exe` sur les ordinateurs cibles. `StorePID.exe` est un programme utilitaire qui s’installe avec Visual Studio 2017 à l’emplacement par défaut suivant :

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE
```

 Exécutez `StorePID.exe` avec des privilèges élevés, à l’aide d’un agent System Center ou par l’intermédiaire d’une invite de commandes avec élévation de privilèges. Faites suivre de la clé de produit et du MPC (code produit Microsoft).

>[!IMPORTANT]
> Assurez-vous de bien inclure les tirets de la clé de produit.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2019"

## <a name="apply-the-license-after-installation"></a>Appliquer la licence après l’installation

Vous pouvez, en mode silencieux, activer une version installée de Visual Studio avec une clé de produit par l’intermédiaire de l’utilitaire `StorePID.exe` sur les ordinateurs cibles. `StorePID.exe` est un programme utilitaire qui s’installe avec Visual Studio 2019 à l’emplacement par défaut suivant :

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE
```

 Exécutez `StorePID.exe` avec des privilèges élevés, à l’aide d’un agent System Center ou par l’intermédiaire d’une invite de commandes avec élévation de privilèges. Faites suivre de la clé de produit et du MPC (code produit Microsoft).

>[!IMPORTANT]
> Assurez-vous de bien inclure les tirets de la clé de produit.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2017"

L’exemple suivant montre une ligne de commande servant à appliquer la licence pour Visual Studio 2017 Enterprise, avec un code MPC de 08860, une clé de produit `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` et qui suppose un emplacement d’installation par défaut :

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

L’exemple suivant montre une ligne de commande servant à appliquer la licence pour Visual Studio 2019 Enterprise, avec un code MPC de 09260, une clé de produit `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` et qui suppose un emplacement d’installation par défaut :

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 Le tableau suivant répertorie les codes MPC pour chaque édition de Visual Studio :

| Édition de Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Édition de Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

::: moniker range="vs-2017"

Si `StorePID.exe` a correctement appliqué la clé de produit, la valeur 0 est retournée pour `%ERRORLEVEL%`. En cas d’erreurs, il retourne un des codes suivant en fonction de la condition d’erreur :

| Error                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Quand vous exécutez une instance virtuelle de Visual Studio, assurez-vous également de virtualiser le dossier AppData Local et le registre. Pour résoudre les problèmes liés aux instances virtuelles, exécutez `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` .  

::: moniker-end

::: moniker range="vs-2019"

Si `StorePID.exe` a correctement appliqué la clé de produit, la valeur 0 est retournée pour `%ERRORLEVEL%`. En cas d’erreurs, il retourne un des codes suivant en fonction de la condition d’erreur :

| Error                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Quand vous exécutez une instance virtuelle de Visual Studio, assurez-vous également de virtualiser le dossier AppData Local et le registre. Pour résoudre les problèmes liés aux instances virtuelles, exécutez `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` .  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](../install/install-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)