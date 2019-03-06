---
title: Élément RequiredFrameworkVersion (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40eefc62eef318bcd9c52a1cbbb966377b3616f8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946995"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Élément RequiredFrameworkVersion (modèles Visual Studio)

Spécifie la version minimale du .NET Framework qui est requis par le modèle. Elle force le **Version du Framework cible** dropdown à afficher dans le **nouveau projet** boîte de dialogue. Le `RequiredFrameworkVersion` élément détermine également la valeur la plus basse disponible dans la liste déroulante.

> [!IMPORTANT]
> À compter de Visual Studio 2017 version 15.6, la **Version du Framework cible** liste déroulante n’est plus un filtre pour les modèles affichés dans le **modèles** section de la **denouveauprojet** boîte de dialogue. Au lieu de cela, la liste déroulante fonctionne comme un sélecteur de framework pour le modèle sélectionné.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il est affiché dans un le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être le numéro de version minimale du .NET Framework qui est requise pour le modèle.

## <a name="remarks"></a>Notes

`RequiredFrameworkVersion` est un élément facultatif. Utilisez cet élément uniquement si le modèle prend en charge une version minimale spécifique (et versions ultérieures, le cas échéant) du .NET Framework. Si vous spécifiez le `RequiredFrameworkVersion` élément et votre modèle ne prend en charge une version minimale spécifique du .NET Framework, le **Version du Framework cible** liste déroulante affiche lorsqu’il n’est pas applicable.

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

Dans cet exemple, la version minimale du .NET Framework qui est requis par le modèle, représenté par `RequiredFrameworkVersion`, est 3.0. Un projet créé avec ce modèle peut cibler les versions du .NET Framework à partir de 3.0.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Cibler une version spécifique de .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
