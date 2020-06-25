---
title: Créer un projet d’IA à partir d’un modèle
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: de0d2521f73da21ca7b6fc40edaecfadd5d703ed
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371558"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Créer un projet AI à partir d’un modèle dans Visual Studio

Une fois que vous avez [installé Visual Studio Tools pour AI](installation.md), vous pouvez facilement créer un projet AI à l’aide des divers modèles fournis.

1. Lancez Visual Studio.

2. Sélectionnez **Fichier > Nouveau > Projet** (Ctrl+Maj+N). Dans la boîte de dialogue **Nouveau projet**, recherchez **Tools pour AI** et sélectionnez le modèle souhaité. Notez que la sélection d’un modèle affiche une brève description de ce que le modèle fournit.

    ![Boîte de dialogue Nouveau projet de Visual Studio 2017 avec un modèle Python](media/create-project/new-ai-project.png)

3. Pour ce démarrage rapide, sélectionnez le modèle **Application TensorFlow**, attribuez un nom (par exemple, « MNIST ») et un emplacement au projet, puis sélectionnez **OK**.

4. Visual Studio crée le fichier projet (un fichier `.pyproj` sur le disque), ainsi que tous les autres fichiers décrits par le modèle. Avec le modèle « Application TensorFlow », le projet contient un seul fichier, du même nom que votre projet. Le fichier est ouvert dans l’éditeur Visual Studio par défaut.

    ![Projet résultant lors de l’utilisation du modèle Application Python](media/create-project/new-tensorflowapp.png)

5. Notez que le code importe déjà plusieurs bibliothèques, dont TensorFlow, numpy, sys et os. De plus, il démarre votre application avec certains arguments d’entrée prêts, ceci pour permettre le changement rapide de l’emplacement des données d’apprentissage d’entrée, des modèles de sortie et des fichiers journaux. Ces paramètres sont utiles quand vous envoyez des travaux à plusieurs contextes de calcul (à savoir un répertoire sur votre emplacement de développement local différent de celui sur un partage de fichiers Azure).

6. Votre projet a également certaines propriétés créées pour faciliter le débogage de votre application en passant automatiquement les arguments de ligne de commande à ces paramètres d’entrée. **Cliquez avec le bouton droit** sur votre projet, puis sélectionnez **Propriétés**

    ![Propriétés](media/create-project/project-properties.png)

7. Cliquez sur l’onglet **Déboguer** pour afficher les arguments de script automatiquement ajoutés. Vous pouvez les modifier si nécessaire, en fonction de l’emplacement où se trouvent vos données d’entrée et de l’emplacement où vous souhaitez stocker vos données de sortie.

    ![Propriétés](media/create-project//project-properties_1.png)

8. Exécutez le programme en appuyant sur Ctrl+F5 ou en sélectionnant **Déboguer > Démarrer sans débogage** dans le menu. Les résultats s’affichent dans une fenêtre de console.
