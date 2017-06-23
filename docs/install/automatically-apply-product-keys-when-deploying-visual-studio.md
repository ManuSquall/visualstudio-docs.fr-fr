---
title: "Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 493ea235a3d89a04a4c6accfa491e622792e4397
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio
Vous pouvez appliquer votre clé de produit par programmation dans le cadre du script utilisé pour automatiser le déploiement de Visual Studio. Les clés de produit peuvent être définies sur un appareil par programmation pendant l'installation de Visual Studio ou au terme d'une installation.

## <a name="apply-the-license-after-installation"></a>Appliquer la licence après l’installation
 Vous pouvez activer une version installée de Visual Studio avec une clé de produit à l’aide de l’utilitaire `StorePID.exe` sur les ordinateurs cibles en mode silencieux. `StorePID.exe` est un programme utilitaire qui s’installe avec Visual Studio 2017 à l’emplacement par défaut suivant : <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Exécutez `StorePID.exe` avec des privilèges élevés à l’aide d’un agent System Center ou d’une invite de commandes avec élévation de privilèges. Tapez ensuite la clé de produit (en incluant les tirets) et le code de produit Microsoft (MPC). Veillez à inclure les tirets de la clé de produit.

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 Voici un exemple de ligne de commande visant à appliquer la licence pour Visual Studio 2017 Enterprise, qui a un code MPC de 08860, avec une clé de produit `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, en supposant une installation à un emplacement par défaut :

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 Le tableau suivant répertorie les codes MPC pour chaque édition de Visual Studio :

| Édition de Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Si `StorePID.exe` a correctement appliqué la clé de produit, la valeur 0 est retournée pour `%ERRORLEVEL%`. En cas d’erreurs, il retourne un code en fonction de la condition d’erreur :

| Erreur                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="see-also"></a>Voir aussi
 * [Installer Visual Studio](../install/install-visual-studio.md)
 * [Créer une installation hors connexion de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)

