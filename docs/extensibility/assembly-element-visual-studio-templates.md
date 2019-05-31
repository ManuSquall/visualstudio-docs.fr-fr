---
title: Assembly, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13c52b7f913e35ace3e0fd41227e27b6c00e90e2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352194"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly, élément (modèles Visual Studio)
Spécifie les informations relatives à un assembly, le modèle utilise pour ajouter une référence de cet assembly aux projets.

 \<VSTemplate > \<TemplateContent > \<références > \<référence > \<Assembly >

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

 Ce texte spécifie l’assembly à ajouter à un projet lorsque le modèle d’élément est instancié. Ce nom d’assembly doit être spécifié dans une des manières suivantes :

- En tant que nom complet de l’assembly. Exemple :

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- En tant que référence de texte simple. Exemple :

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Notes
 `Assembly` est un élément enfant obligatoire de `Reference`.

 Le `Reference`, `References,` et `Assembly` éléments peuvent uniquement être utilisés dans *.vstemplate* fichiers ayant une `Type` valeur d’attribut `Item`.

## <a name="example"></a>Exemple
 L’exemple suivant illustre la `TemplateContent` élément d’un modèle d’élément. Ce code XML ajoute des références à la *System.dll* et *System.Data.dll* assemblys.

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
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)