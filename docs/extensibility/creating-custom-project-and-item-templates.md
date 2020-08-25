---
title: Création de modèles de projet et d’élément personnalisés | Microsoft Docs
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb6bcd63896a11f9ca1eabddddc17b3e52865e5b
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801254"
---
# <a name="create-custom-project-and-item-templates"></a>Créer des modèles de projet et d’élément personnalisés

Le kit de développement logiciel (SDK) Visual Studio comprend des modèles de projet qui créent un modèle de projet personnalisé et un modèle d’élément personnalisé. Ces modèles incluent quelques substitutions de paramètres courants et sont générés en tant que fichiers zip. Ils ne sont pas déployés automatiquement et ne sont pas disponibles dans l’instance expérimentale. Vous devez copier le fichier zip généré dans le répertoire du modèle utilisateur.

Les modèles de création de modèle vous permettent d’inclure des modèles dans des extensions plus volumineuses. Cela vous permet d’implémenter le contrôle de version sur les fichiers sources et de générer un groupe de projets de modèle dans un package VSIX.

Vous pouvez également configurer un modèle pour installer les packages NuGet. Pour plus d’informations, consultez [packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Pour les scénarios de création de modèles de base, vous devez utiliser l’Assistant **exportation de modèle** , qui génère des sorties dans un fichier compressé. Pour plus d’informations sur la création de modèles de base, consultez [création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> À compter de Visual Studio 2017, l’analyse des modèles de projet et d’élément personnalisés ne sera plus effectuée. Au lieu de cela, l’extension doit fournir des fichiers manifestes de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un MSI, vous devez générer manuellement les fichiers manifeste de modèle. Pour plus d’informations, consultez [mise à niveau des modèles de projet et d’élément personnalisés pour Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Le schéma de manifeste de modèle est documenté dans [référence de schéma du manifeste de modèle Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Créer un modèle de projet

1. Créez un projet de modèle de projet. Vous pouvez trouver le modèle de projet dans la boîte de dialogue **nouveau projet** , en recherchant « modèle de projet » et en sélectionnant la version C# ou Visual Basic.

     Le modèle génère un fichier de classe, une icône, un fichier *. vstemplate* , un fichier projet modifiable nommé *ProjectTemplate. vbproj* ou *ProjectTemplate. csproj*, ainsi que certains fichiers qui sont généralement générés par d’autres types de projets, tels qu’un fichier *Resources. resx* , un fichier *AssemblyInfo* et un fichier *. Settings* . Chaque fichier de code contient des substitutions de paramètres communes, le cas échéant.

![sélection du projet de modèle de projet](media/project-template-selection.png)

2. Ajoutez et supprimez des éléments du projet selon les besoins de votre projet. Ne supprimez pas le fichier projet modifiable, le fichier *AssemblyInfo* ou le fichier *. vstemplate* .

3. Mettez à jour le fichier *. vstemplate* pour refléter les ajouts et les suppressions. L’élément de [projet](../extensibility/project-element-visual-studio-templates.md) doit contenir un élément [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pour chaque fichier à inclure dans le modèle.

4. Modifiez vos fichiers de code et tout autre contenu accessible aux utilisateurs, puis ajoutez les substitutions de paramètres appropriées.

5. Modifiez le contenu généré en fonction des besoins.

6. Créez le projet.

     Visual Studio crée un fichier *. zip* qui contient votre modèle. Elle n’est pas déployée et n’est pas disponible dans l’instance expérimentale.

## <a name="create-an-item-template"></a>Créer un modèle d’élément

1. Créez un projet de modèle d’élément.

     Le modèle génère un fichier de classe, une icône, un fichier *. vstemplate* et un fichier *AssemblyInfo* . Le fichier de classe contient des substitutions de paramètre courantes.

2. Ajoutez et supprimez des éléments du projet selon les besoins de votre projet.

3. Mettez à jour le fichier *. vstemplate* pour refléter les ajouts et les suppressions. L’élément de [projet](../extensibility/project-element-visual-studio-templates.md) doit contenir un élément [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pour chaque fichier à inclure dans le modèle.

4. Modifiez vos fichiers de code et tout autre contenu accessible aux utilisateurs, puis ajoutez les substitutions de paramètres appropriées.

5. Modifiez le contenu généré en fonction des besoins.

6. Créez le projet.

     Visual Studio crée un fichier compressé qui contient votre modèle. Elle n’est pas déployée et n’est pas disponible dans l’instance expérimentale.

## <a name="deployment"></a>Déploiement

### <a name="to-deploy-the-project-or-item-template"></a>Pour déployer le modèle de projet ou d’élément

1. Créez un projet VSIX. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).

2. Définissez le projet VSIX comme projet de démarrage. Dans le **Explorateur de solutions**, sélectionnez le nœud de projet VSIX, cliquez avec le bouton droit, puis sélectionnez **définir comme projet de démarrage**.

3. Définissez le projet de modèle de projet en tant que ressource du projet VSIX. Ouvrez le fichier *. vsixmanifest* . Accédez à l’onglet **composants** , puis sélectionnez **nouveau**.

    1. Définissez le champ **type** sur **Microsoft. VisualStudio. ProjectTemplate** ou **Microsoft. VisualStudio. ItemTemplate**.

    2. Pour source, sélectionnez l’option **un projet dans la solution actuelle** , puis sélectionnez le projet qui contient votre modèle.

4. Générez la solution, puis appuyez sur **F5**. L’instance expérimentale s’affiche.

5. Pour un projet de modèle de projet, votre modèle de projet doit apparaître dans la boîte de dialogue **nouveau projet** (**fichier**  >  **nouveau**  >  **projet**), dans le nœud Visual C# ou Visual Basic. Pour un projet de modèle d’élément, votre modèle d’élément doit apparaître dans la boîte de dialogue **Ajouter un nouvel élément** . Pour afficher la boîte de dialogue **Ajouter un nouvel élément** , dans la **Explorateur de solutions**, sélectionnez le nœud du projet et sélectionnez **Ajouter**  >  **un nouvel élément**.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les modèles Visual Studio](../ide/creating-project-and-item-templates.md)
- [Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
