---
title: "T4 Text Template Directives | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, import directive"
  - "text templates, include directive"
  - "text templates, assembly directive"
  - "text templates, output directive"
  - "text templates, directives"
  - "text templates, template directive"
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 81
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 81
---
# T4 Text Template Directives
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les directives fournissent des instructions au moteur de transformation de modèle de texte.  
  
 La syntaxe des directives est la suivante :  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 Toutes les valeurs d'attribut doivent être placées entre guillemets doubles.  Si la valeur elle\-même contient des guillemets, ils doivent être placés dans une séquence d'échappement au moyen du caractère \\.  
  
 En général, les directives sont les premiers éléments d'un fichier modèle ou d'un fichier inclus.  Vous ne devez pas les placer à l'intérieur d'un bloc de code `<#...#>` ou après un bloc de fonctionnalité de classe `<#+...#>`.  
  
 [T4 Template Directive](../modeling/t4-template-directive.md)  
 ```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [T4 Parameter Directive](../modeling/t4-parameter-directive.md)  
 ```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [T4 Output Directive](../modeling/t4-output-directive.md)  
 ```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [T4 Assembly Directive](../modeling/t4-assembly-directive.md)  
 ```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [T4 Import Directive](../modeling/t4-import-directive.md)  
 ```  
<#@ import namespace="namespace" #>  
```  
  
 [T4 Include Directive](../modeling/t4-include-directive.md)  
 ```  
<#@ include file="filePath" #>  
```  
  
 [Directive CleanUpBehavior T4](../modeling/t4-cleanupbehavior-directive.md)  
 ```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 De plus, vous pouvez créer vos propres directives.  Pour plus d'informations, consultez [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md).  Si vous utilisez le Kit de développement logiciel de visualisation et de modélisation pour créer un langage spécifique à un domaine \(DSL\), un processeur de directive sera généré dans le cadre de votre DSL.