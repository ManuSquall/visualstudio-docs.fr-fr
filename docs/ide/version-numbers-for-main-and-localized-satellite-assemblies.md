---
title: "Num&#233;ros de version de l&#39;assembly principal et des assemblys satellites localis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (Visual Studio), numéros de version"
  - "assemblys satellites, numéros de version"
  - "SatelliteContractVersionAttribute"
  - "numéros de version, assemblys"
  - "contrôle de version, assemblys"
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Num&#233;ros de version de l&#39;assembly principal et des assemblys satellites localis&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La classe <xref:System.Resources.SatelliteContractVersionAttribute> fournit la prise en charge du versioning pour un assembly principal qui utilise des ressources localisées par l'intermédiaire du gestionnaire des ressources.  L'application de <xref:System.Resources.SatelliteContractVersionAttribute> à l'assembly principal d'une application vous permet de mettre à jour et de redéployer l'assembly sans mettre à jour ses assemblys satellites.  Par exemple, vous pouvez utiliser la classe <xref:System.Resources.SatelliteContractVersionAttribute> avec un Service Pack qui n'introduit pas de nouvelles ressources sans régénérer et redéployer vos assemblys satellites.  Pour que vos ressources localisées soient disponibles, la version de contrat satellite de votre assembly principal doit correspondre à la classe <xref:System.Reflection.AssemblyVersionAttribute> de vos assemblys satellites.  Vous devez spécifier un numéro de version exact dans la classe <xref:System.Resources.SatelliteContractVersionAttribute> \(les caractères génériques, tels que "\*" ne sont pas autorisés\).  Pour plus d'informations, consultez [Récupération de ressources](../Topic/Retrieving%20Resources%20in%20Desktop%20Apps.md).  
  
## Mise à jour d'assemblys  
 La classe <xref:System.Resources.SatelliteContractVersionAttribute> vous permet de mettre à jour un assembly principal sans avoir à mettre à jour votre assembly satellite ou vice\-versa.  Lorsque l'assembly principal est mis à jour, son numéro de version est modifié.  Si vous souhaitez continuer à utiliser les assemblys satellites existants, vous devez changer le numéro de version de l'assembly principal, mais conserver le même numéro de version de contrat satellite.  Par exemple, dans votre première version d'une application, le numéro de version de l'assembly principal est 1.0.0.0.  Le numéro de version de contrat satellite et le numéro de version de l'assembly satellite sont également 1.0.0.0.  Si vous avez besoin de mettre à jour votre assembly principal pour un Service Pack, vous pouvez modifier la version de l'assembly et utiliser le numéro 1.0.0.1, tout en continuant d'utiliser le numéro 1.0.0.0 comme version de contrat satellite et version de l'assembly satellite.  
  
 Si vous avez besoin de mettre à jour un assembly satellite, sans pour autant mettre à jour votre assembly principal, vous devez modifier le <xref:System.Reflection.AssemblyVersionAttribute> de l'assembly satellite.  Vous devrez joindre à votre assembly satellite un assembly de stratégie qui indique que votre nouvel assembly satellite est compatible avec votre ancien.  Pour plus d'informations sur les stratégies, consultez [Méthode de localisation des assemblys par le runtime](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
 Le code qui suit indique comment définir le numéro de version de contrat satellite.  Ce code peut être placé soit dans un script de génération, soit dans le fichier AssemblyInfo.vb ou AssemblyInfo.cs.  
  
```vb#  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```c#  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## Voir aussi  
 [Méthode de localisation des assemblys par le runtime](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md)   
 [Définition des attributs d'assembly](../Topic/Setting%20Assembly%20Attributes.md)   
 [Sécurité et assemblys satellites localisés](../ide/security-and-localized-satellite-assemblies.md)   
 [Localisation d'applications](../ide/localizing-applications.md)   
 [Globalisation et localisation d'applications](../ide/globalizing-and-localizing-applications.md)