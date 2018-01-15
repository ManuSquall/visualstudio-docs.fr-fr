---
title: "T4 Directives de modèle de texte | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 155477b643224a98194babc8f99c416188d1f867
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="t4-text-template-directives"></a>Directives de modèles de texte T4
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
  
 De plus, vous pouvez créer vos propres directives. Pour plus d’informations, consultez [création de processeurs de Directive de modèle personnalisé T4 texte](../modeling/creating-custom-t4-text-template-directive-processors.md). Si vous utilisez le Kit de développement logiciel de visualisation et de modélisation pour créer un langage spécifique à un domaine (DSL), un processeur de directive sera généré dans le cadre de votre DSL.