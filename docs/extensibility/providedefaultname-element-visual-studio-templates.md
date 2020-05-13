---
title: ProvideDefaultName Element (Visual Studio Templates) Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701718"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Élément ProvideDefaultName (modèles Visual Studio)
Précise si le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] système de projet générera un nom par défaut pour le modèle dans la boîte de dialogue **Add New Item** ou New **Project.**

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

 Le texte doit `true` `false`être soit ou , indiquant si oui ou non pour générer un nom par défaut pour le modèle dans la boîte de dialogue **Add New Item** ou New **Project.**

## <a name="remarks"></a>Notes
 `ProvideDefaultName` est un élément facultatif. La valeur par défaut est `true`.

 Si `ProvideDefaultName` l’élément est `false`, les boîtes **nominatives** de **l’Add New Item** et les boîtes de dialogue nouveau **projet** contiennent la valeur `<Enter_name>`.

 Utilisez l’élément [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) pour spécifier le nom par défaut du projet ou de l’élément dans les boîtes de dialogue **Add New Item** et New **Project.** Lorsque la valeur `ProvideDefaultName` de `true`l’élément `DefaultName` est, l’omission de l’élément pour les projets remplit la boîte de dialogue avec le nom du modèle, c’est-à-dire la valeur de l’élément [Nom.](../extensibility/name-element-visual-studio-templates.md)

## <a name="example"></a>Exemple
 L’exemple de `ProvideDefaultName` code `false`suivant définit l’élément à .

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
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
