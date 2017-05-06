---
title: "&lt;customizations&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)"
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
  - "<customizations>, élément"
  - "customizations, élément"
  - "manifestes de l’application (développement Office dans Visual Studio), élément <customization>"
ms.assetid: fe1133ef-5fdf-4945-a67b-55a66a4e2109
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;customizations&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L’élément `customizations` de l’espace de noms `vstov4` contient toutes les informations sur l’installation et le chargement de chaque solution Office.  
  
## Syntaxe pour les personnalisations au niveau du document  
  
```  
<customizations> <customization id <document solutionId /> </customization> </customizations>  
```  
  
## Syntaxe pour les compléments VSTO  
  
```  
<customizations> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </customizations>  
```  
  
## Éléments et attributs  
 L’élément `customizations` contient des informations spécifiques sur chaque solution Office. Cet élément doit figurer dans l’espace de noms suivant : `vstov4=urn:schemas-microsoft-com:vsto.v4`. Les éléments enfants de l’assembly doivent également figurer dans cet espace de noms.  
  
 L’élément `customizations` ne possède pas d’attributs.  
  
 L’élément `customizations` possède l’élément enfant suivant.  
  
### personnalisation  
 Obligatoire. L’élément `customization` dans l’espace de noms `vstov4` est défini dans [Élément &#60;customization&#62; &#40;Développement Office dans Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## Exemple de personnalisation au niveau du document  
  
### Description  
 L’exemple de code suivant illustre l’élément `customizations` d’une personnalisation au niveau du document.  
  
> [!NOTE]  
>  Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations>  
```  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre l’élément `customizations` d’un complément VSTO. Il s’agit d’un complément VSTO Outlook qui inclut des zones de formulaire. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  