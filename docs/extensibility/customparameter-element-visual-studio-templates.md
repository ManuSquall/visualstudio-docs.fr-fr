---
title: CustomParameter Element (Visual Studio Templates) Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739433"
---
# <a name="customparameter-element-visual-studio-templates"></a>Élément CustomParameter (modèles Visual Studio)
Contient un nom de paramètre personnalisé et la valeur à utiliser lorsqu’un projet ou un élément est créé à partir du modèle.

## <a name="syntax"></a>Syntaxe

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`Name`|Obligatoire. Le nom du paramètre. Le format pour les paramètres est $*nom*$.|
|`Value`|Obligatoire. La valeur de remplacement du paramètre.|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Regroupe les paramètres personnalisés qui doivent être transmis à l’assistant modèle lorsque l’assistant effectue des remplacements de paramètres.|

## <a name="remarks"></a>Notes
 Lorsqu’un `CustomParameter` modèle contient des `Name` éléments, chaque `Value` cas l’attribut est remplacé par l’attribut dans les fichiers de projet ou d’élément créés.

## <a name="example"></a>Exemple
 L’exemple suivant montre comment utiliser plusieurs paramètres personnalisés dans un modèle. Lorsqu’un projet ou un élément est créé à partir `$color1$` d’un modèle avec les paramètres personnalisés suivants, tous les cas et `$color2$` dans les fichiers de modèle seront remplacés par `Red` et, `Blue`respectivement.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Voir aussi
- [Élément CustomParameters (modèles Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
