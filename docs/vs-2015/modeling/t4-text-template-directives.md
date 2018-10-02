---
title: T4 Directives de modèles de texte | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: douge
ms.openlocfilehash: e079b21c3a85f883351808b8defda6d0d68619f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503376"
---
# <a name="t4-text-template-directives"></a>Directives de modèles de texte T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Directives de modèles de texte T4](https://docs.microsoft.com/visualstudio/modeling/t4-text-template-directives).  
  
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



