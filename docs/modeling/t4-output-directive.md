---
title: "T4 Output Directive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 4
---
# T4 Output Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans les modèles de texte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la directive `output` sert à définir l'extension du nom de fichier et l'encodage du fichier transformé.  
  
 Par exemple, si votre projet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comprend un fichier de modèle nommé **MyTemplate.tt** qui contient la directive suivante :  
  
 `<#@output extension=".cs"#>`  
  
 alors [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génèrera un fichier nommé **MyTemplate.cs**  
  
 La directive `output` n'est pas obligatoire dans un modèle de texte au moment de l'exécution \(prétraité\).  Au lieu de cela, votre application obtient la chaîne générée en appelant `TextTransform()`.  Pour plus d'informations, consultez [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Utilisation de la directive Output  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 Il ne doit pas y avoir plus d'une directive `output` dans chaque modèle de texte.  
  
## Attribut extension  
 Spécifie l'extension de nom de fichier du fichier de sortie texte généré.  
  
 La valeur par défaut est **.cs**  
  
 Exemples :  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Valeurs acceptables :  
 toute extension de nom de fichier valide.  
  
## Attribut encoding  
 Spécifie l'encodage à utiliser lors de la génération du fichier de sortie.  Par exemple :  
  
 `<#@ output encoding="utf-8"#>`  
  
 La valeur par défaut est l'encodage utilisé par le fichier de modèle de texte.  
  
 Valeurs acceptables :  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` \(valeur système par défaut\)  
  
 En général, vous pouvez utiliser la chaîne WebName ou le nombre CodePage de n'importe lequel des encodages retournés par <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.