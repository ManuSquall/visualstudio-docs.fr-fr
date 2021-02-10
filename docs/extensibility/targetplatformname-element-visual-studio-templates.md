---
title: Élément TargetPlatformName (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément TargetPlatformName et sur la façon dont il spécifie la plateforme ciblée par le modèle de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f2b8903c99e5bd2f62587b7921be855e4ed6323
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938770"
---
# <a name="targetplatformname-element-visual-studio-templates"></a>Élément TargetPlatformName (modèles Visual Studio)
Spécifie la plateforme ciblée par le modèle de projet. Cet élément permet de spécifier qu’un modèle de projet est utilisé pour créer des applications [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] .

## <a name="syntax"></a>Syntaxe

```xml
<VSTemplate>
    <TemplateData>
        <TargetPlatformName> OperatingSystem</TargetPlatformName>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|Spécifie la version du système d’exploitation ciblée par le modèle de projet.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

## <a name="remarks"></a>Notes
 Le texte doit être **Windows**.

## <a name="example"></a>Exemple
 Cet exemple spécifie que le modèle de projet cible [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou version ultérieure.

```xml
<VSTemplate Type="Project" Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
        <RequiredPlatformVersion>8</RequiredPlatformVersion>
    </TemplateData>
    <TemplateContent> </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Voir aussi
- [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
