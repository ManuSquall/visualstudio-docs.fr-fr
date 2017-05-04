---
title: "&#201;l&#233;ment &lt;entryPoint&gt; (d&#233;veloppement Office dans Visual Studio) | Microsoft Docs"
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
  - "manifestes de l’application (développement Office dans Visual Studio), <entryPoint> (élément)"
ms.assetid: 991d7cbf-85e5-4307-a470-076b2f74d859
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &#201;l&#233;ment &lt;entryPoint&gt; (d&#233;veloppement Office dans Visual Studio)
  L’élément `entryPoints` de l’espace de noms `vstav3`  contient tous les éléments `entryPoint` associés à une solution Office.  
  
## Syntaxe  
  
```  
<entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
</entryPoints>  
```  
  
## Éléments et attributs  
 L’élément `entryPoints` est obligatoire et se trouve dans l’espace de noms `vstav3` . Il existe un seul élément `entryPoints` défini dans un manifeste de l’application pour chaque solution Office. Par exemple, si vous déployez trois solutions Office dans un déploiement à projets multiples, il existe trois éléments `entryPoints` dans le manifeste de l’application.  
  
 L’élément `entryPoints` comporte l’attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|ID|Obligatoire pour un déploiement à projets multiples. Nom de la solution Office. L’ID ne peut pas contenir le symbole égal \(\=\).|  
  
 `entryPoints` comporte les éléments suivants.  
  
### entryPoint  
 Obligatoire. Le rôle de l’élément `entryPoint` dans l’espace de noms `vstav3`  est défini dans [&#60;entryPoint&#62;, élément &#40;développement Office dans Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md).  
  
## Exemple de personnalisation au niveau du document  
  
### Description  
 L’exemple de code suivant illustre l’élément `entryPoints` d’un manifeste de l’application pour une solution au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints>  
```  
  
## Exemple de complément VSTO  
  
### Description  
 L’exemple de code suivant illustre un élément `entryPoints` d’un manifeste de l’application pour une solution au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints>  
```  
  
## Exemple de déploiement à projets multiples  
  
### Description  
 L’exemple de code suivant illustre l’élément `entryPoints` d’un manifeste de l’application pour un déploiement à projets multiples. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:entryPoints id="ContosoExcel"> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> <vstav3:entryPoints id="ContosoOutlook"> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints>  
```  
  
## Voir aussi  
 [Manifestes d'application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  