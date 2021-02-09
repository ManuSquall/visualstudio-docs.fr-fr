---
title: Élément ProvideDefaultName (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément ProvideDefaultName et sur la façon dont il spécifie si Visual Studio génère un nom Visual Studio par défaut dans la boîte de dialogue Ajouter un nouvel élément ou nouveau projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f207a4c86a9c76f009341f96a7d562da1e8fb33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910955"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Élément ProvideDefaultName (modèles Visual Studio)
Spécifie si le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] système de projet génère un nom par défaut pour le modèle dans la boîte de dialogue **Ajouter un nouvel élément** ou **nouveau projet** .

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

## <a name="syntax"></a>Syntaxe

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
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

 Le texte doit être `true` ou `false` , indiquant s’il faut ou non générer un nom par défaut pour le modèle dans la boîte de dialogue **Ajouter un nouvel élément** ou **nouveau projet** .

## <a name="remarks"></a>Notes
 `ProvideDefaultName` est un élément facultatif. La valeur par défaut est `true`.

 Si l' `ProvideDefaultName` élément est `false` , les zones **nom** des boîtes de dialogue **Ajouter un nouvel élément** et **nouveau projet** contiennent la valeur `<Enter_name>` .

 Utilisez l’élément [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) pour spécifier le nom par défaut du projet ou de l’élément dans les boîtes de dialogue **Ajouter un nouvel élément** et **nouveau projet** . Lorsque la valeur de l' `ProvideDefaultName` élément est `true` , l’omission de l' `DefaultName` élément pour les projets remplit la boîte de dialogue avec le nom du modèle, autrement dit, la valeur de l’élément [Name](../extensibility/name-element-visual-studio-templates.md) .

## <a name="example"></a>Exemple
 L’exemple de code suivant affecte `ProvideDefaultName` à l’élément la valeur `false` .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
