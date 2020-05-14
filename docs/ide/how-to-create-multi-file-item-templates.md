---
title: Création de modèles d’élément multifichier
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e8a6e5358a87e3d64b341c89b8ffd4cd3cf3e325
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593731"
---
# <a name="how-to-create-multi-file-item-templates"></a>Guide pratique pour créer des modèles d’élément multifichiers

Il arrive que les modèles d’élément spécifient un seul élément, mais cet élément est parfois composé de plusieurs fichiers. Par exemple, un modèle d’élément Windows Forms exige les trois fichiers suivants :

- Un fichier qui contient le code du formulaire

- Un fichier qui contient les informations relatives au concepteur du formulaire

- Un fichier qui contient les ressources incorporées du formulaire

Les modèles d’élément multifichiers exigent des paramètres pour garantir que les extensions de fichier appropriées sont utilisées lors de la création de l’élément. Si vous créez un modèle d’élément multifichier à l’aide de l’**Assistant Exportation de modèle**, ces paramètres sont générés automatiquement et aucune autre modification n’est nécessaire.

## <a name="use-the-export-template-wizard"></a>Utiliser l’Assistant Exportation de modèle

Vous pouvez créer un modèle d’élément multifichier de la même manière qu’un modèle d’élément à un seul fichier. Consultez [Guide pratique pour créer des modèles d’élément](../ide/how-to-create-item-templates.md). Dans la page **Sélectionner l’élément à exporter** de l’Assistant, sélectionnez le fichier qui contient des fichiers dépendants (par exemple, un fichier de formulaire Windows Forms). L’Assistant inclut automatiquement tous les fichiers dépendants, comme les fichiers du concepteur et les fichiers de ressources, dans le modèle.

## <a name="manually-create-a-multi-file-item-template"></a>Créer manuellement un modèle d’élément multifichier

1. Créez le modèle d’élément comme vous le feriez manuellement pour un modèle d’élément à un seul fichier, mais incluez chaque fichier qui constitue l’élément multifichier.

1. Dans le fichier XML *.vstemplate*, ajoutez un élément `ProjectItem` pour chaque fichier, puis ajoutez un attribut `TargetFileName` à cet élément. Affectez à l’attribut `TargetFileName` la valeur *$fileinputname$.FileExtension*, où *FileExtension* représente l’extension du fichier inclus dans le modèle. Par exemple :

    ```xml
    <ProjectItem TargetFileName="$fileinputname$.vb">
        Form1.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
        Form1.Designer.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.resx">
        Form1.resx
    </ProjectItem>
    ```

     > [!NOTE]
     > Quand vous ajoutez à un projet un élément dérivé de ce modèle, les noms de fichiers dérivent du nom que l’utilisateur entre dans la boîte de dialogue **Ajouter un nouvel élément**.

1. Sélectionnez les fichiers à inclure dans votre modèle, cliquez à droite sur la sélection et choisissez **Envoyer à** > **compressé (zippé) dossier**.

   Les fichiers que vous avez sélectionnés sont compressés dans un fichier *.zip.*

1. Copiez le fichier *.zip* à l’emplacement des modèles d’élément utilisateur. Par défaut, le répertoire est : *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates*. Pour plus d’informations, voir [Comment : Localiser et organiser des modèles](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Fermez Visual Studio, puis rouvrez-le.

1. Créez un nouveau projet ou ouvrez un projet existant, puis choisissez **le projet** > **Ajouter un nouvel article** ou appuyer sur **Ctrl**+**Shift**+**A**.

   Le modèle d’élément multifichier apparaît dans la boîte de dialogue **Ajouter un nouvel élément**.

## <a name="example"></a> Exemple

L’exemple suivant présente un modèle Windows Forms. Quand vous créez un élément à partir de ce modèle, les noms des trois fichiers créés correspondent aux noms entrés dans la boîte de dialogue **Ajouter un nouvel élément**.

```xml
<VSTemplate Version="2.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-file Item Template</Name>
        <Icon>Icon.ico</Icon>
        <Description>An example of a multi-file item template</Description>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">
            Form1.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
            Form1.Designer.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.resx">
            Form1.resx
        </ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi

- [Créer des modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
- [Comment : Créer des modèles d’objets](../ide/how-to-create-item-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Comment : Remplacer les paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md)
