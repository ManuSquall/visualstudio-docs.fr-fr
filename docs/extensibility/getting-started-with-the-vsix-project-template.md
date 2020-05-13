---
title: Démarrer avec le modèle de projet VSIX (fr) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711248"
---
# <a name="get-started-with-the-vsix-project-template"></a>Démarrez avec le modèle du projet VSIX

Vous pouvez utiliser le modèle de projet VSIX pour créer une extension ou pour emballer une extension existante pour le déploiement. Le modèle de projet VSIX a à la fois Visual Basic et Visual C versions, et est installé dans le cadre du Studio visuel SDK.

 Le modèle de projet VSIX se compose simplement d’un fichier *source.extension.vsixmanifest,* qui contient des informations sur l’extension et les actifs qu’il expédie.

 Pour trouver le modèle de projet VSIX, vous devez installer le Visual Studio SDK. Pour plus d’informations, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Déployer un modèle de projet personnalisé à l’aide du modèle de projet VSIX

 Les étapes suivantes montrent comment utiliser le projet VSIX pour emballer un modèle de projet que vous pouvez partager avec d’autres développeurs ou télécharger à la Visual Studio Gallery.

1. Créez un modèle de projet.

    1. Ouvrez le projet à partir duquel créer un modèle. Ce projet peut être de n’importe quel type de projet.

    2. Dans le menu **Projet**, cliquez sur **Exporter le modèle**. Complétez les étapes de l’assistant.

         Un fichier *.zip* est créé en *%USERPROFILE% -Mes Documents-Visual\\Studio 'version'-My Exported Templates*.

2. Créez un projet VSIX vide.

     Sélectionnez **File** > **New** > **Project**. Dans la boîte de recherche, tapez «vsix» et sélectionnez la version **C ou** **Visual Basic** du **projet VSIX**.

3. Ajoutez le fichier *.zip* au projet. Définissez sa copie à `Copy Always`la propriété **d’annuaire de sortie** à .

4. Dans **Solution Explorer**, double-cliquez sur le fichier *source.extension.vsixmanifest* pour l’ouvrir dans le concepteur de manifeste **VSIX**, puis effectuer les modifications suivantes:

    - Définissez le champ **de nom de produit** à mon modèle de **projet**.

    - Réglez le champ **d’identification** du produit sur **MyProjectTemplate - 1**.

    - Définissez le champ **d’auteur** à **Fabrikam**.

    - Définissez le champ **de description** sur mon modèle **de projet**.

    - Dans la section **Actifs,** ajoutez un type **Microsoft.VisualStudio.ProjectTemplate** et définissez son chemin vers le nom du fichier *.zip.*

5. Enregistrer et fermer le fichier *source.extension.vsixmanifest.*

6. Créez le projet.

7. Dans l’annuaire de sortie, cliquez double sur le fichier *.vsix.*

8. Une boîte de message **VSIX Installateur** apparaît. Suivez les instructions pour installer l’extension.

9. Fermez Visual Studio, puis rouvrez-le.

::: moniker range="vs-2017"

10. Sélectionnez **les extensions et les mises à jour** (sur le menu **Tools)** et sélectionnez la catégorie **Templates.** L’une des extensions disponibles devrait être **Mon modèle de projet**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Sélectionnez **Manage Extensions** (sur le menu **Extensions)** et sélectionnez la catégorie **Templates.** L’une des extensions disponibles devrait être **Mon modèle de projet**.

::: moniker-end

11. Le nouveau modèle de projet apparaît dans le dialogue **du nouveau projet** au même endroit que le modèle de projet original. Par exemple, si vous avez créé un modèle nommé **console VB** à partir d’une application de console de base visuelle, **VB Console** apparaît dans le même volet que le modèle **d’application** de console de base visuelle.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Pour spécifier l’emplacement du modèle dans la boîte de dialogue du nouveau projet

1. Les dossiers de gabarit sont situés dans les *répertoires « Visual Studio Installation Path »* et « Visual Studio Installation Path *»* Les noms des sections de haut niveau du dialogue **New Project** ne correspondent pas exactement aux noms des dossiers de modèle. Lorsqu’ils diffèrent, utilisez le nom du dossier de modèle.

    Modifier l’extension de fichier *.vsix* à *.zip*, puis ouvrir le fichier.

2. Créez un nouveau dossier du même nom que la section du dialogue **du nouveau projet** dans laquelle le modèle doit apparaître.

3. Si le modèle doit apparaître dans un sous-section, créez un sous-pli du même nom.

4. Déplacez le fichier *.zip* modèle dans le nouveau dossier.

5. Modifier l’extension *.zip* à *.vsix*.

6. Ouvrez le manifeste VSIX.

7. Dans le manifeste VSIX, mettre à jour la trajectoire **d’actif** du modèle afin qu’il indique la racine de l’arbre d’annuaire qui contient le fichier de modèle. Par exemple, si le modèle est dans *'CSharp’Windows*, la référence doit indiquer *à CSharp*.
