---
title: Création de modèles de projet et d’élément personnalisés
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e04ca6afaa8e5a290e6c2a3419bb4fa28fd46e6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952056"
---
# <a name="creating-custom-project-and-item-templates"></a>Création de modèles de projet et d’élément personnalisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le SDK Visual Studio inclut des modèles de projet de créer un modèle de projet personnalisé et un modèle d’élément personnalisé. Ces modèles incluent des substitutions de paramètre commun et générer en tant que fichiers zip. Ils ne sont pas automatiquement déployés, et ils ne sont pas disponibles dans l’instance expérimentale. Copiez le fichier zip de fichiers à l’emplacement vous

Les modèles de création de modèle vous permettent d’inclure des modèles dans des extensions plus volumineuses. Y compris les modèles dans les extensions vous permet d’implémenter le contrôle de version dans les fichiers source et de créer un groupe de projets de modèle dans un package VSIX.

Pour les scénarios de création de modèle de base, vous devez utiliser le **Export Template** Assistant, qui envoie le résultat vers un fichier compressé. Pour plus d’informations sur la création de modèle de base, consultez [création de projet et modèles d’élément](../ide/creating-project-and-item-templates.md).

À partir de Visual Studio 2017, la recherche de projet personnalisé et les modèles d’élément n’est plus effectuée. Au lieu de cela, l’extension doit fournir les fichiers de manifeste de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser l’installation de Preview 2 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un fichier MSI, vous devez générer manuellement les fichiers manifeste de modèle. Pour plus d’informations, consultez [mettre à niveau un projet personnalisé et des modèles d’élément pour Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Le schéma de manifeste de modèle est documenté dans [référence modèle Visual Studio Manifest schéma](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="create-a-project-template"></a>Créer un modèle de projet

1.  Créez un projet de modèle de projet. Vous pouvez trouver le modèle de projet dans le **nouveau projet** boîte de dialogue, dans Visual Basic ou Visual c# **extensibilité** dossier.

     Le modèle génère un fichier de classe, une icône, un fichier .vstemplate, un fichier de projet modifiable nommé ProjectTemplate.vbproj ou ProjectTemplate.csproj et certains fichiers qui sont généralement générés par d’autres types de projet, un tel fichier resources.resx, un AssemblyInfo fichier et un fichier .settings. Chaque fichier de code contient des substitutions de paramètre commun le cas échéant.

2.  Ajouter et supprimer des éléments à partir du projet en fonction des besoins de votre projet. Ne supprimez pas le fichier projet modifiable, le fichier AssemblyInfo ou le fichier .vstemplate.

3.  Mettre à jour le fichier .vstemplate pour refléter les ajouts et les suppressions. Le [projet](../extensibility/project-element-visual-studio-templates.md) élément doit contenir un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) élément pour chaque fichier à inclure dans le modèle.

4.  Modifier vos fichiers de code et d’autres contenus visibles par l’utilisateur et ajoutez des substitutions de paramètre appropriée.

5.  Modifier le contenu généré en fonction des besoins.

6.  Générez le projet.

     Visual Studio crée un fichier .zip qui contient votre modèle. Il n’est pas déployée, et il n’est pas disponible dans l’instance expérimentale.

## <a name="create-an-item-template"></a>Créer un modèle d’élément

1.  Créer un projet de modèle d’élément.

     Le modèle génère un fichier de classe, un icône, un fichier .vstemplate et un fichier AssemblyInfo. Le fichier de classe contient des substitutions de paramètre commun.

2.  Ajouter et supprimer des éléments à partir du projet en fonction des besoins de votre projet.

3.  Mettre à jour le fichier .vstemplate pour refléter les ajouts et les suppressions. Le [projet](../extensibility/project-element-visual-studio-templates.md) élément doit contenir un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) élément pour chaque fichier à inclure dans le modèle.

4.  Modifier vos fichiers de code et d’autres contenus visibles par l’utilisateur et ajoutez des substitutions de paramètre appropriée.

5.  Modifier le contenu généré en fonction des besoins.

6.  Générez le projet.

     Visual Studio crée un fichier compressé qui contient votre modèle. Il n’est pas déployée, et il n’est pas disponible dans l’instance expérimentale.

## <a name="deploy-the-project-or-item-template"></a>Déployer le modèle de projet ou un élément

1.  Créez un projet VSIX. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).

2.  Définissez le projet VSIX comme projet de démarrage. Dans le **l’Explorateur de solutions**, sélectionnez le nœud du projet VSIX, avec le bouton droit, puis sélectionnez **définir comme projet de démarrage**.

3.  Définissez le projet de modèle de projet en tant qu’actif du projet VSIX. Ouvrez le fichier .vsixmanifest. Accédez à la **actifs** onglet et cliquez sur **New**.

    1.  Définir le **Type** champ **Microsoft.VisualStudio.ProjectTemplate** ou **Microsoft.VisualStudio.ItemTemplate**.

    2.  Pour la source, sélectionnez le **un projet dans la solution actuelle** option, puis sélectionnez le projet qui contient votre modèle.

4.  Générez la solution, puis appuyez sur F5. L’instance expérimentale s’affiche.

5.  Pour un projet de modèle de projet, vous devez voir votre modèle de projet répertorié dans le **nouveau projet** boîte de dialogue (**fichier / nouveau / projet**), dans le nœud Visual Basic ou Visual c#. Pour un projet de modèle d’élément, vous devez voir votre modèle d’élément répertoriée dans la boîte de dialogue Ajouter un nouvel élément (dans le **l’Explorateur de solutions**, sélectionnez le nœud du projet, puis cliquez sur **Ajouter / nouvel élément**).

## <a name="see-also"></a>Voir aussi

- [Référence de modèles Visual Studio](../ide/visual-studio-template-reference.md)