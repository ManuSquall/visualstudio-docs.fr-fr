---
title: "&lt;entryPoint&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)"
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
  - "manifestes d’application (développement Office dans Visual Studio), <entryPoint> (élément)"
  - "<entryPoint> (élément)"
  - "entryPoint (élément)"
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;entryPoint&gt;, &#233;l&#233;ment (d&#233;veloppement Office dans Visual Studio)
  Chaque élément `entryPoint` de l’espace de noms `vstav3`  identifie un assembly de personnalisation qui doit être exécuté lorsque cette application [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] est installée.  
  
## Syntaxe  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## Éléments et attributs  
 L’élément `entryPoint` est obligatoire et se trouve dans l’espace de noms `vstav3` .  
  
 Chaque élément `entryPoint` peut contenir un seul assembly de personnalisation. Plusieurs éléments `entryPoint` peuvent être définis dans un manifeste d’application.  
  
 L’élément `entryPoint` a les attributs suivants :  
  
|Attribut|Description|  
|--------------|-----------------|  
|`class`|Obligatoire. Identifie un assembly de personnalisation à exécuter. La syntaxe de cet attribut est *NomEspaceNoms.NomClasse*.|  
  
 `entryPoint` possède l’élément suivant.  
  
### assemblyIdentity  
 Obligatoire. L’élément `assemblyIdentity` de l’espace de noms `vstav3`  fait référence à un élément `assemblyIdentity` du manifeste d’application [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  
  
 Le rôle de l’élément `assemblyIdentity` et de ses attributs est défini dans [&#60;assemblyIdentity&#62; Element &#40;ClickOnce Application&#41;](~/deployment/assemblyidentity-element-clickonce-application.md).  
  
## Exemple de personnalisation au niveau du document  
  
### Description  
 L’exemple de code suivant illustre les éléments `entryPoint` d’un manifeste d’application pour une solution Office au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre un élément `entryPoint` d’un manifeste d’application pour une solution Office au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  