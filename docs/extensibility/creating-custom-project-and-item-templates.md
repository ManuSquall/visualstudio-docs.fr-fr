---
title: Création de modèles de projets et d’objets personnalisés ( Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739453"
---
# <a name="create-custom-project-and-item-templates"></a>Créez des modèles de projets et d’objets personnalisés

Le Visual Studio SDK comprend des modèles de projet qui créent un modèle de projet personnalisé et un modèle d’article personnalisé. Ces modèles incluent certaines substitutions de paramètres communs, et sont construits sous forme de fichiers zip. Ils ne sont pas automatiquement déployés, et ils ne sont pas disponibles dans le cas expérimental. Vous devez copier le fichier zip généré à l’annuaire du modèle utilisateur.

Les modèles de création de modèles vous permettent d’inclure des modèles dans des extensions plus grandes. Cela vous permet d’implémenter le contrôle de la version sur les fichiers sources et de construire un groupe de projets de modèle en un seul package VSIX.

Vous pouvez également configurer un modèle pour installer des paquets NuGet. Pour plus d’informations, voir [les paquets NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Pour les scénarios de création de modèles de base, vous devez utiliser **l’assistant Modèle d’exportation,** qui se produit sur un fichier compressé. Pour plus d’informations sur la création de modèles de base, voir [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> À partir de Visual Studio 2017, la numérisation des modèles de projets et d’objets personnalisés ne sera plus effectuée. Au lieu de cela, l’extension doit fournir des fichiers manifestes modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un MSI, vous devez générer les fichiers manifestes de modèle à la main. Pour plus d’informations, voir [Upgrading custom project and item templates for Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Le schéma manifeste de modèle est documenté dans [visual Studio modèle de référence manifeste schéma](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Créer un modèle de projet

1. Créez un projet Project Template. Vous pouvez trouver le modèle de projet dans le dialogue **du nouveau projet,** en recherchant le « modèle de projet » et en sélectionnant la version C ou Visual Basic.

     Le modèle génère un fichier de classe, une icône, un fichier *.vstemplate,* un fichier de projet modifiable nommé *ProjectTemplate.vbproj* ou *ProjectTemplate.csproj*, et certains fichiers qui sont généralement générés par d’autres types de projet, un tel fichier *resources.resx,* un fichier *AssemblyInfo,* et un fichier *.paramètres.* Chaque fichier de code contient des substitutions de paramètres communes, le cas échéant.

![sélection de projets](media/project-template-selection.png)

2. Ajoutez et supprimez les éléments du projet au besoin pour votre projet. Ne supprimez pas le fichier de projet modifiable, le fichier *AssemblyInfo* ou le fichier *.vstemplate.*

3. Mettre à jour le fichier *.vstemplate* pour refléter les ajouts et les suppressions. [L’élément Projet](../extensibility/project-element-visual-studio-templates.md) doit contenir un élément [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pour que chaque fichier soit inclus dans le modèle.

4. Modifiez vos fichiers de code et d’autres contenus orientés vers l’utilisateur, et ajoutez des substitutions de paramètres appropriées.

5. Modifier le contenu généré au besoin.

6. Créez le projet.

     Visual Studio crée un fichier *.zip* qui contient votre modèle. Il n’est pas déployé, et il n’est pas disponible dans le cas expérimental.

## <a name="create-an-item-template"></a>Créer un modèle d’élément

1. Créez un projet De modèle d’élément.

     Le modèle génère un fichier de classe, une icône, un fichier *.vstemplate* et un fichier *AssemblyInfo.* Le fichier de classe contient quelques substitutions de paramètres communs.

2. Ajoutez et supprimez les éléments du projet au besoin pour votre projet.

3. Mettre à jour le fichier *.vstemplate* pour refléter les ajouts et les suppressions. [L’élément Projet](../extensibility/project-element-visual-studio-templates.md) doit contenir un élément [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) pour que chaque fichier soit inclus dans le modèle.

4. Modifiez vos fichiers de code et d’autres contenus orientés vers l’utilisateur, et ajoutez des substitutions de paramètres appropriées.

5. Modifier le contenu généré au besoin.

6. Créez le projet.

     Visual Studio crée un fichier compressé qui contient votre modèle. Il n’est pas déployé, et il n’est pas disponible dans le cas expérimental.

## <a name="deployment"></a>Déploiement

### <a name="to-deploy-the-project-or-item-template"></a>Pour déployer le modèle de projet ou d’élément

1. Créez un projet VSIX. Pour plus d’informations, consultez [le modèle de projet VSIX](../extensibility/vsix-project-template.md).

2. Définissez le projet VSIX comme le projet de démarrage. Dans le **Solution Explorer**, sélectionnez le nœud de projet VSIX, clic droit et **sélectionnez Set en tant que projet Startup**.

3. Définissez le projet de modèle de projet comme un atout du projet VSIX. Ouvrez le fichier *.vsixmanifest.* Allez à l’onglet **Actifs** et cliquez sur **Nouveau**.

    1. Définissez le champ **de type** à **Microsoft.VisualStudio.ProjectTemplate** ou **Microsoft.VisualStudio.ItemTemplate**.

    2. Pour la source, sélectionnez le **projet A dans l’option de solution actuelle,** puis sélectionnez le projet qui contient votre modèle.

4. Construire la solution, et appuyez sur **F5**. L’instance expérimentale apparaît.

5. Pour un projet de modèle de projet, vous devez voir votre modèle de projet répertorié dans le dialogue **du nouveau projet** **(File** > **New** > **Project**), dans le nœud Visual C ou Visual Basic. Pour un projet de modèle d’élément, vous devez voir votre modèle d’article répertorié dans le dialogue **Add New Item.** Pour voir le dialogue **Add New Item,** à partir de **l’Explorer Solution**, sélectionnez le nœud de projet et cliquez sur **Ajouter** > **un nouvel article**).

## <a name="see-also"></a>Voir aussi

- [Référence de modèle de studio visuel](../ide/creating-project-and-item-templates.md)
- [Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
