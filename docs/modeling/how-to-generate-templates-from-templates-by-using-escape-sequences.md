---
title: "Comment : générer des modèles à partir de modèles à l’aide de séquences d’échappement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: "35"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 634d5617d1f42891953f8f1a73bcc5d09a8ffa9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Comment : générer des modèles à partir de modèles à l'aide de séquences d'échappement
Vous pouvez créer un modèle de texte qui crée un autre modèle de texte comme sortie texte généré. Pour ce faire, vous devez utiliser des séquences d’échappement pour délimiter les balises de modèle de texte. Si vous n’utilisez pas de séquences d’échappement, votre modèle de texte généré aura une signification prédéfinie. Pour plus d’informations sur l’utilisation de séquences d’échappement dans les modèles de texte, consultez [à l’aide de séquences d’échappement dans les modèles de texte](../modeling/using-escape-sequences-in-text-templates.md).  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Pour générer un modèle de texte à partir d’un modèle de texte  
  
-   Utilisez la barre oblique inverse (\\) comme caractère d’échappement pour produire les balises nécessaires dans le modèle de texte pour les directives, des instructions, des expressions et la classe de fonctionnalités dans un fichier de modèle de texte séparé.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise des caractères d’échappement pour produire un modèle de texte à partir d’un modèle de texte. Le `output` directive définit le type de fichier de destination pour le type de fichier de modèle de texte (.tt).  
  
```csharp  
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