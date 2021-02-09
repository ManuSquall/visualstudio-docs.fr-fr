---
title: Élément CustomParameters, (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément CustomParameters, et sur la façon dont il regroupe les paramètres personnalisés qui doivent être passés à l’Assistant modèle lorsque l’Assistant effectue des remplacements de paramètres.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a899790890bd299dcb77558d31499b0a61bcefe4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927130"
---
# <a name="customparameters-element-visual-studio-templates"></a>Élément CustomParameters, (modèles Visual Studio)
Regroupe les paramètres personnalisés qui doivent être passés à l’Assistant modèle lorsque l’Assistant effectue des remplacements de paramètres.

## <a name="syntax"></a>Syntaxe

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Contient le nom et la valeur d’un paramètre personnalisé à utiliser lors de la création d’un projet ou d’un élément à partir du modèle. Un élément `CustomParameter` peut ne contenir aucun élément `CustomParameters` ou en contenir plusieurs.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Spécifie le contenu du modèle.|

## <a name="remarks"></a>Notes

## <a name="example"></a>Exemple
 L’exemple suivant montre comment utiliser plusieurs paramètres personnalisés dans un modèle. Lorsqu’un projet ou un élément est créé à partir d’un modèle avec les paramètres personnalisés suivants, toutes les instances de `$color1$` et `$color2$` dans les fichiers de modèles sont remplacées par `Red` et `Blue` , respectivement.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Voir aussi
- [Élément CustomParameter (modèles Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
