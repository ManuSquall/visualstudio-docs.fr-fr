---
title: Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio
description: Découvrez comment appliquer des clés de produit par programmation quand vous déployez Visual Studio.
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fea2ffa8fd81a5012c89289df36d7f698fb60c4e
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138714"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio

Vous pouvez appliquer votre clé de produit par programmation dans le cadre du script qui est utilisé pour automatiser le déploiement de Visual Studio. Vous pouvez définir par programmation une clé de produit sur un appareil, au choix pendant une installation de Visual Studio ou au terme de l’installation.

## <a name="apply-the-license-after-installation"></a>Appliquer la licence après l’installation

 Vous pouvez, en mode silencieux, activer une version installée de Visual Studio avec une clé de produit par l’intermédiaire de l’utilitaire `StorePID.exe` sur les ordinateurs cibles. `StorePID.exe` est un programme utilitaire qui s’installe avec Visual Studio 2017 à l’emplacement par défaut suivant : <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Exécutez `StorePID.exe` avec des privilèges élevés, à l’aide d’un agent System Center ou par l’intermédiaire d’une invite de commandes avec élévation de privilèges. Faites suivre de la clé de produit et du MPC (code produit Microsoft).

>[!IMPORTANT]
> Assurez-vous de bien inclure les tirets de la clé de produit.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

 L’exemple suivant montre une ligne de commande servant à appliquer la licence pour Visual Studio 2017 Enterprise, avec un code MPC de 08860, une clé de produit `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` et qui suppose un emplacement d’installation par défaut :

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 Le tableau suivant répertorie les codes MPC pour chaque édition de Visual Studio :

| Édition de Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](../install/install-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
