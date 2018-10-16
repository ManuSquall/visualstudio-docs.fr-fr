---
title: Guide pratique pour créer des modèles à plusieurs projets | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99c8a008cf48d596569e61534d7bfbf7cb9e45c8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256566"
---
# <a name="how-to-create-multi-project-templates"></a>Comment : créer des modèles à plusieurs projets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets. Quand un projet basé sur un modèle à plusieurs projets est créé à partir de la boîte de dialogue **Nouveau projet**, tous les projets inclus dans le modèle sont ajoutés à la solution.  
  
 Un modèle à plusieurs projets doit inclure les éléments suivants, compressés dans un fichier .zip :  
  
-   Un fichier .vstemplate racine pour tout le modèle à plusieurs projets. Ce fichier .vstemplate racine contient les métadonnées affichées dans la boîte de dialogue **Nouveau projet** et indique l’emplacement des fichiers .vstemplate pour les projets du modèle. Ce fichier doit se trouver à la racine du fichier .zip.  
  
-   Un ou plusieurs dossiers contenant les fichiers nécessaires pour un modèle de projet complet. Ils incluent tous les fichiers de code du projet ainsi qu’un fichier .vstemplate pour le projet.  
  
 Par exemple, le fichier .zip d’un modèle à plusieurs projets contenant deux projets peut contenir les fichiers et répertoires suivants :  
  
 MultiProjectTemplate.vstemplate  
  
 \Project1\Project1.vstemplate  
  
 \Project1\Project1.vbproj  
  
 \Project1\Class.vb  
  
 \Project2\Project2.vstemplate  
  
 \Project2\Project2.vbproj  
  
 \Project2\Class.vb  
  
 Le fichier .vstemplate racine d’un modèle à plusieurs projets présente les différences suivantes par rapport à un modèle à projet unique :  
  
-   L’attribut `Type` de l’élément `VSTemplate` a la valeur `ProjectGroup`. Exemple :  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   L’élément `TemplateContent` contient un élément `ProjectCollection` avec un ou plusieurs éléments `ProjectTemplateLink` qui définissent les chemins des fichiers .vstemplate des projets inclus. Exemple :  
  
    ```  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink>  
                Project1\Project1.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink>  
                Project2\Project2.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
    ```  
  
 Les modèles à plusieurs projets ont également un comportement différent des modèles standard. Les modèles à plusieurs projets ont les caractéristiques particulières suivantes :  
  
-   Vous ne pouvez pas assigner les noms de manière individuelle aux projets d’un modèle à plusieurs projets dans la boîte de dialogue **Nouveau projet**. Pour spécifier le nom de chaque projet, vous devez définir l’attribut `ProjectName` sur l’élément `ProjectTemplateLink`. Pour plus d’informations, consultez le premier exemple dans la section suivante.  
  
-   Les modèles à plusieurs projets peuvent contenir des projets écrits dans des langages différents, mais l’ensemble du modèle doit être placé dans une seule catégorie à l’aide de l’élément `ProjectType`.  
  
### <a name="to-create-a-multi-project-template"></a>Pour créer un modèle à plusieurs projets  
  
1.  Créez les projets à inclure dans le modèle à plusieurs projets.  
  
2.  Créez des fichiers .vstemplate pour chacun des projets. Pour plus d’informations, consultez [Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md).  
  
3.  Créez un fichier .vstemplate racine qui contiendra les métadonnées du modèle à plusieurs projets. Pour plus d’informations, consultez le premier exemple dans la section suivante.  
  
4.  Sélectionnez les fichiers et dossiers à inclure dans votre modèle, cliquez avec le bouton droit sur la sélection, cliquez sur **Envoyer vers**, puis cliquez sur **Dossier compressé (zippé)**. Les fichiers et dossiers sont compressés dans un fichier .zip.  
  
5.  Placez le fichier modèle .zip dans le répertoire du modèle de projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Par défaut, ce répertoire est \My Documents\Visual Studio *Version*\Templates\ProjectTemplates\\.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre un fichier .vstemplate racine de base pour un modèle à plusieurs projets. Dans cet exemple, le modèle contient deux projets, `My Windows Application` et `My Class Library`. L'attribut `ProjectName` de l'élément `ProjectTemplateLink` définit le nom à assigner au projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si l'attribut `ProjectName` n'existe pas, le nom du fichier .vstemplate est utilisé comme nom du projet.  
  
```  
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
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l’élément `SolutionFolder` pour scinder les projets en deux groupes, `Math Classes` et `Graphics Classes`. Le modèle contient quatre projets, dont deux sont placés dans chaque dossier de solution.  
  
```  
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
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Élément SolutionFolder (modèles Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [Élément ProjectTemplateLink (modèles Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)



