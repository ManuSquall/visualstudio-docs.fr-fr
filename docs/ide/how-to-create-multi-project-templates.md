---
title: "Comment&#160;: cr&#233;er des mod&#232;les &#224; plusieurs projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles à projets multiples"
  - "modèles de projet, créer des modèles à projets multiples"
  - "modèles Visual Studio, créer des modèles à projets multiples"
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Comment&#160;: cr&#233;er des mod&#232;les &#224; plusieurs projets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les modèles à plusieurs projets jouent le rôle de conteneurs pour au moins deux projets.  Lorsqu'un projet basé sur un modèle à projets multiples est créé à partir de la boîte de dialogue **Nouveau projet**, tous les projets inclus dans ce modèle sont ajoutés à la solution.  
  
 Un modèle à projets multiples doit inclure les éléments suivants, compressés dans un fichier .zip :  
  
-   Un fichier .vstemplate racine pour tout le modèle à plusieurs projets.  Ce fichier .vstemplate racine contient les métadonnées affichées dans la boîte de dialogue **Nouveau projet** et spécifie où rechercher les fichiers .vstemplate pour les projets de ce modèle.  Ce fichier doit se trouver à la racine du fichier .zip.  
  
-   Un ou plusieurs dossiers contenant les fichiers obligatoires pour un modèle de projet complet.  Ils incluent tous les fichiers de code du projet ainsi qu'un fichier .vstemplate pour le projet.  
  
 Par exemple, le fichier .zip d'un modèle à projets multiples contenant deux projets peut contenir les fichiers et répertoires suivants :  
  
 MultiProjectTemplate.vstemplate  
  
 \\Project1\\Project1.vstemplate  
  
 \\Project1\\Project1.vbproj  
  
 \\Project1\\Class.vb  
  
 \\Project2\\Project2.vstemplate  
  
 \\Project2\\Project2.vbproj  
  
 \\Project2\\Class.vb  
  
 Le fichier .vstemplate racine d'un modèle à projets multiples présente les différences suivantes par rapport à un modèle de projet unique :  
  
-   L'attribut `Type` de l'élément `VSTemplate` contient la valeur `ProjectGroup`.  Par exemple :  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   L'élément `TemplateContent` contient un élément `ProjectCollection` avec un ou plusieurs éléments `ProjectTemplateLink` qui définissent les chemins d'accès aux fichiers .vstemplate des projets inclus.  Par exemple :  
  
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
  
 Les modèles à plusieurs projets ont également un comportement différent des modèles normaux.  Les modèles à plusieurs projets ont les caractéristiques uniques suivantes :  
  
-   Il n'est pas possible d'assigner des noms à des projets individuels d'un modèle à plusieurs projets dans la boîte de dialogue **Nouveau projet**.  À la place, pour spécifier le nom de chaque projet, utilisez l'attribut `ProjectName` sur l'élément `ProjectTemplateLink`.  Pour plus d'informations, consultez le premier exemple de la section suivante.  
  
-   Les modèles à projets multiples peuvent contenir des projets écrits dans différents langages, mais l'ensemble du modèle ne peut être placé que dans une catégorie à l'aide de l'élément `ProjectType`.  
  
### Pour créer un modèle à plusieurs projets  
  
1.  Créez les projets à inclure dans le modèle à plusieurs projets.  
  
2.  Créez des fichiers .vstemplate pour chaque projet.  Pour plus d'informations, consultez [Comment : créer des modèles de projet](../ide/how-to-create-project-templates.md).  
  
3.  Créez un fichier .vstemplate racine qui contiendra les métadonnées du modèle à projets multiples.  Pour plus d'informations, consultez le premier exemple de la section suivante.  
  
4.  Sélectionnez les fichiers et dossiers à inclure dans votre modèle, cliquez avec le bouton droit sur la sélection, cliquez sur **Envoyer vers** puis cliquez sur **Dossier compressé \(zippé\)**.  Les fichiers et dossiers sont compressés dans un fichier .zip.  
  
5.  Placez le fichier modèle .zip dans le répertoire du modèle de projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  par défaut, ce répertoire est \\My Documents\\Visual Studio *version*\\Templates\\ProjectTemplates \\.  
  
## Exemple  
 Cet exemple montre un fichier .vstemplate racine de base pour un modèle à projets multiples.  Dans cet exemple, le modèle contient deux projets, `My Windows Application` et `My Class Library`.  L'attribut `ProjectName` de l'élément `ProjectTemplateLink` définit le nom à assigner au projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si l'attribut `ProjectName` n'existe pas, le nom du fichier .vstemplate est utilisé comme nom du projet.  
  
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
  
## Exemple  
 Cet exemple utilise l'élément `SolutionFolder` pour diviser les projets en deux groupes, `Math Classes` et `Graphics Classes`.  Le modèle contient quatre projets, dont deux placés dans chaque dossier de solution.  
  
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
  
## Voir aussi  
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Comment : créer des modèles de projet](../ide/how-to-create-project-templates.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder, élément \(modèles Visual Studio\)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink, élément \(modèles Visual Studio\)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)