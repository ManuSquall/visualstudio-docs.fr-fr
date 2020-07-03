---
title: Prise en main avec le modèle de projet VSIX | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ca9672b22120718f63638d8668812d0e42e41f
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905882"
---
# <a name="get-started-with-the-vsix-project-template"></a>Prise en main du modèle de projet VSIX

Vous pouvez utiliser le modèle de projet VSIX pour créer une extension ou pour empaqueter une extension existante en vue d’un déploiement. Le modèle de projet VSIX a à la fois des versions Visual Basic et Visual C#, et est installé dans le cadre du kit de développement logiciel (SDK) Visual Studio.

 Le modèle de projet VSIX se compose juste d’un fichier *. extension. vsixmanifest source* , qui contient des informations sur l’extension et les ressources qu’elle envoie.

 Pour rechercher le modèle de projet VSIX, vous devez installer le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Déployer un modèle de projet personnalisé à l’aide du modèle de projet VSIX

 Les étapes suivantes montrent comment utiliser le projet VSIX pour empaqueter un modèle de projet que vous pouvez partager avec d’autres développeurs ou télécharger dans la Galerie Visual Studio.

1. Créez un modèle de projet.

    1. Ouvrez le projet à partir duquel créer un modèle. Ce projet peut être de n’importe quel type de projet.

    2. Dans le menu **Projet**, cliquez sur **Exporter le modèle**. Effectuez les étapes de l’Assistant.

         Un fichier *. zip* est créé dans *%UserProfile%\My Documents\Visual Studio {version} \Mes \\ *Exported Templates.

2. Créez un projet VSIX vide.

     Sélectionnez **Fichier** > **Nouveau** > **Projet**. Dans la zone de recherche, tapez « VSIX », puis sélectionnez la version **C#** ou **Visual Basic** du **projet VSIX**.

3. Ajoutez le fichier *. zip* au projet. Affectez à la propriété **copier dans le répertoire de sortie** la valeur `Copy Always` .

4. Dans **Explorateur de solutions**, double-cliquez sur le fichier *source. extension. vsixmanifest* pour l’ouvrir dans le **Concepteur de manifeste VSIX**, puis apportez les modifications suivantes :

    - Définissez le champ **nom du produit** sur **mon modèle de projet**.

    - Définissez le champ **Product ID** sur **MyProjectTemplate-1**.

    - Définissez le champ **auteur** sur **Fabrikam**.

    - Définissez le champ **Description** sur **mon modèle de projet**.

    - Dans la section **ressources** , ajoutez un type **Microsoft. VisualStudio. ProjectTemplate** et définissez son chemin d’accès sur le nom du fichier *. zip* .

5. Enregistrez et fermez le fichier *source. extension. vsixmanifest* .

6. Créez le projet.

7. Dans le répertoire de sortie, double-cliquez sur le fichier *. vsix* .

8. Une boîte de message du **programme d’installation VSIX** s’affiche. Suivez les instructions pour installer l’extension.

9. Fermez Visual Studio, puis rouvrez-le.

::: moniker range="vs-2017"

10. Sélectionnez **extensions et mises à jour** (dans le menu **Outils** ) et sélectionnez la catégorie **modèles** . L’une des extensions disponibles doit être **mon modèle de projet**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Sélectionnez **gérer les extensions** (dans le menu **Extensions** ) et sélectionnez la catégorie **modèles** . L’une des extensions disponibles doit être **mon modèle de projet**.

::: moniker-end

11. Le nouveau modèle de projet s’affiche dans la boîte de dialogue **nouveau projet** au même emplacement que le modèle de projet d’origine. Par exemple, si vous avez créé un modèle nommé **console VB** à partir d’une application console Visual Basic, la **console VB** apparaît dans le même volet que le modèle **application console** Visual Basic.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Pour spécifier l’emplacement du modèle dans la boîte de dialogue Nouveau projet

1. Les dossiers de modèles se trouvent dans les répertoires *{chemin d’installation de Visual Studio} \Common7\IDE\ProjectTemplates* et *{chemin d’installation de Visual Studio} \Common7\IDE\ItemTemplates* . Les noms des sections de niveau supérieur dans la boîte de dialogue **nouveau projet** ne correspondent pas exactement aux noms des dossiers de modèles. À l’endroit où ils diffèrent, utilisez le nom du dossier de modèles.

    Remplacez l’extension de fichier *. vsix* par *. zip*, puis ouvrez le fichier.

2. Créez un nouveau dossier portant le même nom que la section de la boîte de dialogue **nouveau projet** . le modèle doit apparaître dans.

3. Si le modèle doit apparaître dans une sous-section, créez un sous-dossier du même nom.

4. Déplacez le fichier template *. zip* dans le nouveau dossier.

5. Remplacez l’extension *. zip* par *. vsix*.

6. Ouvrez le manifeste VSIX.

7. Dans le manifeste VSIX, mettez à jour le chemin d’accès de l' **élément** multimédia du modèle afin qu’il pointe vers la racine de l’arborescence de répertoires qui contient le fichier de modèle. Par exemple, si le modèle se trouve dans *\CSharp\Windows*, la référence doit pointer vers *\CSharp*.
