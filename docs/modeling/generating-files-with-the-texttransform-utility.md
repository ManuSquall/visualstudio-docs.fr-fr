---
title: Génération de fichiers avec l'utilitaire TextTransform
description: Découvrez comment l’utilitaire TextTransform est un outil en ligne de commande que vous pouvez utiliser pour transformer un modèle de texte.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 743b7deb118bb3506773ec1a82d2331633afa7bc
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388826"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Générer des fichiers avec l’utilitaire TextTransform

TextTransform.exe est un outil en ligne de commande que vous pouvez utiliser pour transformer un modèle de texte. Lorsque vous appelez TextTransform.exe, vous spécifiez le nom d’un fichier de modèle de texte comme argument. TextTransform.exe appelle le moteur de transformation de texte et traite le modèle de texte. TextTransform.exe est généralement appelé à partir de scripts. Toutefois, cela n’est généralement pas obligatoire, car vous pouvez effectuer une transformation de texte dans Visual Studio ou dans le processus de génération.

> [!NOTE]
> Si vous souhaitez effectuer la transformation de texte dans le cadre d’un processus de génération, envisagez d’utiliser la tâche de transformation de texte MSBuild. Pour plus d’informations, consultez [génération de code dans un processus de génération](../modeling/code-generation-in-a-build-process.md). Sur un ordinateur sur lequel Visual Studio est installé, vous pouvez également écrire une application ou une extension Visual Studio qui peut transformer des modèles de texte. Pour plus d’informations, consultez [traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform.exe se trouve dans le répertoire suivant :

::: moniker range=">=vs-2019"

**\Program Files (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

pour Professional Edition, ou

**\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

pour Enterprise Edition.

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

pour Professional Edition, ou

**\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

pour Enterprise Edition.

Dans les versions précédentes de Visual Studio, le fichier se trouve à l’emplacement suivant :

**\Program Files (x86) \Common Files\Microsoft Shared\TextTemplating \{ version}**

où {version} dépend de la version précédente installée.

::: moniker-end

## <a name="syntax"></a>Syntaxe

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Paramètres

|**Argument**|**Description**|
|-|-|
|`templateName`|Identifie le nom du fichier de modèle que vous souhaitez transformer.|

|**Option**|**Description**|
|-|-|
|**-out**\<filename>|Fichier dans lequel la sortie de la transformation est écrite.|
|**-r**\<assembly>|Assembly utilisé pour compiler et exécuter le modèle de texte.|
|**-u**\<namespace>|Espace de noms utilisé pour compiler le modèle.|
|**-I**\<includedirectory>|Répertoire qui contient les modèles de texte inclus dans le modèle de texte spécifié.|
|**-P**\<referencepath>|Répertoire dans lequel rechercher les assemblys spécifiés dans le modèle de texte ou pour utiliser l’option **-r** .<br /><br /> Par exemple, pour inclure les assemblys utilisés pour l’API Visual Studio, utilisez<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-DP** \<processorName> ! \<className> !\<assemblyName&#124;codeBase>|Le nom, le nom de type complet et l’assembly d’un processeur de directive qui peuvent être utilisés pour traiter des directives personnalisées dans le modèle de texte.|
|**-a** [processorName] ! [directiveName] ! \<parameterName> !\<parameterValue>|Spécifiez une valeur de paramètre pour un processeur de directive. Si vous spécifiez uniquement le nom et la valeur du paramètre, le paramètre sera disponible pour tous les processeurs de directive. Si vous spécifiez un processeur de directive, le paramètre est uniquement disponible pour le processeur spécifié. Si vous spécifiez un nom de directive, le paramètre n’est disponible que lorsque la directive spécifiée est en cours de traitement.<br /><br /> Pour accéder aux valeurs de paramètre à partir d’un processeur de directive ou d’un modèle de texte, utilisez [ITextTemplatingEngineHost. ResolveParameterValue n'](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). Dans un modèle de texte, incluez `hostspecific` dans la directive de modèle et appelez le message sur `this.Host` . Par exemple :<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Tapez toujours les marques' ! ', même si vous omettez les noms facultatifs de processeur et de directive. Exemple :<br /><br /> `-a !!param!value`|
|**-h**|Fournit de l’aide.|

## <a name="related-topics"></a>Rubriques connexes

|Tâche|Rubrique|
|-|-|
|Générer des fichiers dans une solution Visual Studio.|[Génération de code durant la conception à l'aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Écrire des processeurs de directive pour transformer vos propres sources de données.|[Personnalisation d'une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)|
|Écrivez un hôte de création de modèles de texte qui vous permet d’appeler des modèles de texte à partir de votre propre application.|[Traitement des modèles de texte à l'aide d'un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md)|
