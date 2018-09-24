---
title: Création de modèles de projets et modèles d’élément | Microsoft Docs
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
ms.openlocfilehash: eeea0f92fc846b6ed51673d22450b22e01b348eb
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497860"
---
# <a name="create-custom-project-and-item-templates"></a>Créer des modèles de projet et d’élément personnalisés

Le SDK Visual Studio inclut des modèles de projet de créer un modèle de projet personnalisé et un modèle d’élément personnalisé. Ces modèles incluent des substitutions de paramètre commun et générer en tant que fichiers zip. Ils ne sont pas automatiquement déployés, et ils ne sont pas disponibles dans l’instance expérimentale. Vous devez copier le fichier zip généré dans le répertoire de modèle utilisateur.
  
Les modèles de création de modèle vous permettent d’inclure des modèles dans des extensions plus volumineuses. Cela vous permet d’implémenter le contrôle de version dans les fichiers source et de créer un groupe de projets de modèle dans un package VSIX.  
  
Vous pouvez également configurer un modèle pour installer les packages NuGet. Pour plus d’informations, consultez [packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Pour les scénarios de création de modèle de base, vous devez utiliser le **Export Template** Assistant, qui envoie le résultat vers un fichier compressé. Pour plus d’informations sur la création de modèle de base, consultez [création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).  

> [!NOTE]
> À partir de Visual Studio 2017, l’analyse pour les modèles de projets et modèles d’élément est n’est plus effectuée. Au lieu de cela, l’extension doit fournir les fichiers de manifeste de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un fichier MSI, vous devez générer manuellement les fichiers manifeste de modèle. Pour plus d’informations, consultez [mise à niveau projet et élément de modèles personnalisés pour Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Le schéma de manifeste de modèle est documenté dans [référence de schéma de manifeste de modèle Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Créer un modèle de projet  
  
1.  Créez un projet de modèle de projet. Vous pouvez trouver le modèle de projet dans le **nouveau projet** boîte de dialogue, dans Visual Basic ou Visual c# *extensibilité* dossier.  
  
     Le modèle génère un fichier de classe, une icône, une *.vstemplate* de fichiers, un fichier de projet modifiable nommé *ProjectTemplate.vbproj* ou *ProjectTemplate.csproj*et certains fichiers qui sont généralement générés par d’autres types de projet, tel un *resources.resx* fichier, un *AssemblyInfo* fichier et un *.settings* fichier. Chaque fichier de code contient des substitutions de paramètre commun le cas échéant.  
  
2.  Ajouter et supprimer des éléments à partir du projet en fonction des besoins de votre projet. Ne supprimez pas le fichier projet modifiable, la *AssemblyInfo* fichier, ou le *.vstemplate* fichier.  
  
3.  Mise à jour le *.vstemplate* fichier afin de refléter les ajouts et les suppressions. Le [projet](../extensibility/project-element-visual-studio-templates.md) élément doit contenir un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) élément pour chaque fichier à inclure dans le modèle.  
  
4.  Modifier vos fichiers de code et d’autres contenus visibles par l’utilisateur et ajoutez des substitutions de paramètre appropriée.  
  
5.  Modifier le contenu généré en fonction des besoins.  
  
6.  Générez le projet.  
  
     Visual Studio crée un *.zip* fichier qui contient votre modèle. Il n’est pas déployée, et il n’est pas disponible dans l’instance expérimentale.  
  
## <a name="create-an-item-template"></a>Créer un modèle d’élément  
  
1.  Créer un projet de modèle d’élément.  
  
     Le modèle génère un fichier de classe, une icône, une *.vstemplate* fichier et un *AssemblyInfo* fichier. Le fichier de classe contient des substitutions de paramètre commun.  
  
2.  Ajouter et supprimer des éléments à partir du projet en fonction des besoins de votre projet.  
  
3.  Mise à jour le *.vstemplate* fichier afin de refléter les ajouts et les suppressions. Le [projet](../extensibility/project-element-visual-studio-templates.md) élément doit contenir un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) élément pour chaque fichier à inclure dans le modèle.  
  
4.  Modifier vos fichiers de code et d’autres contenus visibles par l’utilisateur et ajoutez des substitutions de paramètre appropriée.  
  
5.  Modifier le contenu généré en fonction des besoins.  
  
6.  Générez le projet.  
  
     Visual Studio crée un fichier compressé qui contient votre modèle. Il n’est pas déployée, et il n’est pas disponible dans l’instance expérimentale.  
  
## <a name="deployment"></a>Déploiement  
  
### <a name="to-deploy-the-project-or-item-template"></a>Pour déployer le modèle de projet ou un élément  
  
1.  Créez un projet VSIX. Pour plus d’informations, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
2.  Définissez le projet VSIX comme projet de démarrage. Dans le **l’Explorateur de solutions**, sélectionnez le nœud du projet VSIX, avec le bouton droit, puis sélectionnez **définir comme projet de démarrage**.  
  
3.  Définissez le projet de modèle de projet en tant qu’actif du projet VSIX. Ouvrez le *.vsixmanifest* fichier. Accédez à la **actifs** onglet et cliquez sur **New**.  
  
    1.  Définir le **Type** champ **Microsoft.VisualStudio.ProjectTemplate** ou **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Pour la source, sélectionnez le **un projet dans la solution actuelle** option, puis sélectionnez le projet qui contient votre modèle.  
  
4.  Générer la solution, puis appuyez sur **F5**. L’instance expérimentale s’affiche.  
  
5.  Pour un projet de modèle de projet, vous devez voir votre modèle de projet répertorié dans le **nouveau projet** boîte de dialogue (**fichier** > **New**  >  **Projet**), dans le nœud Visual Basic ou Visual c#. Pour un projet de modèle d’élément, vous devez voir votre modèle d’élément répertoriée dans le **ajouter un nouvel élément** boîte de dialogue. Pour afficher le **ajouter un nouvel élément** boîte de dialogue, à partir de la **l’Explorateur de solutions**, sélectionnez le nœud du projet, puis cliquez sur **ajouter** > **unnouvelélément**).  
  
## <a name="see-also"></a>Voir aussi

[Référence de modèle Visual Studio](../ide/visual-studio-template-reference.md)  
[Packages NuGet dans les modèles Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)