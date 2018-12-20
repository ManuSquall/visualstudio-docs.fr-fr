---
title: Créer des modèles web
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: cff4fda5113cdbacba2d9389e360707f49ba595b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063666"
---
# <a name="how-to-manually-create-web-templates"></a>Procédure : créer manuellement des modèles web

La création d’un modèle web ne ressemble pas à la création d’autres genres de modèle. Dans la mesure où les modèles de projet web apparaissent dans la boîte de dialogue **Ajouter un nouveau site web** et que les éléments de projet web sont catégorisés par langage de programmation, le fichier *vstemplate* doit spécifier le modèle en tant que modèle web et identifier le langage de programmation.

> [!NOTE]
> Les modèles web doivent contenir un fichier *.webproj* vide. Celui-ci doit être obligatoirement référencé dans le fichier *vstemplate*, dans l’attribut `File` de l’élément `Project`. Bien que les projets web ne nécessitent pas de fichier projet *.proj*, vous devez créer ce fichier stub pour que le modèle web fonctionne correctement.

## <a name="to-manually-create-a-web-template"></a>Pour créer manuellement un modèle web

1. Créez un projet web.

2. Modifiez ou supprimez les fichiers du projet, ou ajoutez de nouveaux fichiers au projet.

3. Créez un fichier XML et enregistrez-le avec l’extension de fichier *vstemplate* dans le même répertoire que votre projet. Ne l’ajoutez pas au projet dans Visual Studio.

4. Modifiez le fichier XML *vstemplate* pour fournir des métadonnées de modèle de projet. Pour plus d’informations, consultez l’[exemple qui suit](#example).

5. Localisez l’élément `ProjectType` dans le fichier *vstemplate*, puis affectez au texte la valeur `Web`.

6. Après l’élément `ProjectType`, ajoutez un élément `ProjectSubType` et affectez au texte la valeur du langage de programmation du modèle. Voici les valeurs pouvant être affectées comme langage de programmation :

   - CSharp
   - VisualBasic

     Par exemple :

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Sélectionnez les fichiers présents dans votre modèle (en incluant le fichier *vstemplate*), cliquez avec le bouton droit sur la sélection, puis choisissez **Envoyer vers** > **Dossier compressé**. Les fichiers sont compressés dans un fichier *.zip*.

8. Placez le fichier de modèle *.zip* dans le répertoire de modèles de projet Visual Studio. Par défaut, ce répertoire est *%USERPROFILE%\Documents\Visual Studio \<Version\>\ProjectTemplates*.

## <a name="example"></a>Exemple

L’exemple suivant montre un fichier *vstemplate* de base pour un modèle de projet web :

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
