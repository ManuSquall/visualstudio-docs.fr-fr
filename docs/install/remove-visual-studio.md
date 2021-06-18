---
title: Supprimer Visual Studio
titleSuffix: ''
description: Découvrez comment supprimer complètement Visual Studio de votre ordinateur, étape par étape.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: how-to
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
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5af0cf31d3a53b12910ea8108c93a99cbaf3e87f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306954"
---
# <a name="remove-visual-studio"></a>Supprimer Visual Studio

Si vous rencontrez une erreur catastrophique et que vous ne pouvez pas réparer ou désinstaller Visual Studio, vous pouvez exécuter l' `InstallCleanup.exe` outil pour supprimer les fichiers d’installation et les informations sur les produits pour toutes les instances installées de Visual studio 2017, Visual studio 2019 ou Visual studio 2022.

> [!WARNING]
> Utilisez l’outil InstallCleanup **uniquement en dernier recours en cas d'** échec de la réparation ou de la désinstallation. Cet outil peut désinstaller des fonctionnalités d’autres installations de Visual Studio ou d’autres produits, qui peuvent être également nécessaires à la réparation ou à la réinstallation.

## <a name="run-installcleanupexe"></a>Exécuter InstallCleanup.exe

Vous pouvez utiliser l’un des commutateurs de ligne de commande suivants avec l' `InstallCleanup.exe` outil :

| Commutateur | Comportement                                                                                                                                                                                                                                                                                                                 |
|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-i`   | Ce commutateur est la valeur par défaut si aucun autre commutateur n’est passé. Il supprime uniquement le répertoire d’installation principal et les informations sur le produit. Utilisez ce commutateur si vous envisagez de réinstaller la même version de Visual Studio après l’exécution de l' `InstallCleanup.exe` outil.                                                              |
| `-f`   | Ce commutateur supprime le répertoire d’installation principal, les informations sur le produit et la plupart des autres fonctionnalités installées en dehors du répertoire d’installation, qui peuvent également être partagées avec d’autres installations de Visual Studio ou d’autres produits. Utilisez ce commutateur si vous envisagez de supprimer Visual Studio sans le réinstaller ultérieurement. |

Voici comment exécuter l' `InstallCleanup.exe` outil :

1. Fermez le programme d’installation de Visual Studio.
1. Ouvrez une invite de commandes d'administrateur. Pour ouvrir une invite de commandes administrateur, suivez les étapes ci-dessous :
   * Tapez **cmd** dans la zone « Tapez ici pour effectuer une recherche ».
   * Cliquez avec le bouton droit sur **Invite de commandes**, puis sélectionnez **Exécuter en tant qu’administrateur**.
1. Entrez le chemin d’accès complet de l' `InstallCleanup.exe` outil et ajoutez le commutateur de ligne de commande que vous préférez. Par défaut, le chemin d’accès de l’outil est le suivant. Les guillemets doubles entourent une commande contenant des espaces :

   ```shell
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Si vous ne trouvez pas `InstallCleanup.exe` dans le répertoire Visual Studio installer, qui se trouve toujours dans `%ProgramFiles(x86)%\Microsoft Visual Studio` , voici ce que vous devez faire ensuite. Suivez les instructions pour [installer Visual Studio](install-visual-studio.md). Ensuite, lorsque l’écran de sélection de la charge de travail s’affiche, fermez la fenêtre et suivez à nouveau les étapes de cette page.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Mettre à jour Visual Studio 2017](update-visual-studio.md)
* [Modifier Visual Studio 2017](modify-visual-studio.md)
* [Désinstaller Visual Studio](uninstall-visual-studio.md)
