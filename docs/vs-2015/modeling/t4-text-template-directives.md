---
title: T4 Directives de modèles de texte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 83
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6f5c4c474ad737add8580381e7fda5fb0b0c1afc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044835"
---
# <a name="t4-text-template-directives"></a>Directives de modèles de texte T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les directives fournissent des instructions au moteur de transformation de modèle de texte.  
  
 La syntaxe des directives est la suivante :  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 Toutes les valeurs d'attribut doivent être placées entre guillemets doubles. Si la valeur elle-même contient des guillemets, ils doivent être placés dans une séquence d'échappement au moyen du caractère \.  
  
 En général, les directives sont les premiers éléments d'un fichier modèle ou d'un fichier inclus. Vous ne devez pas les placer à l'intérieur d'un bloc de code `<#...#>` ou après un bloc de fonctionnalité de classe `<#+...#>`.  
  
 [Directive du modèle T4](../modeling/t4-template-directive.md)  

```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [Directive du paramètre T4](../modeling/t4-parameter-directive.md)  

```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [Directive de sortie T4](../modeling/t4-output-directive.md)  

```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [Directive d’assembly T4](../modeling/t4-assembly-directive.md)  

```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [Directive d’importation T4](../modeling/t4-import-directive.md)  

```  
<#@ import namespace="namespace" #>  
```  
  
 [Directive d’inclusion T4](../modeling/t4-include-directive.md)  

```  
<#@ include file="filePath" #>  
```  
  
 [Directive CleanUpBehavior T4](../modeling/t4-cleanupbehavior-directive.md)  

```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 De plus, vous pouvez créer vos propres directives. Pour plus d’informations, consultez [processeurs de Directive modèles de création personnalisé T4 texte](../modeling/creating-custom-t4-text-template-directive-processors.md). Si vous utilisez le Kit de développement logiciel de visualisation et de modélisation pour créer un langage spécifique à un domaine (DSL), un processeur de directive sera généré dans le cadre de votre DSL.
