---
title: Élément RequiredFrameworkVersion (modèles Visual Studio) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701510"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Élément RequiredFrameworkVersion (modèles Visual Studio)

Spécifie la version minimale du .NET Framework requis par le modèle. Cela entraîne l’affichage de la liste déroulante **version du Framework cible** dans la boîte de dialogue **nouveau projet** . L' `RequiredFrameworkVersion` élément détermine également la valeur la plus basse disponible dans la liste déroulante.

> [!IMPORTANT]
> À compter de Visual Studio 2017 version 15,6, la liste déroulante **version cible du .NET Framework** n’est plus un filtre pour les modèles affichés dans la section **modèles** de la boîte de dialogue **nouveau projet** . Au lieu de cela, la liste déroulante fonctionne comme un sélecteur d’infrastructure pour le modèle sélectionné.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle et définit son mode d’affichage dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être le numéro de version minimal du .NET Framework requis pour le modèle.

## <a name="remarks"></a>Notes

`RequiredFrameworkVersion` est un élément facultatif. Utilisez cet élément uniquement si le modèle prend en charge une version minimale spécifique (et les versions ultérieures, le cas échéant) du .NET Framework. Si vous spécifiez l' `RequiredFrameworkVersion` élément et que votre modèle ne prend pas en charge une version minimale spécifique du .NET Framework, la liste déroulante **version du Framework cible** s’affiche lorsqu’elle n’est pas applicable.

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

Dans cet exemple, la version minimale du .NET Framework qui est requis par le modèle, représenté par `RequiredFrameworkVersion` , est 3,0. Un projet créé avec ce modèle peut cibler des versions de .NET Framework à partir de 3,0.

## <a name="see-also"></a>Voir aussi

- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Vue d’ensemble du ciblage des frameworks](../ide/visual-studio-multi-targeting-overview.md)
