---
title: T4 La Directive de sortie | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: dc226af7afb14d180dfdc823e293365df2a7a9ca
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="t4-output-directive"></a>Directive de sortie T4
Dans les modèles de texte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la directive `output` sert à définir l'extension du nom de fichier et l'encodage du fichier transformé.  
  
 Par exemple, si votre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet inclut un fichier modèle nommé **MyTemplate.tt** qui contient la directive suivante :  
  
 `<#@output extension=".cs"#>`  
  
 puis [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère un fichier nommé **MyTemplate.cs**  
  
 La directive `output` n'est pas obligatoire dans un modèle de texte au moment de l'exécution (prétraité). Au lieu de cela, votre application obtient la chaîne générée en appelant `TextTransform()`. Pour plus d’informations, consultez [génération de texte d’exécution avec les modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Utilisation de la directive Output  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 Il ne doit pas y avoir plus d'une directive `output` dans chaque modèle de texte.  
  
## <a name="extension-attribute"></a>attribut d’extension  
 Spécifie l’extension de nom de fichier du fichier de sortie texte généré.  
  
 La valeur par défaut est **.cs**  
  
 Exemples :  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Valeurs acceptables :  
 toute extension de nom de fichier valide.  
  
## <a name="encoding-attribute"></a>attribut d’encodage  
 Spécifie l'encodage à utiliser lors de la génération du fichier de sortie. Par exemple :  
  
 `<#@ output encoding="utf-8"#>`  
  
 La valeur par défaut est l'encodage utilisé par le fichier de modèle de texte.  
  
 Valeurs acceptables :  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (valeur système par défaut)  
  
 En général, vous pouvez utiliser la chaîne WebName ou le nombre CodePage de n'importe lequel des encodages retournés par <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.