---
title: "&lt;formRegion&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
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
  - "manifestes d’application (développement Office dans Visual Studio), élément <formRegion>"
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt;formRegion&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  L’élément `formRegion` de l’espace de noms `vstov4`  identifie une zone de formulaire Microsoft Office Outlook associée à un complément VSTO.  
  
## Syntaxe  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## Éléments et attributs  
 L’élément `formRegion` de l’espace de noms `vstov4`  identifie une zone de formulaire associée à un complément VSTO Outlook. Il est obligatoire uniquement pour les compléments VSTO Outlook qui incluent des zones de formulaire.  
  
 Plusieurs éléments `formRegion` peuvent être définis à l’intérieur d’un élément `formRegions` pour un même complément VSTO.  
  
 L’élément `formRegion` comporte l’attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Obligatoire. Identifie le nom de la zone de formulaire.|  
  
 L’élément `formRegion` comporte les éléments enfants suivants.  
  
### messageClass  
 L’élément `messageClass`  identifie le formulaire Outlook associé à la zone de formulaire.  
  
 L’élément `messageClass` comporte l’attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`name`|Obligatoire. Identifie le formulaire associé à la zone de formulaire.|  
  
## Exemple  
 L’exemple de code suivant illustre un élément `formRegion` dans le manifeste d’application d’un complément VSTO Outlook déployé à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cette zone de formulaire est associée à trois classes de message. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion>  
```  
  
## Voir aussi  
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  