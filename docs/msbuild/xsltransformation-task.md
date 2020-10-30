---
title: XslTransformation, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche XslTransformation pour transformer une entrée XML à l’aide d’un XSLT et une sortie vers un appareil ou un fichier de sortie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da983f6dc215a5afd651733ecea6b62846ca95cc
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047198"
---
# <a name="xsltransformation-task"></a>XslTransformation (tâche)

Transforme une entrée XML à l’aide d’une transformation XSLT ou XSLT compilée, et génère la sortie dans un fichier ou un périphérique de sortie.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `XslTransformation` .

|Paramètre|Description|
|---------------|-----------------|
|`OutputPaths`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers de sortie de la transformation XML.|
|`Parameters`|Paramètre `String` facultatif.<br /><br /> Spécifie les paramètres pour le document d’entrée XSLT.  Indiquez le code XML brut qui contient chaque paramètre sous la forme `<Parameter Name="" Value="" Namespace="" />` .|
|`XmlContent`|Paramètre `String` facultatif.<br /><br /> Spécifie l’entrée XML sous forme de chaîne.|
|`XmlInputPaths`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les fichiers d’entrée XML.|
|`XslCompiledDllPath`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie la transformation XSLT compilée.|
|`XslContent`|Paramètre `String` facultatif.<br /><br /> Spécifie l’entrée XSLT sous forme de chaîne.|
|`XslInputPath`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le fichier d’entrée XSLT.|

## <a name="remarks"></a>Remarques

 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

Dans l’exemple suivant, un fichier de transformation XSL *Transform. XSLT* est utilisé pour modifier le fichier XML `$(XmlInputFileName)` . Les données XML transformées sont écrites dans `$(IntermediateOutputPath)output.xml` . La transformation XSL prend `$(Parameter1)` comme paramètre d’entrée.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Voir aussi

- [Paramètres XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
