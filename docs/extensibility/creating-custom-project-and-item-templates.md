---
title: Création de projets et modèles d’élément | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc866c9a0cd5f3aaaa06e5bc59ea2427cc86268a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-custom-project-and-item-templates"></a>Création de projets et modèles d’élément

Le Kit de développement logiciel Visual Studio inclut des modèles de projet que vous créez un modèle de projet personnalisé et un modèle d’élément personnalisé. Ces modèles comprennent des substitutions de paramètre commun et créer en tant que fichiers zip. Elles ne sont pas déployées automatiquement, et elles ne sont pas disponibles dans l’instance expérimentale. Vous devez copier le fichier zip générés pour le répertoire de modèles utilisateur.
  
Les modèles de création de modèle vous permettent d’inclure des modèles dans les extensions supérieure. Cela vous permet d’implémenter le contrôle de version sur les fichiers sources et de créer un groupe de projets de modèle dans un package VSIX.  
  
Vous pouvez également configurer un modèle pour installer les packages NuGet. Pour plus d’informations, consultez [les packages NuGet dans des modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Pour les scénarios de création de modèle de base, vous devez utiliser le **exporter le modèle** Assistant, ce qui génère un fichier compressé. Pour plus d’informations sur la création du modèle de base, consultez [création de modèles de projet et élément](../ide/creating-project-and-item-templates.md).  

> [!NOTE]
> À partir de Visual Studio 2017, l’analyse des modèles de projets et modèles d’élément sera n’est plus effectuée. Au lieu de cela, l’extension doit fournir les fichiers de manifeste de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un fichier MSI, vous devez générer les fichiers manifeste de modèle à la main. Pour plus d’informations, consultez [mise à niveau des projets et des modèles d’élément pour Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Le schéma de modèle de manifeste est documenté dans [Visual Studio Template manifeste Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="creating-a-project-template"></a>Création d’un modèle de projet  
  
1.  Créez un projet de modèle de projet. Vous pouvez trouver le modèle de projet dans le **nouveau projet** boîte de dialogue, dans Visual Basic ou Visual c# **extensibilité** dossier.  
  
     Le modèle génère un fichier de classe, une icône, un fichier .vstemplate, un fichier de projet modifiable nommé ProjectTemplate.vbproj ou ProjectTemplate.csproj et certains fichiers qui sont habituellement générées par d’autres types de projet, un tel fichier resources.resx, un AssemblyInfo. et un fichier .settings. Chaque fichier de code contient les substitutions de paramètre commun le cas échéant.  
  
2.  Ajouter et supprimer des éléments à partir du projet en fonction des besoins de votre projet. Ne supprimez pas le fichier projet modifiable, le fichier AssemblyInfo ou le fichier .vstemplate.  
  
3.  Mettre à jour le fichier .vstemplate pour refléter les ajouts et les suppressions. Le [projet](../extensibility/project-element-visual-studio-templates.md) élément doit contenir un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) élément pour chaque fichier à inclure dans le modèle.  
  
4.  Modifier vos fichiers de code et d’autres contenus de la direction de l’utilisateur et ajoutez des substitutions de paramètre appropriées.  
  
5.  Modifier le contenu généré en fonction des besoins.  
  
6.  Générez le projet.  
  
     Visual Studio crée un fichier .zip qui contient votre modèle. Il n’est pas déployée, et il n’est pas disponible dans l’instance expérimentale.  
  
## <a name="creating-an-item-template"></a>Création d’un modèle d’élément  
  
1.  Créer un projet de modèle d’élément.  
  
     Le modèle génère un fichier de classe, une icône, un fichier .vstemplate et un fichier AssemblyInfo. Le fichier de classe contient des substitutions de paramètre commun.  
  
2.  Ajouter et supprimer des éléments à partir du projet en fonction des besoins de votre projet.  
  
3.  Mettre à jour le fichier .vstemplate pour refléter les ajouts et les suppressions. Le [projet](../extensibility/project-element-visual-studio-templates.md) élément doit contenir un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) élément pour chaque fichier à inclure dans le modèle.  
  
4.  Modifier vos fichiers de code et d’autres contenus de la direction de l’utilisateur et ajoutez des substitutions de paramètre appropriées.  
  
5.  Modifier le contenu généré en fonction des besoins.  
  
6.  Générez le projet.  
  
     Visual Studio crée un fichier compressé qui contient votre modèle. Il n’est pas déployée, et il n’est pas disponible dans l’instance expérimentale.  
  
## <a name="deployment"></a>Déploiement  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Pour déployer le modèle de projet ou un élément  
  
1.  Créez un projet VSIX. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
2.  Définissez le projet VSIX comme projet de démarrage. Dans le **l’Explorateur de solutions**, sélectionnez le nœud du projet VSIX, avec le bouton droit et sélectionnez **définir comme projet de démarrage**.  
  
3.  Définir le projet de modèle de projet comme composant du projet VSIX. Ouvrez le fichier .vsixmanifest. Accédez à la **actifs** onglet et cliquez sur **nouveau**.  
  
    1.  Définir le **Type** au champ **Microsoft.VisualStudio.ProjectTemplate** ou **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Pour la source, sélectionnez le **un projet dans la solution actuelle** option et sélectionnez le projet qui contient votre modèle.  
  
4.  Générez la solution, appuyez sur F5. L’instance expérimentale s’affiche.  
  
5.  Pour un projet de modèle de projet, vous devez voir votre modèle de projet répertorié dans le **nouveau projet** boîte de dialogue (**fichier > Nouveau > projet**), dans le nœud Visual Basic ou Visual c#. Pour un projet de modèle d’élément, vous devez voir votre modèle d’élément dans la boîte de dialogue Ajouter un nouvel élément (dans le **l’Explorateur de solutions**, sélectionnez le nœud du projet, cliquez sur **Ajouter / nouvel élément**).  
  
## <a name="see-also"></a>Voir aussi

[Référence de modèle Visual Studio](../ide/visual-studio-template-reference.md)  
[Packages NuGet dans des modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)