---
title: CustomParameters Element (Visual Studio Templates) Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739409"
---
# <a name="customparameters-element-visual-studio-templates"></a>Élément CustomParameters (modèles Visual Studio)
Regroupe les paramètres personnalisés qui doivent être transmis à l’assistant modèle lorsque l’assistant effectue des remplacements de paramètres.

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
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Contient un nom de paramètre personnalisé et la valeur à utiliser lorsqu’un projet ou un élément est créé à partir du modèle. Un élément `CustomParameter` peut ne contenir aucun élément `CustomParameters` ou en contenir plusieurs.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Spécifie le contenu du modèle.|

## <a name="remarks"></a>Notes

## <a name="example"></a>Exemple
 L’exemple suivant montre comment utiliser plusieurs paramètres personnalisés dans un modèle. Lorsqu’un projet ou un élément est créé à partir `$color1$` d’un modèle avec les paramètres personnalisés suivants, tous les cas et `$color2$` dans les fichiers de modèle seront remplacés par `Red` et, `Blue`respectivement.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Voir aussi
- [Élément CustomParameter (modèles Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Paramètres de modèle](../ide/template-parameters.md)
- [Référence de schéma de modèle de studio visuel](../extensibility/visual-studio-template-schema-reference.md)
