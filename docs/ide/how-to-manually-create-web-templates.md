---
title: Créer des modèles web
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 245b20dd9cad465129d6c79c38e53b6379c2c09c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591006"
---
# <a name="how-to-manually-create-web-templates"></a>Guide pratique pour créer manuellement des modèles web

La création d’un modèle web ne ressemble pas à la création d’autres genres de modèle. Étant donné que les modèles de projets Web apparaissent dans la boîte de dialogue **Add New Web Site** et que les éléments de projet Web sont classés par langage de programmation, le fichier *vstemplate* doit spécifier le modèle comme modèle Web et identifier le langage de programmation.

> [!NOTE]
> Les modèles Web doivent contenir un fichier *.webproj* vide, et il doit `File` être référencé dans le fichier *vstemplate* dans l’attribut de l’élément. `Project` Bien que les projets Web ne nécessitent pas un fichier de projet *.proj,* il est nécessaire de créer ce fichier de talon pour le modèle web de fonctionner correctement.

## <a name="to-manually-create-a-web-template"></a>Pour créer manuellement un modèle web

1. Créez un projet web.

2. Modifiez ou supprimez les fichiers du projet, ou ajoutez de nouveaux fichiers au projet.

3. Créez un fichier XML et enregistrez-le avec une extension de nom de fichier *vstemplate,* dans le même répertoire que votre projet. Ne l’ajoutez pas au projet dans Visual Studio.

4. Modifier le fichier *vstemplate* XML pour fournir des métadonnées de modèle de projet. Pour plus d’informations, consultez l’[exemple qui suit](#example).

5. Localiser `ProjectType` l’élément dans le fichier *vstemplate,* et définir la valeur du texte à `Web`.

6. Après l’élément `ProjectType`, ajoutez un élément `ProjectSubType` et affectez au texte la valeur du langage de programmation du modèle. Voici les valeurs pouvant être affectées comme langage de programmation :

   - CSharp
   - VisualBasic

     Par exemple :

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Sélectionnez les fichiers dans votre modèle (cela inclut le fichier *vstemplate),* cliquez à droite sur la sélection, et choisissez **Envoyer à** > **compressé (zippé) dossier**. Les fichiers sont compressés dans un fichier *.zip*.

8. Placez le fichier de modèle *.zip* dans le répertoire du modèle de projet Visual Studio. Par défaut, ce répertoire est *%USERPROFILE% \<'Documents’Visual Studio Version\>'ProjectTemplates*.

## <a name="example"></a> Exemple

L’exemple suivant montre un fichier *vstemplate* de base pour un modèle de projet Web :

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi

- [Créer des modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
- [Informations de référence sur les schémas de modèles Visual Studio (extensibilité)](../extensibility/visual-studio-template-schema-reference.md)
