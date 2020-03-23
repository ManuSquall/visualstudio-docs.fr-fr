---
ms.topic: include
ms.openlocfilehash: 47c390fbc7a6f84c25d4bde0317985bd149cae2f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68159602"
---
1. Lancez Visual Studio et sélectionnez **File** > **New** > **Project**.

1. Dans la boîte de dialogue **Nouveau projet**, recherchez « Python », sélectionnez le modèle **À partir de code Python existant**, spécifiez un nom et un emplacement pour le projet, puis sélectionnez **OK**.

1. Dans l’Assistant qui apparaît, définissez le chemin de votre code existant, un filtre pour les types de fichiers et les chemins de recherche nécessaires à votre projet, puis sélectionnez **Suivant**. Si vous ne savez pas ce que sont les chemins de recherche, laissez ce champ vide.

    ![Nouveau projet à partir du code existant, étape 1](../media/projects-from-existing-1.png)

1. Dans la boîte de dialogue suivante, sélectionnez le fichier de démarrage pour votre projet, puis sélectionnez **Suivant**. (Si vous le souhaitez, sélectionnez un environnement; acceptez autrement les défauts.) Notez que le dialogue n’affiche que des fichiers dans le dossier racine; si le fichier que vous voulez est dans un sous-pli, laissez le fichier de démarrage vide et définissez-le plus tard dans **Solution Explorer** (décrit ci-dessous).

    ![Nouveau projet à partir du code existant, étape 2](../media/projects-from-existing-2.png)

1. Sélectionnez l’emplacement auquel enregistrer le fichier projet (c’est-à-dire un fichier *.pyproj* sur le disque). Si c’est applicable, vous pouvez également inclure la détection automatique des environnements virtuels et personnaliser le projet pour différents frameworks web. Si vous n’êtes pas sûr de ces options, laissez-les avec leurs valeurs par défaut.

    ![Nouveau projet à partir du code existant, étape 3](../media/projects-from-existing-3.png)

1. Sélectionnez **Terminer** : Visual Studio crée alors le projet et l’ouvre dans **l’Explorateur de solutions**. Si vous souhaitez déplacer le fichier *.pyproj*, sélectionnez-le dans **l’Explorateur de solutions** et choisissez **Fichier** > **Enregistrer sous**. Cette action met à jour les références de fichiers dans le projet, mais ne déplace aucun fichier de code.

1. Pour définir un autre fichier de démarrage, localisez le fichier dans **l’Explorateur de solutions**, cliquez avec le bouton droit et sélectionnez **Définir comme fichier de démarrage**.