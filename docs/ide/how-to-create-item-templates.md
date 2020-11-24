---
title: Créer des modèles d’élément
description: Découvrez comment utiliser l’Assistant exportation de modèle pour créer un modèle d’élément dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: abf058526a6ff48a37d4c7585e7deabe1decb14a
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597273"
---
# <a name="how-to-create-item-templates"></a>Guide pratique pour créer des modèles d’élément

Cet article vous montre comment créer un modèle d’élément à l’aide de l’**Assistant Exportation de modèle**. Si votre modèle comprend plusieurs fichiers, consultez [Guide pratique pour créer des modèles d’élément multifichiers](../ide/how-to-create-multi-file-item-templates.md).

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Ajouter un modèle d’élément à la boîte de dialogue Ajouter un nouvel élément

1. Créez ou ouvrez un projet dans Visual Studio.

1. Ajoutez un élément au projet et modifiez-le si vous le souhaitez.

1. Modifiez le fichier de code pour indiquer où le remplacement de paramètres doit avoir lieu. Pour plus d’informations, consultez [Guide pratique pour substituer des paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md).

1. Dans le menu **projet** , choisissez **Exporter le modèle**.

1. Dans la page **Choisir un type de modèle** choisissez **Modèle d’élément**, sélectionnez le projet qui contient l’élément, puis choisissez **Suivant**.

1. Dans la page **Sélectionner l’élément à exporter**, choisissez l’élément pour lequel créer un modèle, puis choisissez **Suivant**.

1. Dans la page **Sélectionner les références aux éléments**, sélectionnez les références d’assembly à inclure dans le modèle, puis choisissez **Suivant**.

1. Dans la page **Sélectionner les options du modèle**, entrez le nom du modèle et éventuellement une description, une image d’icône et une image d’aperçu, puis choisissez **Terminer**.

    Les fichiers du modèle sont ajoutés à un fichier *.zip* et copiés dans le répertoire que vous avez spécifié dans l’Assistant. L’emplacement par défaut est *%USERPROFILE%\Documents\Visual Studio \Mes Exported \<version\> Templates*.

1. Si vous n’avez pas sélectionné l’option **Importer automatiquement le modèle dans Visual Studio** dans l’**Assistant Exportation de modèle**, recherchez le modèle exporté. Copiez-le ensuite dans le répertoire des modèles d’éléments utilisateur. L’emplacement par défaut est *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ItemTemplates*.

1. Fermez Visual Studio, puis rouvrez-le.

1. Créez un projet ou ouvrez un projet existant, puis choisissez **projet**  >  **Ajouter un nouvel élément** ou appuyez sur **CTRL** + **MAJ** + **a**.

   Le modèle d’élément apparaît dans la boîte de dialogue **Ajouter un nouvel élément**. Si vous avez ajouté une description dans l’**Assistant Exportation de modèle**, la description s’affiche dans la partie droite de la boîte de dialogue.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Permettre l’utilisation du modèle d’élément dans un projet d’application Windows universel

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

## <a name="enable-templates-for-specific-project-subtypes"></a>Activer des modèles pour des sous-types de projet spécifiques

Vous pouvez spécifier que votre modèle doit uniquement apparaître pour certains sous-types de projet, comme Windows, Office, Base de données ou Web.

1. Localisez l’élément `ProjectType` dans le fichier *.vstemplate* du modèle d’élément.

1. Ajoutez un élément [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) juste après l’élément `ProjectType`.

1. Affectez au texte de l'élément l'une des valeurs suivantes :

    - Windows
    - Office
    - Base de données
    - Web

Par exemple : `<ProjectSubType>Database</ProjectSubType>`.

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

## <a name="manually-create-an-item-template"></a>Créer manuellement un modèle d’élément

Dans certains cas, vous pouvez avoir envie de créer un modèle d’élément manuellement, à partir de zéro.

1. Créez un projet et un élément de projet.

2. Modifiez l'élément de projet jusqu'à ce qu'il soit prêt à être enregistré en tant que modèle.

3. Modifiez le fichier de code pour indiquer où le remplacement de paramètres doit avoir lieu, le cas échéant. Pour plus d’informations sur le remplacement de paramètres, consultez [Guide pratique pour substituer des paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md).

4. Créez un fichier XML et enregistrez-le avec l’extension de nom de fichier *.vstemplate* dans le même répertoire que votre fichier d’élément de projet.

5. Modifiez le fichier XML *.vstemplate* pour fournir des métadonnées de modèle d’élément. Pour plus d’informations, consultez [Informations de référence sur les schémas de modèles (extensibilité)](../extensibility/visual-studio-template-schema-reference.md), ainsi que l’exemple de la section précédente.

6. Enregistrez le fichier *.vstemplate*, puis fermez-le.

7. Dans l’**Explorateur Windows**, sélectionnez les fichiers à inclure dans votre modèle. Cliquez avec le bouton droit sur la sélection, puis choisissez **Envoyer vers** le  >  **dossier compressé**. Les fichiers que vous avez sélectionnés sont compressés dans un fichier *. zip* .

::: moniker range="vs-2017"

8. Copiez le fichier *.zip*, puis collez-le à l’emplacement du modèle d’élément utilisateur. Le répertoire par défaut est *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*. Pour plus d’informations, consultez [Guide pratique pour localiser et organiser les modèles de projet et d’élément](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

8. Copiez le fichier *.zip*, puis collez-le à l’emplacement du modèle d’élément utilisateur. Le répertoire par défaut est *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*. Pour plus d’informations, consultez [Guide pratique pour localiser et organiser les modèles de projet et d’élément](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Guide pratique pour créer des modèles d’élément multifichiers](../ide/how-to-create-multi-file-item-templates.md)
- [Informations de référence sur les schémas de modèles Visual Studio (extensibilité)](../extensibility/visual-studio-template-schema-reference.md)
