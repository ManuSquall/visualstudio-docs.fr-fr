---
title: Supprimer Visual Studio
titleSuffix: ''
description: Découvrez comment supprimer complètement Visual Studio de votre ordinateur, étape par étape.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b0e8c8fe10451e9e5906eabf7f4f65086d147904
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113712"
---
# <a name="remove-visual-studio"></a>Supprimer Visual Studio

Si vous rencontrez une erreur catastrophique et que vous ne pouvez pas réparer ou désinstaller Visual Studio, vous pouvez exécuter l’outil `InstallCleanup.exe` pour supprimer les fichiers d’installation et les informations sur les produits pour toutes les instances installées de Visual Studio 2017 ou Visual Studio 2019.

> [!WARNING]
> Utilisez l’outil InstallCleanup **uniquement en dernier recours en cas d'** échec de la réparation ou de la désinstallation. Cet outil peut désinstaller des fonctionnalités d’autres installations de Visual Studio ou d’autres produits, qui peuvent être également nécessaires à la réparation ou à la réinstallation.

## <a name="run-installcleanupexe"></a>Exécuter InstallCleanup. exe

Vous pouvez utiliser l’un des commutateurs de ligne de commande suivants avec l’outil `InstallCleanup.exe` :

| Basculer | Comportement |
| ------ | -------- |
| `-i`   | Ce commutateur est la valeur par défaut si aucun autre commutateur n’est passé. Il supprime uniquement le répertoire d’installation principal et les informations sur le produit. Utilisez ce commutateur si vous envisagez de réinstaller la même version de Visual Studio après avoir exécuté l’outil `InstallCleanup.exe`. |
| `-f`   | Ce commutateur supprime le répertoire d’installation principal, les informations sur le produit et la plupart des autres fonctionnalités installées en dehors du répertoire d’installation, qui peuvent également être partagées avec d’autres installations de Visual Studio ou d’autres produits. Utilisez ce commutateur si vous envisagez de supprimer Visual Studio sans le réinstaller ultérieurement. |

Voici comment exécuter l’outil `InstallCleanup.exe` :

1. Fermez le programme d’installation de Visual Studio.
1. Ouvrez une invite de commandes administrateur. Pour ouvrir une invite de commandes administrateur, suivez les étapes ci-dessous :
   * Tapez **cmd** dans la zone « Tapez ici pour effectuer une recherche ».
   * Cliquez avec le bouton droit sur **Invite de commandes**, puis sélectionnez **Exécuter en tant qu’administrateur**.
1. Entrez le chemin d’accès complet de l’outil de `InstallCleanup.exe` et ajoutez le commutateur de ligne de commande que vous préférez. Par défaut, le chemin d’accès de l’outil est le suivant :

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > Si vous ne trouvez pas `InstallCleanup.exe` dans le répertoire Visual Studio Installer, qui se trouve toujours dans `%ProgramFiles(x86)%\Microsoft Visual Studio`, voici ce que vous devez faire ensuite. Suivez les instructions pour [installer Visual Studio](install-visual-studio.md). Ensuite, lorsque l’écran de sélection de la charge de travail s’affiche, fermez la fenêtre et suivez à nouveau les étapes de cette page.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Mettre à jour Visual Studio](update-visual-studio.md)
* [Modifier Visual Studio](modify-visual-studio.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
