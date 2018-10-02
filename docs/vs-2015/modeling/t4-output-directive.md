---
title: T4 La Directive de sortie | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e0eaa2d8e3fc257e14e04bad3cac706b8a3bc92a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503019"
---
# <a name="t4-output-directive"></a>Directive de sortie T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Directive de sortie T4](https://docs.microsoft.com/visualstudio/modeling/t4-output-directive).  
  
Dans les modèles de texte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la directive `output` sert à définir l'extension du nom de fichier et l'encodage du fichier transformé.  
  
 Par exemple, si votre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projet inclut un fichier de modèle nommé **MyTemplate.tt** qui contient la directive suivante :  
  
 `<#@output extension=".cs"#>`  
  
 puis [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] génère un fichier nommé **MyTemplate.cs**  
  
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



