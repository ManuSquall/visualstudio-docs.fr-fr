---
title: ProvideDefaultName, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2a19d6a93b709128e8750b6cea82d067b77db98
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335819"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName, élément (modèles Visual Studio)
Spécifie si le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] système de projet génère un nom par défaut pour le modèle dans le **ajouter un nouvel élément** ou **nouveau projet** boîte de dialogue.

 \<VSTemplate> \<TemplateData> \<ProvideDefaultName>

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

 Le texte doit être `true` ou `false`, indiquant s’il faut générer un nom par défaut pour le modèle dans le **ajouter un nouvel élément** ou **nouveau projet** boîte de dialogue.

## <a name="remarks"></a>Notes
 `ProvideDefaultName` est un élément facultatif. La valeur par défaut est `true`.

 Si le `ProvideDefaultName` élément est `false`, le **nom** cases de la **ajouter un nouvel élément** et **nouveau projet** boîtes de dialogue contiennent la valeur `<Enter_name>`.

 Utilisez le [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) élément pour spécifier le nom par défaut du projet ou élément dans le **ajouter un nouvel élément** et **nouveau projet** boîtes de dialogue. Lorsque la valeur de la `ProvideDefaultName` élément est `true`, omission de la `DefaultName` , élément pour les projets remplit la boîte de dialogue avec le nom du modèle, autrement dit, la valeur à partir de la [nom](../extensibility/name-element-visual-studio-templates.md) élément.

## <a name="example"></a>Exemple
 Le code suivant exemple définit le `ProvideDefaultName` élément à `false`.

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
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
