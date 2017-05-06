---
title: "&#201;l&#233;ment &lt;customization&gt; (D&#233;veloppement Office dans Visual Studio)"
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
  - "manifestes de l’application (développement Office dans Visual Studio), <customization> (élément)"
ms.assetid: a3bf7f35-bd98-4530-9226-46489cd37bb1
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &#201;l&#233;ment &lt;customization&gt; (D&#233;veloppement Office dans Visual Studio)
  L’élément `customization` de l’espace de noms `vstov4` décrit une solution Office spécifique. Les éléments enfants sont différents pour les personnalisations au niveau du document et les compléments VSTO.  
  
## Syntaxe pour les personnalisations au niveau du document  
  
```  
<customization id <document solutionId /> </customization>  
```  
  
## Syntaxe pour les compléments VSTO  
  
```  
<customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization>  
```  
  
## Éléments et attributs  
 L’élément `customization` contient des informations propres à la personnalisation. Cet élément doit être dans l’espace de noms suivant : `vstov4=urn:schemas-microsoft-com:vsto.v4`. Il existe un seul élément `customization` pour chaque solution Office. Par exemple, si vous déployez trois solutions Office dans un déploiement à projets multiples, il existe trois éléments `customization` dans le manifeste de l’application.  
  
 Les éléments enfants de l’assembly doivent également être dans cet espace de noms.  
  
 L’élément `customization` comporte l’attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`id`|Obligatoire pour un déploiement à projets multiples. L’élément `id` identifie de façon unique une solution Office.|  
  
### Personnalisations au niveau du document  
 L’élément `customization` comporte l’élément enfant suivant.  
  
#### document  
 L’élément `document` dans l’espace de noms `vstov4` est défini dans [&#60;document&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).  
  
### Compléments VSTO  
 L’élément `customization` comporte l’élément enfant suivant.  
  
#### appAddin  
 L’élément `appAddin` dans l’espace de noms `vstov4` est défini dans [Élément &#60;appAddin&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).  
  
## Exemple de personnalisation au niveau du document  
  
### Description  
 L’exemple de code suivant illustre l’élément `customization` d’une personnalisation au niveau du document. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization>  
```  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre l’élément `customization` d’un complément VSTO. Il s’agit d’un complément VSTO Outlook qui inclut des zones de formulaire. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  