---
title: Élément requiredFrameworkVersion (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701510"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Élément RequiredFrameworkVersion (modèles Visual Studio)

Spécifie la version minimale du cadre .NET qui est requis par le modèle. Il entraîne l’affichage de la **version-cadre cible** dans le dialogue **du nouveau projet.** L’élément `RequiredFrameworkVersion` détermine également la valeur la plus faible disponible dans le décrochage.

> [!IMPORTANT]
> À partir de Visual Studio 2017 version 15.6, le dropdown **Target Framework Version** n’est plus un filtre pour les modèles affichés dans la section **Templates** du dialogue **New Project.** Au lieu de cela, le décrochage fonctionne comme un cueilleur-cadre pour le modèle sélectionné.

 \<VSTemplate> \<TemplateData> \<RequiredFrameworkVersion>

## <a name="syntax"></a>Syntaxe

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Catégorise le modèle et définit comment il est affiché dans le **nouveau projet** ou la boîte de dialogue Add **New Item.**|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être le numéro de version minimum du cadre .NET qui est requis pour le modèle.

## <a name="remarks"></a>Notes

`RequiredFrameworkVersion` est un élément facultatif. Utilisez cet élément uniquement si le modèle prend en charge une version minimale spécifique (et des versions ultérieures s’il y a eu) du cadre .NET. Si vous `RequiredFrameworkVersion` spécifiez l’élément et que votre modèle ne prend pas en charge une version minimale spécifique du cadre .NET, le dropdown de la **version cadre cible** s’affiche lorsqu’il n’est pas applicable.

## <a name="example"></a>Exemple

L’exemple suivant illustre les métadonnées d’un modèle de classe standard. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

Dans cet exemple, la version minimale du cadre .NET qui `RequiredFrameworkVersion`est requis par le modèle, représenté par , est de 3,0. Un projet créé avec ce modèle peut cibler les versions cadres .NET à partir de 3.0.

## <a name="see-also"></a>Voir aussi

- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Vue d’ensemble du ciblage des frameworks](../ide/visual-studio-multi-targeting-overview.md)
