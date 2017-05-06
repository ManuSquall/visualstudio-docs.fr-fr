---
title: "&#201;l&#233;ment &lt;formRegions&gt; (d&#233;veloppement Office dans Visual Studio)"
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
  - "formRegions (élément)"
  - "<formRegions> (élément)"
  - "manifestes de l’application (développement Office dans Visual Studio), <formRegions> (élément)"
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &#201;l&#233;ment &lt;formRegions&gt; (d&#233;veloppement Office dans Visual Studio)
  L’élément `formRegions` de l’espace de noms `vstov4`  contient les zones de formulaire Microsoft Office Outlook associées à un complément VSTO.  
  
## Syntaxe  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## Éléments et attributs  
 L’élément `formRegions` de l’espace de noms `vstov4`  contient tous les éléments `formRegion` pour un complément VSTO Outlook. Il est uniquement obligatoire pour les compléments VSTO Outlook qui incluent des zones de formulaire.  
  
 Un seul élément `formRegions` peut être défini dans un manifeste de l’application.  
  
 L’élément `formRegions` ne possède pas d’attributs.  
  
 L’élément `formRegions` possède l’élément suivant.  
  
### formRegion  
 Obligatoire pour les compléments VSTO Outlook qui comprennent des zones de formulaire. L’élément `formRegion` est défini dans [&#60;formRegion&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre un élément `formRegions` dans un manifeste de l’application pour une solution Office au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  