---
title: L’élément RequiredFrameworkVersion (modèles Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc1a138c50c0fe13962f6601449eb3498d90398
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137834"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Élément RequiredFrameworkVersion (modèles Visual Studio)

Spécifie la version minimale du .NET Framework requise par le modèle. Elle force le **Version du Framework cible** liste déroulante s’affiche dans le **nouveau projet** boîte de dialogue. Le `RequiredFrameworkVersion` élément détermine également la valeur la plus basse disponible dans la liste déroulante.

> [!IMPORTANT]
> À compter de Visual Studio 2017 version 15,6, le **Version du Framework cible** liste déroulante n’est plus un filtre pour les modèles affichés dans le **modèles** section de la **denouveauprojet** boîte de dialogue. Au lieu de cela, la liste déroulante fonctionne comme un sélecteur de framework pour le modèle sélectionné.

 \<VSTemplate > \<TemplateData > \<RequiredFrameworkVersion >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il est affiché, que ce soit le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être le numéro de version minimale du .NET Framework qui est requise pour le modèle.

## <a name="remarks"></a>Notes

`RequiredFrameworkVersion` est un élément facultatif. Utilisez cet élément uniquement si le modèle prend en charge une version minimale spécifique (et versions ultérieures, le cas échéant) du .NET Framework. Si vous spécifiez la `RequiredFrameworkVersion` votre modèle et élément ne prend en charge une version minimale spécifique du .NET Framework, le **Version du Framework cible** liste déroulante affiche lorsqu’il n’est pas applicable.

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

Dans cet exemple, la version minimale du .NET Framework requise par le modèle, représenté par `RequiredFrameworkVersion`, est 3.0. Un projet créé avec ce modèle peut cibler les versions du .NET Framework à partir de 3.0.

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Cibler une version spécifique du .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
