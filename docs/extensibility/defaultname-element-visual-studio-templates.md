---
title: Élément De Nom De défaut (Modèles de studio visuel) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92bd29824cf1d3b91a7bdaa7220479c583ad0f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712309"
---
# <a name="defaultname-element-visual-studio-templates"></a>Élément DefaultName (modèles Visual Studio)
Spécifie le nom que le système de projet Visual Studio générera pour le projet ou l’élément lorsqu’il sera créé.

 \<VSTemplate> \<TemplateData> \<DefaultName>

## <a name="syntax"></a>Syntaxe

```
<DefaultName>
    Default Project Name
</DefaultName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Ce texte spécifie le nom par défaut du projet ou de l’élément.

## <a name="remarks"></a>Notes
 `DefaultName` est un élément facultatif.

 Pour les projets, cet élément spécifie le nom de l’annuaire qui stocke le projet sur disque. Pour les éléments, il spécifie le nom de fichier du fichier source.

 Lorsque vous créez un projet ou un élément, vous pouvez modifier le nom par défaut à l’aide de **l’option Nom,** qui est disponible à partir de la boîte de dialogue **New Project** ou ajouter la boîte de dialogue **Nouvel Élément.**

 Si vous ne voulez pas que le système de projet génère le nom par défaut `False`du projet ou de l’élément, définissez l’élément [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) à .

## <a name="example"></a>Exemple
 L’exemple suivant illustre les métadonnées du [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modèle d’élément standard pour une classe.

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
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
