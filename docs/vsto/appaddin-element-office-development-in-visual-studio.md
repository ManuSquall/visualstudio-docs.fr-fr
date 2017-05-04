---
title: "&#201;l&#233;ment &lt;appAddin&gt; (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
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
  - "manifestes de l’application (développement Office dans Visual Studio), <appAddin> (élément)"
ms.assetid: 6152fe5b-6af1-465d-aee7-19e4fd4d04c1
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# &#201;l&#233;ment &lt;appAddin&gt; (d&#233;veloppement Office dans Visual Studio)
  L’élément `appAddin` de l’espace de noms `vstov4`  stocke les informations propres à la personnalisation des compléments VSTO.  
  
## Syntaxe  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## Éléments et attributs  
 L’élément `appAddin` est obligatoire et se trouve dans l’espace de noms `vstov4` . Il existe un seul élément `appAddin` défini dans un manifeste de l’application.  
  
 L’élément `appAddin` a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`application`|Obligatoire. Identifie l’application Microsoft Office. La valeur peut être l’une des suivantes : Excel, InfoPath, Outlook, PowerPoint, Project, Visio ou Word.|  
|`loadBehavior`|Facultatif. Par défaut, `loadBehavior` est activé en définissant cette valeur sur . Pour le débogage, vous pouvez désactiver le complément VSTO en définissant la valeur sur deux. Pour plus d’informations, consultez le tableau intitulé Valeurs LoadBehavior dans [Entrées de Registre pour les compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|`keyName`|Obligatoire. Cette valeur est le nom de la clé de Registre que l’application utilise pour charger le complément VSTO. Pour plus d'informations, consultez [Entrées de Registre pour les compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 L’élément `appAddin` possède les éléments enfants suivants.  
  
### FriendlyName  
 Facultatif. L’élément `friendlyName` est expliqué dans [&#60;friendlyName&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### description  
 Facultatif. L’élément `description` est expliqué dans [&#60;description&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### formRegions  
 Obligatoire uniquement pour les compléments VSTO Outlook qui incluent des zones de formulaire. L’élément `formRegions` est expliqué dans [Élément &#60;formRegions&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre les éléments `appAddin` dans une solution Outlook déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  