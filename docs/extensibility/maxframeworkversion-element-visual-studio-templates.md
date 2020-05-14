---
title: MaxFrameworkVersion Element (Visual Studio Templates) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702618"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion élément (modèles Visual Studio)

Spécifie la version maximale du cadre .NET qui est requis par le modèle. Il détermine la valeur la plus élevée disponible dans le retrait de la **version-cadre cible** du dialogue **du nouveau projet.** Pour que les utilisateurs puissent sélectionner une version-cadre, vous devez également spécifier [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) comme version cadre minimale .NET pour le modèle.

> [!IMPORTANT]
> À partir de Visual Studio 2017 version 15.6, le dropdown **Target Framework Version** n’est plus un filtre pour les modèles affichés dans la section **Templates** du dialogue **New Project.** Au lieu de cela, le décrochage de la **version-cadre cible** fonctionne comme un cueilleur-cadre pour le modèle sélectionné.

 \<VSTemplate> \<TemplateData> \<MaxFrameworkVersion>

## <a name="syntax"></a>Syntaxe

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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

 Le texte doit être le numéro de version le plus élevé du cadre .NET qui est autorisé par le modèle.

## <a name="remarks"></a>Notes

`MaxFrameworkVersion` est un élément facultatif. L’élément `MaxFrameworkVersion` doit être omis à moins qu’il ne soit nécessaire, afin de ne pas limiter par inadvertance la plage prise en charge des versions cadre .NET pour le modèle. Il devrait également être omis si .NET Framework n’est pas applicable au modèle.

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

Dans cet exemple, la version maximale du cadre .NET qui `MaxFrameworkVersion`est exigée par le modèle, représentée par , est de 4.7.1. Un projet créé avec ce modèle peut cibler les versions cadres .NET jusqu’à 4.7.1.

## <a name="see-also"></a>Voir aussi

- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’objets](../ide/creating-project-and-item-templates.md)
