---
title: Langues des ressources neutres pour la localisation | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 45fadacc75b2772ba32d7cb0d796c972076b81ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256689"
---
# <a name="neutral-resources-languages-for-localization"></a>Langues des ressources neutres pour la localisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La classe <xref:System.Resources.NeutralResourcesLanguageAttribute> spécifie la culture des ressources incluses dans l’assembly principal. Cet attribut est utilisé comme une amélioration des performances, afin que l’objet <xref:System.Resources.ResourceManager> ne recherche pas des ressources qui sont incluses dans l’assembly principal.  
  
 Le code suivant illustre la définition du langage des ressources neutre. Le code peut être placé dans un script de build, ou dans le fichier AssemblyInfo.vb ou AssemblyInfo.cs.  
  
```vb  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```csharp  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Resources.ResourceManager>   
 [Introduction aux applications internationales basées sur le .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Organisation hiérarchique des ressources pour la localisation](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Localisation d’applications](../ide/localizing-applications.md)   
 [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)

