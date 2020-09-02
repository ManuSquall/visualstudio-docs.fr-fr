---
title: Créer des modèles web
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6870143be825469fde2be4b3448da24d54034fc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284176"
---
# <a name="how-to-manually-create-web-templates"></a>Guide pratique pour créer manuellement des modèles web

La création d’un modèle web ne ressemble pas à la création d’autres genres de modèle. Étant donné que les modèles de projet Web apparaissent dans la boîte de dialogue **Ajouter un nouveau site Web** et que les éléments de projet Web sont catégorisés par langage de programmation, le fichier *VSTemplate* doit spécifier le modèle en tant que modèle Web et identifier le langage de programmation.

> [!NOTE]
> Les modèles Web doivent contenir un fichier *. webproj* vide et doivent être référencés dans le fichier *VSTemplate* dans l' `File` attribut de l' `Project` élément. Bien que les projets Web ne nécessitent pas de fichier projet *. proj* , il est nécessaire de créer ce fichier stub pour que le modèle Web fonctionne correctement.

## <a name="to-manually-create-a-web-template"></a>Pour créer manuellement un modèle web

1. Créez un projet web.

2. Modifiez ou supprimez les fichiers du projet, ou ajoutez de nouveaux fichiers au projet.

3. Créez un fichier XML et enregistrez-le avec une extension de nom de fichier *VSTemplate* , dans le même répertoire que votre projet. Ne l’ajoutez pas au projet dans Visual Studio.

4. Modifiez le fichier XML *VSTemplate* pour fournir les métadonnées du modèle de projet. Pour plus d’informations, consultez l’[exemple qui suit](#example).

5. Localisez l' `ProjectType` élément dans le fichier *VSTemplate* , puis affectez la valeur au texte `Web` .

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

7. Sélectionnez les fichiers dans votre modèle (y compris le fichier *VSTemplate* ), cliquez avec le bouton droit sur la sélection, puis choisissez **Envoyer vers**le  >  **dossier compressé**. Les fichiers sont compressés dans un fichier *.zip*.

8. Placez le fichier de modèle *. zip* dans le répertoire de modèles de projet Visual Studio. Par défaut, ce répertoire est *%USERPROFILE%\Documents\Visual Studio \<Version\> \ProjectTemplates*.

## <a name="example"></a>Exemple

L’exemple suivant montre un fichier *VSTemplate* de base pour un modèle de projet Web :

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

- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Informations de référence sur les schémas de modèles Visual Studio (extensibilité)](../extensibility/visual-studio-template-schema-reference.md)
