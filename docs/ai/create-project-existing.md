---
title: Créer un projet AI à partir d’un code existant
description: Découvrez comment utiliser Visual Studio Tools for AI pour intégrer du code python existant dans un projet Visual Studio.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 7746d8dd39bb4400a7779ad43e489cf6e7475fb9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841625"
---
# <a name="create-an-ai-project-from-existing-code"></a>Créer un projet AI à partir d’un code existant

Une fois que vous avez [installé Visual Studio Tools pour AI](installation.md), il est facile de placer du code Python existant dans un projet Visual Studio.

> [!Important]
> Le processus décrit ici ne déplace pas ou ne copie pas les fichiers sources d’origine. Si vous voulez travailler avec une copie, dupliquez d’abord le dossier.

1. Lancez Visual Studio et sélectionnez **Fichier > Nouveau > Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, recherchez « **AI Tools** », sélectionnez le modèle « **À partir de code Python existant** », spécifiez un nom et un emplacement pour le projet, puis sélectionnez **OK**.

   ![Nouveau projet à partir du code existant, étape 1](media/create-project-existing/new-ai-project.png)

3. Dans l’Assistant qui apparaît, définissez le chemin de votre code existant, un filtre pour les types de fichiers et les chemins de recherche nécessaires à votre projet, puis sélectionnez **OK**. Si vous ne savez pas ce que sont les chemins de recherche, laissez ce champ vide.

   ![Nouveau projet à partir du code existant, étape 2](media/create-project-existing/azurebatch-newproject.png)

   Si votre code existant fait partie d’un projet Azure Machine Learning, cochez la case **Est un dossier Azure Machine Learning** pour garantir la réussite de la conversion des détails de configuration Azure Machine Learning importants comme le compte Expérimentation, l’espace de travail, les contextes de calcul à utiliser, et bien plus encore.

4. Pour définir un fichier de démarrage, localisez le fichier dans **l’Explorateur de solutions**, cliquez avec le bouton droit, puis sélectionnez **Définir comme fichier de démarrage**.

5. Exécutez le programme en appuyant sur **CTRL** + **F5** ou en sélectionnant **Déboguer > exécuter sans débogage**.

> [!div class="nextstepaction"]
> [Didacticiel : Utilisation de Python dans Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Voir aussi

- [Identifier manuellement un environnement Python existant](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
