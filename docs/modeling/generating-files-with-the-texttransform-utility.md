---
title: Génération de fichiers avec l’utilitaire TextTransform dans Visual Studio
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61c71b67c02493ac77a2fd1c21bb47e78122a1d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928657"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Générer des fichiers avec l’utilitaire TextTransform

TextTransform.exe est un outil de ligne de commande que vous pouvez utiliser pour transformer un modèle de texte. Lorsque vous appelez TextTransform.exe, vous spécifiez le nom d’un fichier de modèle de texte en tant qu’argument. TextTransform.exe appelle le moteur de transformation de texte et traite le modèle de texte. TextTransform.exe est généralement appelée à partir de scripts. Toutefois, il n’est pas généralement requis, étant donné que vous pouvez effectuer une transformation de texte dans Visual Studio ou dans le processus de génération.

> [!NOTE]
> Si vous souhaitez effectuer une transformation de texte dans le cadre du processus de génération, envisagez d’utiliser la tâche de transformation de texte de MSBuild. Pour plus d’informations, consultez [génération de Code dans un processus de génération](../modeling/code-generation-in-a-build-process.md). Sur un ordinateur sur lequel Visual Studio est installé, vous pouvez également écrire une application ou une Extension Visual Studio qui peut transformer des modèles de texte. Pour plus d’informations, consultez [de traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe se trouve dans le répertoire suivant :

 **\Program fichiers (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

pour l’édition Professional, ou

 **\Program fichiers (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 pour l’édition Enterprise.

Dans les versions précédentes de Visual Studio, le fichier se trouve dans l’emplacement suivant :

**\Program fichiers (x86) \Common Files\Microsoft Shared\TextTemplating\{version}**

où {version} dépend de la version précédente est installée.

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
|**-out** \<filename >|Le fichier dans lequel la sortie de la transformation est écrite.|
|**-r** \<assembly>|Un assembly utilisé pour la compilation et exécution du modèle de texte.|
|**-u** \<espace de noms >|Un espace de noms qui est utilisé pour la compilation du modèle.|
|**-Je** \<includedirectory >|Un répertoire qui contient les modèles de texte inclus dans le modèle de texte spécifié.|
|**P -** \<referencepath >|Un répertoire pour rechercher les assemblys spécifiés dans le modèle de texte ou pour l’utilisation de la **- r** option.<br /><br /> Par exemple, pour inclure des assemblys utilisés pour l’API Visual Studio, utilisez<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Le nom, nom de type complet et assembly d’un processeur de directive peut être utilisé pour traiter des directives personnalisées dans le modèle de texte.|
|**-un** [processorName] ! [directiveName] ! \<nom_paramètre > ! \<parameterValue >|Spécifiez une valeur de paramètre pour un processeur de directive. Si vous spécifiez simplement le nom du paramètre et la valeur, le paramètre sera disponible pour tous les processeurs de directive. Si vous spécifiez un processeur de directive, le paramètre est disponible uniquement pour le processeur spécifié. Si vous spécifiez un nom de la directive, le paramètre est disponible uniquement lorsque la directive spécifiée est en cours de traitement.<br /><br /> Pour accéder aux valeurs de paramètre à partir d’un processeur de directive ou d’un modèle de texte, utilisez [ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx). Dans un modèle de texte, incluez `hostspecific` dans la directive de modèle et appeler le message sur `this.Host`. Exemple :<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Tapez toujours le ' !' marque, même si vous omettez le processeur et les noms de directive. Exemple :<br /><br /> `-a !!param!value`|
|**-h**|Fournit une aide.|

## <a name="related-topics"></a>Rubriques connexes

|Tâche|Rubrique|
|-|-|
|Générer des fichiers dans une solution Visual Studio.|[Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Écrire des processeurs de directive pour transformer vos propres sources de données.|[Personnalisation d’une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)|
|Écrire un hôte de création de modèles de texte qui vous permet d’appeler des modèles de texte à partir de votre propre application.|[Traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md)|