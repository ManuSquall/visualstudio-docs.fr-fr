---
title: Élément MaxFrameworkVersion (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément MaxFrameworkVersion et sur la façon dont il spécifie la version maximale du .NET Framework requis par le modèle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05d61e298c666d22df1af8d426cb0671feb8b9c5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090614"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Élément MaxFrameworkVersion (modèles Visual Studio)

Spécifie la version maximale du .NET Framework requis par le modèle. Elle détermine la valeur la plus élevée disponible dans la liste déroulante **version du Framework cible** de la boîte de dialogue **nouveau projet** . Pour que les utilisateurs puissent sélectionner une version d’infrastructure, vous devez également spécifier [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) comme version minimale .NET Framework pour le modèle.

> [!IMPORTANT]
> À compter de Visual Studio 2017 version 15,6, la liste déroulante **version cible du .NET Framework** n’est plus un filtre pour les modèles affichés dans la section **modèles** de la boîte de dialogue **nouveau projet** . Au lieu de cela, la liste déroulante **version cible du .NET Framework** fonctionne comme un sélecteur d’infrastructure pour le modèle sélectionné.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle et définit son mode d’affichage dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être le numéro de version le plus élevé du .NET Framework qui est autorisé par le modèle.

## <a name="remarks"></a>Notes

`MaxFrameworkVersion` est un élément facultatif. L' `MaxFrameworkVersion` élément doit être omis, sauf s’il est requis, afin de ne pas limiter par inadvertance la plage prise en charge des versions de .NET Framework pour le modèle. Elle doit également être omise si .NET Framework n’est pas applicable au modèle.

## <a name="example"></a>Exemple

L’exemple suivant illustre les métadonnées pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modèle de classe standard.

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

Dans cet exemple, la version maximale du .NET Framework requis par le modèle, représenté par `MaxFrameworkVersion` , est 4.7.1. Un projet créé avec ce modèle peut cibler .NET Framework versions jusqu’à la version 4.7.1.

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
