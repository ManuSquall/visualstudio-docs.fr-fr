---
title: "&#201;l&#233;ment &lt;application&gt; (D&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
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
helpviewer_keywords: 
  - "manifestes d’application (développement Office dans Visual Studio), <application> (élément)"
ms.assetid: b8d3db7c-9127-4812-b18f-bb17e1f8788f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# &#201;l&#233;ment &lt;application&gt; (D&#233;veloppement Office dans Visual Studio)
  L’élément `application` de l’espace de noms `vstav3` encapsule la description de solutions Office. Les éléments enfants sont différents pour les personnalisations au niveau du document et les compléments VSTO.  
  
## Syntaxe pour les personnalisations au niveau du document  
  
```  
<application> <customization id <document solutionId /> </customization> </application>  
```  
  
## Syntaxe pour les compléments de niveau application  
  
```  
<application> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </application>  
```  
  
## Éléments et attributs  
 L’élément `application` de l’espace de noms `vstav3` est le nœud qui encapsule toutes les informations propres à la personnalisation contenues dans l’espace de noms `vstov4`.  
  
 L’élément `application` ne possède pas d’attributs.  
  
 L’élément `application` possède l’élément suivant.  
  
### personnalisation  
 Le rôle de l’élément `customization` dans l’espace de noms `vstov3` est défini dans [Élément &#60;customization&#62; &#40;Développement Office dans Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## Exemple de personnalisation au niveau du document  
  
### Description  
 L’exemple de code suivant illustre un élément `application` dans une solution Office au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre un élément `application` dans une solution Office de niveau application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  