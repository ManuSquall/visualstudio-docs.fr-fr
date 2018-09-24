---
title: Élément MaxFrameworkVersion (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12433fd96aee78c0f8f9ead3b531ae11b1d28f17
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636358"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Élément MaxFrameworkVersion (modèles Visual Studio)

Spécifie la version maximale du .NET Framework qui est requis par le modèle. Il détermine la valeur la plus élevée disponible dans le **Version du Framework cible** liste déroulante de la **nouveau projet** boîte de dialogue. Pour que les utilisateurs à être en mesure de sélectionner une version de framework, vous devez également spécifier [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) comme version minimale du .NET Framework pour le modèle.

> [!IMPORTANT]
> À compter de Visual Studio 2017 version 15.6, la **Version du Framework cible** liste déroulante n’est plus un filtre pour les modèles affichés dans le **modèles** section de la **denouveauprojet** boîte de dialogue. Au lieu de cela, le **Version du Framework cible** déroulante fonctionne comme un sélecteur de framework pour le modèle sélectionné.

 \<VSTemplate > \<TemplateData > \<MaxFrameworkVersion >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il est affiché dans un le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être le numéro de version le plus élevé du .NET Framework qui est autorisé par le modèle.

## <a name="remarks"></a>Notes

`MaxFrameworkVersion` est un élément facultatif. Le `MaxFrameworkVersion` élément doit être omis, sauf si elle est nécessaire, pour autant limiter par inadvertance les versions de la plage prise en charge de .NET Framework pour le modèle. Il doit également être omis si .NET Framework n’est pas applicable pour le modèle.

## <a name="example"></a>Exemple

L’exemple suivant illustre les métadonnées d’une norme [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modèle de classe.

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

Dans cet exemple, la version maximale du .NET Framework qui est requis par le modèle, représenté par `MaxFrameworkVersion`, est la version 4.7.1. Un projet créé avec ce modèle peut cibler les versions du .NET Framework jusqu'à la version 4.7.1.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)
