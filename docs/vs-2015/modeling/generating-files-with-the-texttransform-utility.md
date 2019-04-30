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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 607eda7550819e4150f026a0671ed744ba9c10a7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427044"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Génération de fichiers avec l'utilitaire TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe est un outil de ligne de commande que vous pouvez utiliser pour transformer un modèle de texte. Lorsque vous appelez TextTransform.exe, vous spécifiez le nom d’un fichier de modèle de texte en tant qu’argument. TextTransform.exe appelle le moteur de transformation de texte et traite le modèle de texte. TextTransform.exe est généralement appelée à partir de scripts. Toutefois, il n’est pas généralement requis, étant donné que vous pouvez effectuer une transformation de texte dans Visual Studio ou dans le processus de génération.  
  
> [!NOTE]
> Si vous souhaitez effectuer une transformation de texte dans le cadre du processus de génération, envisagez d’utiliser la tâche de transformation de texte de MSBuild. Pour plus d’informations, consultez [génération de Code dans un processus de génération](../modeling/code-generation-in-a-build-process.md). Dans un ordinateur sur lequel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est installé, vous pouvez également écrire une application ou [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension qui peut transformer les modèles de texte. Pour plus d’informations, consultez [de traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
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
|**-out** \<filename >|Le fichier dans lequel la sortie de la transformation est écrite.|  
|**-r** \<assembly>|Un assembly utilisé pour la compilation et exécution du modèle de texte.|  
|**-u** \<espace de noms >|Un espace de noms qui est utilisé pour la compilation du modèle.|  
|**-Je** \<includedirectory >|Un répertoire qui contient les modèles de texte inclus dans le modèle de texte spécifié.|  
|**P -** \<referencepath >|Un répertoire pour rechercher les assemblys spécifiés dans le modèle de texte ou pour l’utilisation de la **- r** option.<br /><br /> Par exemple, pour inclure des assemblys utilisés pour l’API Visual Studio, utilisez<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Le nom, nom de type complet et assembly d’un processeur de directive peut être utilisé pour traiter des directives personnalisées dans le modèle de texte.|  
|**-un** [processorName] ! [directiveName] ! \<nom_paramètre > ! \<parameterValue >|Spécifiez une valeur de paramètre pour un processeur de directive. Si vous spécifiez simplement le nom du paramètre et la valeur, le paramètre sera disponible pour tous les processeurs de directive. Si vous spécifiez un processeur de directive, le paramètre est disponible uniquement pour le processeur spécifié. Si vous spécifiez un nom de la directive, le paramètre est disponible uniquement lorsque la directive spécifiée est en cours de traitement.<br /><br />  Dans un modèle de texte, incluez `hostspecific` dans la directive de modèle et appeler le message sur `this.Host`. Exemple :<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Tapez toujours le ' !' marque, même si vous omettez le processeur et les noms de directive. Exemple :<br /><br /> `-a !!param!value`|  
|**-h**|Fournit une aide.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Générer des fichiers dans une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Écrire des processeurs de directive pour transformer vos propres sources de données.|[Personnalisation d’une transformation de texte T4](../modeling/customizing-t4-text-transformation.md)|  
|Écrire un hôte de création de modèles de texte qui vous permet d’appeler des modèles de texte à partir de votre propre application.|[Traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md)|
