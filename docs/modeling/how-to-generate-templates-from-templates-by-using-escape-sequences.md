---
title: "Comment : générer des modèles à partir de modèles à l’aide de séquences d’échappement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 902cbf66ba0a45f605dc082009cd63cfdf6be1af
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
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