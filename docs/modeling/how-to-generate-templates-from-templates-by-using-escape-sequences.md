---
title: "How to: Generate Templates from Templates By Using Escape Sequences | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, generating templates from templates"
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 35
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 35
---
# How to: Generate Templates from Templates By Using Escape Sequences
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez définir un modèle de texte qui crée un autre modèle de texte en tant que sortie de texte générée.  Pour ce faire, vous devez utiliser des séquences d'échappement pour délimiter les balises de modèle de texte.  Si vous n'utilisez pas de séquences d'échappement, votre modèle de texte généré aura une signification prédéfinie.  Pour plus d'informations sur l'utilisation des séquences d'échappement dans les modèles de texte, consultez [Using Escape Sequences in Text Templates](../modeling/using-escape-sequences-in-text-templates.md).  
  
### Pour générer un modèle de texte à partir d'un autre modèle de texte  
  
-   Utilisez la barre oblique inverse \(\\\) comme caractère d'échappement pour produire, dans un fichier modèle de texte séparé, les balises nécessaires dans le modèle de texte pour les directives, les instructions, les expressions et les fonctionnalités de classe.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## Exemple  
 L'exemple suivant utilise des caractères d'échappement pour produire un modèle de texte à partir d'un autre modèle de texte.  La directive `output` définit le type de fichier modèle de texte \(.tt\) comme type de fichier de destination.  
  
```c#  
\<#@ output extension=".tt" \#>  
\<#@ assembly name="System.Xml.dll" \#>  
\<#@ import namespace="System.Xml" \#>  
\<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {\#>  
           \<#= attr.Name \#>  
       \<#}  
     }  
\#>  
```  
  
 La sortie de texte générée est un modèle de texte.  
  
```  
<#@ output extension=".tt" #>  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {#>  
           <#= attr.Name #>  
       <#}  
     }  
#>  
```