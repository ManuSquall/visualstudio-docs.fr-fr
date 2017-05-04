---
title: "Configuration requise pour d&#233;velopper des solutions SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, composants requis"
  - "développement SharePoint dans Visual Studio, spécification"
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Configuration requise pour d&#233;velopper des solutions SharePoint
  Vous devez installer les éléments préalables suivants sur le système pour exploiter les outils de développement de solution SharePoint fournis dans Visual Studio:  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] ou une édition de Visual Studio Application Lifecycle Management \(ALM\).  
  
    -   Fonctionnalité [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ou [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], ou les deux, lors de l'installation de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installé sur [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] 64 bits ou [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 64 bits.  
  
     ou  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] installé sur [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] 64 bits ou [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 64 bits.  
  
> [!NOTE]  
>  Alors que seuls les systèmes d'exploitation serveur sont officiellement pris en charge par SharePoint, deux systèmes d'exploitation client sont autorisés : [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] et [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1.  Pour plus d'informations, consultez [Guide d'installation de station de travail de développement SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkID=164557).  
  
 Les types de projet du modèle BDC \(Business Data Connectivity\) nécessitent l'installation de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] sur le système.  
  
 Pour développer des solutions SharePoint dans Visual Studio, vous devez installer SharePoint sur le même ordinateur que Visual Studio.  En outre, les outils de développement SharePoint prennent en charge uniquement une configuration autonome de SharePoint ; ils ne prennent pas en charge de configuration de batterie \(à distance\).  
  
> [!NOTE]  
>  Les projets SharePoint dans Visual Studio prennent en charge uniquement [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  Si vous sélectionnez [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] pour un nouveau projet SharePoint, il continuera de cibler [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  
  
 Pour plus d'informations sur l'installation de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consultez [Installation de Visual Studio](../Topic/Installing%20Visual%20Studio.md).  
  
## Contrôle de compte d'utilisateur Vista et Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] et [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] intègrent une fonction de sécurité appelée Contrôle de compte d'utilisateur \(ou UAC, User Account Control\).  Pour développer des solutions SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sur les systèmes [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] et [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], le contrôle de compte d'utilisateur exige que vous exécutiez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en tant qu'administrateur système.  Sur le bureau, ouvrez le menu contextuel de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], puis sélectionnez **Exécuter en tant qu’administrateur**.  
  
 Pour que le raccourci sur le bureau permette d'exécuter systématiquement le programme en tant qu'administrateur, cliquez dessus avec le bouton droit, choisissez **Propriétés**, cliquez sur le bouton **Avancé**, puis sélectionnez **Exécuter en tant qu'administrateur**.  
  
 Pour plus d'informations, consultez [Présentation et configuration du contrôle de compte d'utilisateur dans Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476) et [Windows 7 User Account Control](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Considérations au sujet des autorisations SharePoint  
 Pour développer des solutions SharePoint, il est indispensable de posséder les autorisations nécessaires à leur exécution et à leur débogage.  Avant d'entreprendre le test d'une solution SharePoint, procédez comme suit pour vérifier si vous disposez des autorisations suffisantes :  
  
1.  Ajoutez votre compte d'utilisateur en tant qu'Administrateur sur le système.  
  
2.  Ajoutez votre compte d'utilisateur en tant qu'administrateur de batterie pour le serveur SharePoint.  
  
    1.  Dans l'Administration centrale de SharePoint, cliquez sur le lien **Gérer le groupe Administrateurs de la batterie**.  
  
    2.  Sur la page **Administrateurs de batterie**, choisissez le bouton **Nouveau**.  
  
3.  Ajoutez votre compte d'utilisateur au groupe WSS\_ADMIN\_WPG.  
  
## Voir aussi  
 [Getting Started &#40;SharePoint Development in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  