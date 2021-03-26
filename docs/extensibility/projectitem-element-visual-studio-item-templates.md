---
title: ProjectItem, élément (modèles d’élément Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément ProjectItem pour les modèles d’élément et sur la manière dont il accepte des attributs différents selon que le modèle est pour un projet ou un élément.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0910486202bca781ec19b6d5895e68ed93f8c3d5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068724"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem, élément (modèles d’élément Visual Studio)
Spécifie un fichier qui est inclus dans le modèle d’élément.

> [!NOTE]
> L' `ProjectItem` élément accepte des attributs différents selon que le modèle est destiné à un projet ou à un élément. Cette rubrique explique l' `ProjectItem` élément pour l’élément. Pour obtenir une explication de l' `ProjectItem` élément pour les modèles de projet, consultez [ProjectItem, élément (modèles de projet Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<ProjectItem>

## <a name="syntax"></a>Syntaxe

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

| Attribut | Description |
|---------------------| - |
| `SubType` | Attribut facultatif.<br /><br /> Spécifie le sous-type d’un élément dans un modèle d’élément multifichier. Cette valeur est utilisée pour déterminer l’éditeur qui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sera utilisé pour ouvrir l’élément. |
| `CustomTool` | Attribut facultatif.<br /><br /> Définit le CustomTool pour l’élément dans le fichier projet. |
| `ItemType` | Attribut facultatif.<br /><br /> Définit le ItemType pour l’élément dans le fichier projet. |
| `ReplaceParameters` | Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si l’élément a des valeurs de paramètres qui doivent être remplacées lors de la création d’un projet à partir du modèle. La valeur par défaut est `false`. |
| `TargetFileName` | Attribut facultatif.<br /><br /> Spécifie le nom de l’élément créé à partir du modèle. Cet attribut est utile pour l’utilisation du remplacement de paramètre pour créer un nom d’élément. |

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Spécifie le contenu du modèle.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 `string`Qui représente le nom d’un fichier dans le fichier *. zip* du modèle.

## <a name="remarks"></a>Notes
 `ProjectItem` est un enfant facultatif de `TemplateContent` .

 L' `TargetFileName` attribut peut être utilisé pour renommer des fichiers avec des paramètres. Par exemple, si le fichier *MyFile. vb* existe dans le répertoire racine du fichier *. zip* du modèle, mais que vous souhaitez que le fichier soit nommé en fonction du nom de fichier fourni par l’utilisateur dans la boîte de dialogue **Ajouter un nouvel élément** , utilisez le code XML suivant :

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Lorsqu’un élément est créé à partir de ce modèle, le nom de fichier est basé sur le nom que l’utilisateur a entré dans la boîte de dialogue **Ajouter un nouvel élément** . Cela est utile lors de la création de modèles d’élément multifichier. Pour plus d’informations, consultez [Comment : créer des modèles d’élément multifichier](../ide/how-to-create-multi-file-item-templates.md) et des [paramètres de modèle](../ide/template-parameters.md).

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées pour le modèle d’élément standard d’une [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Guide pratique pour créer des modèles d’élément multifichiers](../ide/how-to-create-multi-file-item-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
