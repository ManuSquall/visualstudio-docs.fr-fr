---
title: Assembly, élément (modèles Visual Studio) | Microsoft Docs
titleSuffix: ''
description: En savoir plus sur l’élément assembly et sur la manière dont il spécifie les informations relatives à un assembly, que le modèle utilise pour ajouter une référence de cet assembly aux projets.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 54fc5cfccde99776136f0cb904d02bf6a4971045
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097316"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly, élément (modèles Visual Studio)
Spécifie des informations sur un assembly, que le modèle utilise pour ajouter une référence de cet assembly aux projets.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>
 \<Assembly>

## <a name="syntax"></a>Syntaxe

```
<Assembly> AssemblyName </Assembly>
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
|[Référence](../extensibility/reference-element-visual-studio-templates.md)|Spécifie la référence d’assembly à ajouter quand l’élément est ajouté à un projet.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Ce texte spécifie l’assembly à ajouter à un projet lorsque le modèle d’élément est instancié. Ce nom d’assembly doit être spécifié de l’une des manières suivantes :

- En tant que nom complet de l’assembly. Par exemple :

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- En tant que référence de texte simple. Par exemple :

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Notes
 `Assembly` est un élément enfant obligatoire de `Reference`.

 Les `Reference` `References,` éléments, et `Assembly` ne peuvent être utilisés que dans les fichiers *. vstemplate* qui ont une `Type` valeur d’attribut de `Item` .

## <a name="example"></a>Exemple
 L’exemple suivant illustre l' `TemplateContent` élément d’un modèle d’élément. Ce code XML ajoute des références aux assemblys *System.dll* et *System.Data.dll* .

```
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
