---
title: Créer des modèles de projet
description: Découvrez comment utiliser l’Assistant exportation de modèle et d’autres méthodes pour créer des modèles de projet dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: a823d6a519da286e5c6df8947d64934a244c1985
ms.sourcegitcommit: 9c831a7f39e5b3e3c5db000b2545715bf12225f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105933769"
---
# <a name="how-to-create-project-templates"></a>Guide pratique pour créer des modèles de projet

Cette rubrique vous montre comment créer un modèle à l’aide de l’**Assistant Exportation de modèle**, qui crée un package de votre modèle sous forme de fichier *.zip*.

## <a name="use-the-export-template-wizard"></a>Utiliser l’Assistant Exportation de modèle

1. Crée un projet.

    > [!NOTE]
    > Utilisez uniquement des caractères d’identificateur valides lorsque vous nommez un projet qui sera la source d’un modèle. Sinon, des erreurs de compilation peuvent se produire dans les projets créés à partir du modèle. Pour plus d’informations sur les caractères d’identificateur valides, consultez [Noms d’éléments déclarés (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) ou [Identificateurs (C++)](/cpp/cpp/identifiers-cpp). Vous pouvez également utiliser les [Paramètres de modèle](../ide/template-parameters.md) afin d’employer des noms « sécurisés » pour les classes et les espaces de noms.

2. Modifiez le projet jusqu’à ce qu’il soit prêt à être exporté en tant que modèle. Par exemple, vous pouvez modifier des fichiers de code pour indiquer où le remplacement des paramètres doit avoir lieu. Consultez [Guide pratique pour substituer des paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md).

3. Dans le menu **projet** , choisissez **Exporter le modèle**.

   L’Assistant **Exportation de modèle** s’ouvre.

4. Dans la page **Choisir un type de modèle**, sélectionnez **Modèle de projet**. Sélectionnez le projet à exporter dans un modèle, puis choisissez **Suivant**.

::: moniker range="vs-2017"

5. Dans la page **Sélectionner les options du modèle**, entrez un nom et éventuellement une description, une icône et une image d’aperçu pour votre modèle. Ces éléments apparaissent dans la boîte de dialogue **Nouveau projet**. Cliquez sur **Terminer**.

   Le projet est exporté dans un fichier *.zip* et placé à l’emplacement de sortie spécifié. S’il est sélectionné, il est importé dans Visual Studio.

Pour rechercher votre modèle dans la boîte de dialogue **Nouveau projet**, développez **Installé**, puis développez la catégorie qui correspond à l’élément `ProjectType` dans le fichier *.vstemplate*. Par exemple, un fichier *.vstemplate* contenant `<ProjectType>CSharp</ProjectType>` apparaît sous **Installé** > **Visual C#**, par défaut. Vous pouvez organiser votre modèle dans un sous-répertoire du type de projet en créant simplement un dossier dans ce répertoire et en y plaçant le fichier *.zip* du modèle. Pour plus d’informations, consultez Guide pratique [pour localiser et organiser les modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. Dans la page **Sélectionner les options du modèle**, entrez un nom et éventuellement une description, une icône et une image d’aperçu pour votre modèle. Ces éléments apparaissent dans la boîte de dialogue où vous créez un projet. Cliquez sur **Terminer**.

   Le projet est exporté dans un fichier *.zip* et placé à l’emplacement de sortie spécifié. S’il est sélectionné, il est importé dans Visual Studio.

Pour rechercher votre modèle dans la boîte de dialogue où vous créez un projet, recherchez-le par son nom ou parcourez la liste. (Le filtrage basé sur le langage ou le type de projet n’est actuellement pas possible pour les modèles utilisateur.)

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Autres méthodes pour créer des modèles de projet

Vous pouvez créer des modèles de projet manuellement en rassemblant les fichiers qui constituent le projet dans un dossier, puis en créant un fichier XML *.vstemplate* avec les métadonnées appropriées. Pour plus d’informations, consultez [Guide pratique pour créer manuellement des modèles web](../ide/how-to-manually-create-web-templates.md).

Si le SDK Visual Studio est installé, vous pouvez inclure dans un wrapper le modèle fini, dans un fichier VSIX, pour le déployer en utilisant le modèle **Projet VSIX**. Pour plus d’informations, consultez [Bien démarrer avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Voir aussi

- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Comment : créer des modèles d’élément](../ide/how-to-create-item-templates.md)
- [Bien démarrer avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
- [Personnaliser des modèles de projet et d’élément](customizing-project-and-item-templates.md)
