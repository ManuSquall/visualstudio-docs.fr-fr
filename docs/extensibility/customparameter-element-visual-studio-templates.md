---
title: Élément CustomParameter (modèles Visual Studio) | Microsoft Docs
description: En savoir plus sur l’élément CustomParameter et sur la façon dont il contient un nom de paramètre personnalisé et une valeur à utiliser lorsqu’un projet ou un élément est créé à partir du modèle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98f7df8593b09acb2fa4db81ebfa734aeb1ddcaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947734"
---
# <a name="customparameter-element-visual-studio-templates"></a>Élément CustomParameter (modèles Visual Studio)
Contient le nom et la valeur d’un paramètre personnalisé à utiliser lors de la création d’un projet ou d’un élément à partir du modèle.

## <a name="syntax"></a>Syntaxe

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Name`|Obligatoire. Le nom du paramètre. Le format des paramètres est $*Name*$.|
|`Value`|Obligatoire. Valeur de remplacement pour le paramètre.|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Regroupe les paramètres personnalisés qui doivent être passés à l’Assistant modèle lorsque l’Assistant effectue des remplacements de paramètres.|

## <a name="remarks"></a>Notes
 Lorsqu’un modèle contient des `CustomParameter` éléments, chaque instance de l' `Name` attribut est remplacée par l' `Value` attribut dans les fichiers de projet ou d’élément créés.

## <a name="example"></a>Exemple
 L’exemple suivant montre comment utiliser plusieurs paramètres personnalisés dans un modèle. Lorsqu’un projet ou un élément est créé à partir d’un modèle avec les paramètres personnalisés suivants, toutes les instances de `$color1$` et `$color2$` dans les fichiers de modèles sont remplacées par `Red` et `Blue` , respectivement.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Voir aussi
- [Élément CustomParameters, (modèles Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
