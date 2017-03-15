---
title: "D&#233;pannage des exceptions&#160;: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException (exception)"
ms.assetid: d780b8cc-c3f1-45ed-8f8e-3f8728a4b770
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException
Une exception <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> est levée lorsqu'un <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> ne peut pas analyser une ligne dans le format spécifié.  
  
 La propriété `Error Line` de l'objet exception contient le texte de la ligne qui provoque l'erreur.  
  
## Conseils associés  
 **Assurez\-vous que les paramètres TextFieldType et Delimiter sont correctement définis**  
 Le `TextFieldType` \(délimité ou à largeur fixe\) doit correspondre au format du fichier. Si le `TextFieldType` est `FixedWidth`, vérifiez que la propriété `FieldWidths` a été correctement définie. Si le `TextFieldType` est `Delimited`, vérifiez que la propriété `Delimiters` a été correctement définie.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 [Parsing Text Files with the TextFieldParser Object](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [How to: Read From Comma\-Delimited Text Files](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [How to: Read From Fixed\-width Text Files](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)