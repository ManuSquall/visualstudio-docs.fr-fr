---
title: Élément MaxFrameworkVersion (modèles Visual Studio) | Documents Microsoft
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
ms.openlocfilehash: 4bc28fcc35a4a59852ef6864886acff4dc87ef60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Élément MaxFrameworkVersion (modèles Visual Studio)

Spécifie la version maximale du .NET Framework requise par le modèle. Il détermine la valeur la plus élevée disponible dans le **Version du Framework cible** liste déroulante de la **nouveau projet** boîte de dialogue. Pour que les utilisateurs puissent sélectionner une version de framework, vous devez également spécifier [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) en tant que la version minimale de .NET Framework pour le modèle.

> [!IMPORTANT]
> À compter de Visual Studio 2017 version 15,6, le **Version du Framework cible** liste déroulante n’est plus un filtre pour les modèles affichés dans le **modèles** section de la **denouveauprojet** boîte de dialogue. Au lieu de cela, le **Version du Framework cible** déroulante fonctionne comme un sélecteur de framework pour le modèle sélectionné.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il est affiché, que ce soit le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être le numéro de version le plus élevé du .NET Framework qui est autorisé par le modèle.

## <a name="remarks"></a>Notes

`MaxFrameworkVersion` est un élément facultatif. Le `MaxFrameworkVersion` élément doit être omis sauf s’il est nécessaire, pour autant par inadvertance limiter les versions de la plage prise en charge de .NET Framework pour le modèle. Il doit également être omis si .NET Framework n’est pas applicable pour le modèle.

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

Dans cet exemple, la version maximale du .NET Framework requise par le modèle, représenté par `MaxFrameworkVersion`, est 4.7.1. Un projet créé avec ce modèle peut cibler les versions du .NET Framework jusqu'à 4.7.1.

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
