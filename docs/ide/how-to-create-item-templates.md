---
title: Créer des modèles d’élément pour Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 342b7ebd17280c47296fae43c6541a5e969ad5f3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31954660"
---
# <a name="how-to-create-item-templates"></a>Guide pratique pour créer des modèles d’élément

Cet article vous montre comment créer un modèle d’élément à l’aide de l’**Assistant Exportation de modèle**. Si votre modèle comprend plusieurs fichiers, consultez [Guide pratique pour créer des modèles d’élément multifichiers](../ide/how-to-create-multi-file-item-templates.md).

## <a name="to-add-a-user-item-template-to-the-add-new-item-dialog-box"></a>Pour ajouter un modèle d’élément utilisateur à la boîte de dialogue Ajouter un nouvel élément

1. Créez ou ouvrez un projet dans Visual Studio.

1. Ajoutez un élément au projet et modifiez-le si vous le souhaitez.

1. Modifiez le fichier de code pour indiquer où le remplacement de paramètres doit avoir lieu. Pour plus d’informations, consultez [Guide pratique pour substituer des paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md).

1. Dans le menu **Projet**, choisissez **Exporter le modèle**.

1. Dans la page **Choisir un type de modèle** choisissez **Modèle d’élément**, sélectionnez le projet qui contient l’élément, puis choisissez **Suivant**.

1. Dans la page **Sélectionner l’élément à exporter**, choisissez l’élément pour lequel créer un modèle, puis choisissez **Suivant**.

1. Dans la page **Sélectionner les références aux éléments**, sélectionnez les références d’assembly à inclure dans le modèle, puis choisissez **Suivant**.

1. Dans la page **Sélectionner les options du modèle**, entrez le nom du modèle et éventuellement une description, une image d’icône et une image d’aperçu, puis choisissez **Terminer**.

    Les fichiers du modèle sont ajoutés à un fichier *.zip* et copiés dans le répertoire que vous avez spécifié dans l’Assistant. L’emplacement par défaut est : *%USERPROFILE%\Documents\Visual Studio \<version\>\My Exported Templates*.

1. Si vous n’avez pas sélectionné l’option **Importer automatiquement le modèle dans Visual Studio** dans l’**Assistant Exportation de modèle**, recherchez le modèle exporté. Copiez-le ensuite dans le répertoire des modèles d’éléments utilisateur. L’emplacement par défaut est : *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ItemTemplates*.

1. Fermez Visual Studio, puis rouvrez-le.

1. Créez un projet ou ouvrez un projet existant, puis choisissez **Projet** > **Ajouter un nouvel élément**, ou appuyez sur **Ctrl**+**Maj**+**A**.

   Le modèle d’élément apparaît dans la boîte de dialogue **Ajouter un nouvel élément**. Si vous avez ajouté une description dans l’**Assistant Exportation de modèle**, la description s’affiche dans la partie droite de la boîte de dialogue.

## <a name="to-enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Pour permettre l’utilisation du modèle d’élément dans un projet d’application Windows universelle

L’Assistant effectue une grande partie du travail nécessaire à la création d’un modèle de base, mais dans de nombreux cas, vous devez modifier manuellement le fichier *.vstemplate* après avoir exporté le modèle. Par exemple, si vous souhaitez que l’élément s’affiche dans la boîte de dialogue **Ajouter un nouvel élément** pour un projet d’application Windows universelle, vous devez effectuer quelques étapes supplémentaires.

1. Suivez les étapes de la section précédente pour exporter un modèle d’élément.

1. Extrayez le fichier *.zip* créé, puis ouvrez le fichier *.vstemplate* dans Visual Studio.

1. Pour un projet Windows universel C#, ajoutez le code XML suivant à l’intérieur de l’élément `<TemplateData>` :

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. Dans Visual Studio, enregistrez le fichier *.vstemplate*, puis fermez-le.

1. Copiez et collez le fichier *.vstemplate* dans le fichier *.zip* d’origine.

     Si la boîte de dialogue **Copier le fichier** apparaît, sélectionnez l’option **Copier et remplacer**.

Vous pouvez maintenant ajouter un élément basé sur ce modèle à un projet Windows universel à partir de la boîte de dialogue **Ajouter un nouvel élément**.

## <a name="to-enable-templates-for-specific-project-subtypes"></a>Pour activer les modèles pour des sous-types de projet spécifiques

Vous pouvez spécifier que votre modèle doit uniquement apparaître pour certains sous-types de projet, comme Windows, Office, Base de données ou Web.

1. Localisez l’élément `ProjectType` dans le fichier *.vstemplate* du modèle d’élément.

1. Ajoutez un élément [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) juste après l’élément `ProjectType`.

1. Affectez au texte de l'élément l'une des valeurs suivantes :

    - Windows
    - Office
    - Base de données
    - Web

Par exemple : `<ProjectSubType>Database</ProjectSubType>`.

L’exemple suivant présente un modèle d’élément disponible pour les projets **Office**.

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Pour créer manuellement un modèle d'élément sans utiliser l'Assistant Exportation de modèle

Dans certains cas, vous pouvez avoir envie de créer un modèle d’élément manuellement, à partir de zéro.

1. Créez un projet et un élément de projet.

1. Modifiez l'élément de projet jusqu'à ce qu'il soit prêt à être enregistré en tant que modèle.

1. Modifiez le fichier de code pour indiquer où le remplacement de paramètres doit avoir lieu, le cas échéant. Pour plus d’informations sur le remplacement de paramètres, consultez [Guide pratique pour substituer des paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md).

1. Créez un fichier XML et enregistrez-le avec l’extension de nom de fichier *.vstemplate* dans le même répertoire que votre fichier d’élément de projet.

1. Modifiez le fichier XML *.vstemplate* pour fournir des métadonnées de modèle d’élément. Pour plus d’informations, consultez [Informations de référence sur les schémas de modèles (extensibilité)](../extensibility/visual-studio-template-schema-reference.md), ainsi que l’exemple de la section précédente.

1. Enregistrez le fichier *.vstemplate*, puis fermez-le.

1. Dans l’**Explorateur Windows**, sélectionnez les fichiers à inclure dans votre modèle. Cliquez avec le bouton droit sur la sélection, puis choisissez **Envoyer vers** > **Dossier compressé**. Les fichiers que vous avez sélectionnés sont compressés dans un fichier *.zip*.

1. Copiez le fichier *.zip*, puis collez-le à l’emplacement du modèle d’élément utilisateur. Dans Visual Studio 2017, le répertoire par défaut est *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*. Pour plus d’informations, consultez [Guide pratique pour localiser et organiser les modèles de projet et d’élément](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Voir aussi

- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Guide pratique pour créer des modèles d’élément multifichiers](../ide/how-to-create-multi-file-item-templates.md)
- [Informations de référence sur les schémas de modèles Visual Studio (extensibilité)](../extensibility/visual-studio-template-schema-reference.md)
