---
title: Créer des modèles web pour Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f7dcc6f14bc631d4d5880d0d7f1ee123bde0306
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-manually-create-web-templates"></a>Guide pratique pour créer manuellement des modèles web

La création d’un modèle web ne ressemble pas à la création d’autres genres de modèle. Dans la mesure où les modèles de projet web apparaissent dans la boîte de dialogue **Ajouter un nouveau site web** et que les éléments de projet web sont catégorisés par langage de programmation, le fichier *.vstemplate* doit spécifier le modèle en tant que modèle web et identifier le langage de programmation.

> [!NOTE]
> Les modèles web doivent contenir un fichier *.webproj* vide. Celui-ci doit être obligatoirement référencé dans le fichier *.vstemplate*, dans l’attribut `File` de l’élément `Project`. Bien que les projets web ne nécessitent pas de fichier projet *.proj*, vous devez créer ce fichier stub pour que le modèle web fonctionne correctement.

### <a name="to-manually-create-a-web-template"></a>Pour créer manuellement un modèle web

1. Créez un projet web.

1. Modifiez ou supprimez les fichiers du projet, ou ajoutez de nouveaux fichiers au projet.

1. Créez un fichier XML et enregistrez-le avec l’extension de fichier *.vstemplate* dans le même répertoire que votre projet. Ne l’ajoutez pas au projet dans Visual Studio.

1. Modifiez le fichier XML *.vstemplate* pour fournir des métadonnées de modèle de projet. Pour plus d’informations, consultez l’[exemple qui suit](#example).

1. Localisez l’élément `ProjectType` dans le fichier *.vstemplate*, puis affectez au texte la valeur `Web`.

1. Après l’élément `ProjectType`, ajoutez un élément `ProjectSubType` et affectez au texte la valeur du langage de programmation du modèle. Voici les valeurs pouvant être affectées comme langage de programmation :

    - CSharp
    - VisualBasic

    Exemple :

    ```xml
    <TemplateData>
        ...
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        ...
    </TemplateData>
    ```

1. Sélectionnez les fichiers présents dans votre modèle (en incluant le fichier *.vstemplate*), cliquez avec le bouton droit sur la sélection, puis choisissez **Envoyer vers** > **Dossier compressé**. Les fichiers sont compressés dans un fichier *.zip*.

1. Placez le fichier de modèle *.zip* dans le répertoire de modèles de projet Visual Studio. Par défaut, ce répertoire est *%USERPROFILE%\Documents\Visual Studio \<Version\>\ProjectTemplates*.

## <a name="example"></a>Exemple

L’exemple suivant montre un fichier *.vstemplate* de base pour un modèle de projet web :

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
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

[Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)  
[Informations de référence sur les schémas de modèles Visual Studio (extensibilité)](../extensibility/visual-studio-template-schema-reference.md)