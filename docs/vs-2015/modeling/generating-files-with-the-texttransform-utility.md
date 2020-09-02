---
title: Génération de fichiers avec l’utilitaire TextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18776795fdf693c855edd3f629d674089daaaebd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666094"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Génération de fichiers avec l'utilitaire TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe est un outil en ligne de commande que vous pouvez utiliser pour transformer un modèle de texte. Lorsque vous appelez TextTransform.exe, vous spécifiez le nom d’un fichier de modèle de texte comme argument. TextTransform.exe appelle le moteur de transformation de texte et traite le modèle de texte. TextTransform.exe est généralement appelé à partir de scripts. Toutefois, cela n’est généralement pas obligatoire, car vous pouvez effectuer une transformation de texte dans Visual Studio ou dans le processus de génération.

> [!NOTE]
> Si vous souhaitez effectuer la transformation de texte dans le cadre d’un processus de génération, envisagez d’utiliser la tâche de transformation de texte MSBuild. Pour plus d’informations, consultez [génération de code dans un processus de génération](../modeling/code-generation-in-a-build-process.md). Sur un ordinateur sur lequel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est installé, vous pouvez également écrire une application ou une [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extension qui peut transformer des modèles de texte. Pour plus d’informations, consultez [traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe se trouve dans le répertoire suivant :

 **\Program Files\Common Files\Microsoft Shared\TextTemplating\11.0**

## <a name="syntax"></a>Syntaxe

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>Paramètres

|**Argument**|**Description**|
|------------------|---------------------|
|`templateName`|Identifie le nom du fichier de modèle que vous souhaitez transformer.|

|**Option**|**Description**|
|----------------|---------------------|
|**-out** \<filename>|Fichier dans lequel la sortie de la transformation est écrite.|
|**-r**\<assembly>|Assembly utilisé pour compiler et exécuter le modèle de texte.|
|**-u**\<namespace>|Espace de noms utilisé pour compiler le modèle.|
|**-I**\<includedirectory>|Répertoire qui contient les modèles de texte inclus dans le modèle de texte spécifié.|
|**-P**\<referencepath>|Répertoire dans lequel rechercher les assemblys spécifiés dans le modèle de texte ou pour utiliser l’option **-r** .<br /><br /> Par exemple, pour inclure les assemblys utilisés pour l’API Visual Studio, utilisez<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-DP** \<processorName> ! \<className> !\<assemblyName&#124;codeBase>|Le nom, le nom de type complet et l’assembly d’un processeur de directive qui peuvent être utilisés pour traiter des directives personnalisées dans le modèle de texte.|
|**-a** [processorName] ! [directiveName] ! \<parameterName> !\<parameterValue>|Spécifiez une valeur de paramètre pour un processeur de directive. Si vous spécifiez uniquement le nom et la valeur du paramètre, le paramètre sera disponible pour tous les processeurs de directive. Si vous spécifiez un processeur de directive, le paramètre est uniquement disponible pour le processeur spécifié. Si vous spécifiez un nom de directive, le paramètre n’est disponible que lorsque la directive spécifiée est en cours de traitement.<br /><br />  Dans un modèle de texte, incluez `hostspecific` dans la directive de modèle et appelez le message sur `this.Host` . Par exemple :<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Tapez toujours les marques' ! ', même si vous omettez les noms facultatifs de processeur et de directive. Par exemple :<br /><br /> `-a !!param!value`|
|**-h**|Fournit de l’aide.|

## <a name="related-topics"></a>Rubriques connexes

|Tâche|Rubrique|
|----------|-----------|
|Générer des fichiers dans une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Génération de code durant la conception à l'aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Écrire des processeurs de directive pour transformer vos propres sources de données.|[Personnalisation d'une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)|
|Écrivez un hôte de création de modèles de texte qui vous permet d’appeler des modèles de texte à partir de votre propre application.|[Traitement des modèles de texte à l'aide d'un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md)|
