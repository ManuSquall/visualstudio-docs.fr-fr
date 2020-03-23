---
title: Créer des modèles à projets multiples
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6da7464f5e22e186edff7671744c2605bee3c9ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591084"
---
# <a name="how-to-create-multi-project-templates"></a>Guide pratique pour créer des modèles à plusieurs projets

Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets. Quand vous créez un projet basé sur un modèle multiprojet, tous les projets inclus dans le modèle sont ajoutés à la solution.

Un modèle à plusieurs projets contient deux modèles de projet ou plus, ainsi qu’un modèle racine de type **ProjectGroup**.

Les modèles à plusieurs projets se comportent différemment des modèles à projet unique. Leurs caractéristiques particulières sont les suivantes :

- Vous ne pouvez pas affecter des noms de façon individuelle aux projets d’un modèle multiprojet quand le modèle est utilisé pour créer un projet. Pour spécifier un nom pour chaque projet, utilisez plutôt l’attribut **ProjectName** sur l’élément **ProjectTemplateLink** dans le fichier *vstemplate*.

- Les modèles à plusieurs projets peuvent contenir des projets pour des langages différents, mais l’ensemble du modèle lui-même doit être placé dans une seule catégorie. Spécifiez la catégorie du modèle dans l’élément **ProjectType** du fichier *vstemplate*.

Un modèle à plusieurs projets doit inclure les éléments suivants, compressés dans un fichier *.zip* :

- Un fichier *de vstemplate* racine pour l’ensemble du modèle multi-projet. Ce fichier *vstemplate* racine contient des métadonnées qui s’affichent dans la boîte de dialogue où vous créez un projet. Il spécifie également où trouver les fichiers *vstemplate* pour les projets du modèle. Ce fichier doit se trouver à la racine du fichier *.zip*.

- Deux dossiers ou plus contenant les fichiers exigés pour un modèle de projet complet sont nécessaires. Les dossiers comprennent tous les fichiers de code pour le projet, ainsi qu’un fichier *vstemplate* pour le projet.

Par exemple, le fichier *.zip* d’un modèle à plusieurs projets contenant deux projets peut comporter les fichiers et répertoires suivants :

- *MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

Le fichier *de vstemplate* racine pour un modèle multi-projet diffère d’un modèle d’un seul projet de la manière suivante :

- L’attribut **Type** de l’élément **VSTemplate** a la valeur **ProjectGroup** au lieu de **Project**. Par exemple :

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- L’élément **TemplateContent** contient un élément **ProjectCollection** ayant un ou plusieurs éléments **ProjectTemplateLink** qui définissent les chemins des fichiers *vstemplate* des projets inclus. Par exemple :

    ```xml
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink>
                Project1\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink>
                Project2\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
    ```

> [!TIP]
> Si vous souhaitez que seul le modèle à plusieurs projets s’affiche dans la boîte de dialogue du nouveau projet et pas les projets individuels qu’il contient, marquez les modèles internes comme [masqués](../extensibility/hidden-element-visual-studio-templates.md). Par exemple :
>
> ```xml
> <VSTemplate Type="Project" ... >
>     <TemplateData>
>         ...
>         <Hidden>true</Hidden>
>     </TemplateData>
>     ...
> </VSTemplate>
> ```

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Créer un modèle multiprojet à partir d’une solution existante

1. Créez une solution et ajoutez deux projets ou plus.

2. Personnalisez les projets jusqu’à ce qu’ils soient prêts à être exportés dans un modèle.

   > [!TIP]
   > Si vous utilisez des [paramètres de modèle](template-parameters.md) et que vous voulez référencer des variables du modèle parent, préfixez le nom du paramètre avec `ext_`. Par exemple : `$ext_safeprojectname$`. Par ailleurs, définissez l’attribut **CopyParameters** de l’élément **ProjectTemplateLink** sur **true**.
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. Sur le menu du **projet,** choisissez **Export Template**.

   L’Assistant **Exportation de modèle** s’ouvre.

4. Dans la page **Choisir un type de modèle**, sélectionnez **Modèle de projet**. Sélectionnez un des projets que vous voulez exporter vers un modèle, puis choisissez **Suivant**. (Vous répétez ces étapes pour chaque projet de la solution.)

5. Dans la page **Sélectionner les options du modèle**, entrez un nom et éventuellement une description, une icône et une image d’aperçu pour votre modèle. Cliquez sur **Terminer**.

   Le projet est exporté dans un fichier *.zip* et placé à l’emplacement de sortie spécifié.

   > [!NOTE]
   > Chaque projet doit être exporté séparément dans un modèle, donc répétez les étapes précédentes pour chaque projet dans la solution.

6. Créez un répertoire pour votre modèle, avec un sous-répertoire pour chaque projet.

7. Extrayez le contenu du fichier *.zip* de chaque projet dans le sous-répertoire correspondant que vous avez créé.

8. Dans le répertoire de base, créez un fichier XML portant une extension *.vstemplate*. Ce fichier contient les métadonnées du modèle à plusieurs projets. Consultez l’exemple qui suit pour la structure du fichier. Assurez-vous de spécifier le chemin relatif vers le fichier *vstemplate* de chaque projet.

9. Sélectionnez tous les fichiers dans l’annuaire de base, et à partir du bon clic ou du menu contextuelle, choisissez **Envoyer à** > **compressé (zippé) dossier**.

   Les fichiers et dossiers sont compressés dans un fichier *.zip*.

10. Copiez le fichier *.zip* dans le répertoire des modèles de projet utilisateur. Par défaut, ce répertoire est : *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates*.

11. Dans Visual Studio, choisissez **File** > **New** > **Project** et vérifiez que votre modèle apparaît.

## <a name="two-project-example"></a>Exemple avec deux projets

Cet exemple montre un fichier de base *de vstemplate* racine multi-projet. Dans cet exemple, le modèle a deux projets, **My Windows Application** et **My Class Library**. L’attribut **ProjectName** de l’élément **ProjectTemplateLink** spécifie le nom donné au projet.

> [!TIP]
> Si l’attribut **ProjectName** n’est pas spécifié, le nom du fichier *vstemplate* est utilisé comme nom de projet.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="example-with-solution-folders"></a>Exemple avec des dossiers de solution

Cet exemple utilise l’élément **SolutionFolder** pour diviser les projets en deux groupes, **Math Classes** et **Graphics Classes**. Le modèle comporte quatre projets, dont deux sont placés dans chaque dossier solution.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi

- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
- [Comment : Créer des modèles de projet](../ide/how-to-create-project-templates.md)
- [Informations de référence sur les schémas de modèles Visual Studio (extensibilité)](../extensibility/visual-studio-template-schema-reference.md)
- [Élément SolutionFolder (modèles Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [Élément ProjectTemplateLink (modèles Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
