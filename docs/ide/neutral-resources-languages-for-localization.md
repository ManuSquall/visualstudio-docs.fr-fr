---
title: "Langues des ressources neutres pour la localisation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "culture, rechercher des ressources"
  - "globalisation (Visual Studio), ressources"
  - "localisation (Visual Studio), ressources"
  - "ressources neutres"
  - "NeutralResourcesLanguageAttribute (classe)"
  - "ressources (Visual Studio), système de secours"
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Langues des ressources neutres pour la localisation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La classe <xref:System.Resources.NeutralResourcesLanguageAttribute> spécifie la culture des ressources comprises dans l'assembly principal.  Cet attribut est utilisé pour améliorer les performances en faisant en sorte que l'objet <xref:System.Resources.ResourceManager> ne recherche pas les ressources incluses dans l'assembly principal.  
  
 Le code qui suit indique comment définir la langue des ressources neutres.  Ce code peut être placé soit dans un script de génération, soit dans le fichier AssemblyInfo.vb ou AssemblyInfo.cs.  
  
```vb#  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```c#  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## Voir aussi  
 <xref:System.Resources.ResourceManager>   
 [Introduction aux applications internationales basées sur le .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Organisation hiérarchique des ressources pour la localisation](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Localisation d'applications](../ide/localizing-applications.md)   
 [Globalisation et localisation d'applications](../ide/globalizing-and-localizing-applications.md)